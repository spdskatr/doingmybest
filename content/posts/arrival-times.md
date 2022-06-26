---
title: "How Long Do I Have To Wait Before Everyone Arrives?"
date: 2022-06-25T12:09:57-05:00
description: ""
tags: ["random"]
math: true
---

Let's say you are organising a meeting for you and $N-1$ of your friends ($N$ people in total). You have all agreed on a time $T$ for the meeting, but the meeting can only start until everyone arrives. Obviously, not everyone is going to arrive at the meeting at exactly time $T$, some people will arrive early and others will arrive late. As the meeting organiser, you want to know how much time you will have to wait for everyone to arrive at the meeting.

First, let's make a few assumptions to turn this into a workable mathematical problem.
- Assume that everyone will arrive at the meeting at some point.
- Assume that each person's lateness is an independent and identical normal distribution $X_i$ with mean $0$ and standard deviation $\sigma$. Negative lateness means that the person arrived early.

With this framework, the random variable $Y$ that represents when the meeting actually starts is defined by
$$Y = \max_{1 \le i \le N} X_i.$$

So, what is the mean (or expected value) of $Y$?

# Expected value of $Y$

*WARNING: A lot of unnecessary maths that goes nowhere. You can skip this section if you wish.*

Well, we would probably have to find out the probability density function (PDF) $f_Y(t)$ of $Y$ first. Then, we could calculate the expected value $E[Y]$ as 

$$E[Y] = \int_{-\infty}^{\infty} t \ f_Y(t) \ \mathrm{dt}.$$

The problem is, we don't know the PDF of $Y$. What do we do?

Well, it turns out that we can get the PDF using the cumulative distrubution function (CDF) $P(Y \le t)$, since by definition,

$$f_Y(t) = \mathrm{\frac{d}{dt}} (P(Y \le t))$$

and we *can* calculate $P(Y \le t)$  using some effort.

What's $P(Y \le t)$? Well, that's the probability that everyone will have made it to the meeting $t$ minutes after the official meeting time. If we consider each person individually, we get

$$
\begin{aligned}
P(Y \le t) &= P(X_1 \le t) \ P(X_2 \le t) \ \dots \ P(X_N \le t) \\\\
&= P(X_1 \le t)^N
\end{aligned}$$

The CDF for $X_1$, $P(X_1 \le t)$, is equal to

$$P(X_1 \le t) = \frac{1}{2}\left(1 + \mathrm{erf}\left(\frac{t}{\sigma \sqrt 2}\right)\right)$$

where $\mathrm{erf}$ is the [error function](https://en.wikipedia.org/wiki/Error_function). Plugging this back into our original equation, we have

$$\begin{aligned}
E[Y] &= \int_{-\infty}^{\infty} t \ \mathrm{\frac{d}{dt}} \left(\left(\frac{1}{2}\left(1 + \mathrm{erf}\left(\frac{t}{\sigma \sqrt 2}\right)\right)\right)^N\right) \ \mathrm{dt} \\\\ 
&= \frac{1}{2^N}\int_{-\infty}^{\infty} t \ \mathrm{\frac{d}{dt}} \left(\left(1 + \mathrm{erf}\left(\frac{t}{\sigma \sqrt 2}\right)\right)^N\right) \ \mathrm{dt}\\\\
&= \frac{1}{2^N}\int_{-\infty}^{\infty} t \ \left(\frac{1}{\sigma \sqrt 2}\right)\left(\frac{2}{\sqrt {\pi}} e^{-\frac{t^2}{2\sigma^2}}\right) \left(N \left(1 + \mathrm{erf}\left(\frac{t}{\sigma \sqrt 2}\right)\right)^{N-1}\right) \ \mathrm{dt}\\\\
&= \frac{\sqrt{2} N}{2^N \sigma \sqrt{\pi}} \int_{-\infty}^{\infty} t \ e^{-\frac{t^2}{2\sigma^2}}\left(1 + \mathrm{erf}\left(\frac{t}{\sigma \sqrt 2}\right)\right)^{N-1} \ \mathrm{dt} \\\\
&= \dots \\\\
&= \text{\it (Mathematician left for coffee break)}
\end{aligned}$$

{{< figure src="/posts/arrival-times/opalnope.webp" >}}

# Wait, what are we even doing again?
Hold up, we just dived head-first into a fistful of mathematical calculations without even thinking about how they actually help us solve the problem.

This would be perfectly fine if we just wanted some fun maths problems to work on, but we're trying to solve a *real-world problem* here. Real-world problems are messy.

How much delay should we have to plan ahead for in this scenario? Even given our assumptions, no matter how much we prepare, there will always be a small probability that someone in the group arrives extremely late. It's unclear how the expected value even helps us here. Clearly, if we just use the average, wouldn't it still be quite likely that someone hasn't arrived by then?

Let's do this again, but this time approach it *carefully*.

# Attempt two

Let's say that, for our purposes, we want our wait time to be such that we are at least 95% sure that everyone will have arrived. This way, we can be fairly sure that the meeting will start at or before the scheduled time, and more importantly, *can make up for any error that results from our assumptions not being perfect*.

This is fairly simple to express using our framework from before; we wish to find $t$, such that

$$P(Y \le t) = 0.95.$$

From the equations from before, this is equivalent to

$$P(X_1 \le t)^N = 0.95$$

which, after rearranging, we get

$$P(X_1 \le t) = 0.95^\frac{1}{N}.$$

Recall that $X_1$ is normally distributed. Hence, we can simply plug our value into the inverse of the [standard normal CDF](https://en.wikipedia.org/wiki/Normal_distribution#Cumulative_distribution_functions) (denoted by $\Phi^{-1}$):

$$t = \sigma \ \Phi^{-1}\left(0.95^\frac{1}{N}\right).$$

And there we have it! That's our expression for the waiting time! More importantly, the 0.95 came through that calculation completely intact, which means we can replace it with any probability we want. That's what we'll do!

# Results
Now that we have worked out an expression, we want to present our findings so that other people can make use of our insights. Here's where we need to ask ourselves, which variables do we actually care about?
- The number of people who will turn up to the meeting
- The standard deviation for the distribution of arrival times
- The probability that everyone turns up before that time

Let's write up some Python code to generate a table.
```py
import numpy as np
from scipy.stats import norm

def get_time(N, sigma, p):
    # The inverse of a CDF is known in scipy as the
    # percent-point function, or PPF.
    return sigma * norm.ppf(np.power(p, 1/N))

for name, sigma in [("walking", 3), ("driving", 12)]:
    print(f"**Results for method of transportation: {name} "
          f"(stddev = {sigma})**")
    print()
    N_VALUES = [1, 5, 25, 100]
    print("| Success chance | 1 person | 5 people |"
          " 25 people | 100 people |")
    print("| :-: | :-: | :-: | :-: | :-: |")
    for p in [0.5, 0.8, 0.95, 0.999]:
        # Don't mind my inconsistent use of f-strings
        print("| **{0}** |".format(p) + \
            "".join([
                " {0:.1f} mins |".format(get_time(N, sigma, p)) 
                for N in N_VALUES
            ]))
    print()
```

## Output
**Results for method of transportation: walking (stddev = 3)**

| Success chance | 1 person | 5 people | 25 people | 100 people |
| :-: | :-: | :-: | :-: | :-: |
| **0.5** | 0.0 mins | 3.4 mins | 5.8 mins | 7.4 mins |
| **0.8** | 2.5 mins | 5.1 mins | 7.1 mins | 8.5 mins |
| **0.95** | 4.9 mins | 7.0 mins | 8.6 mins | 9.9 mins |
| **0.999** | 9.3 mins | 10.6 mins | 11.8 mins | 12.8 mins |

**Results for method of transportation: driving (stddev = 12)**

| Success chance | 1 person | 5 people | 25 people | 100 people |
| :-: | :-: | :-: | :-: | :-: |
| **0.5** | 0.0 mins | 13.5 mins | 23.1 mins | 29.5 mins |
| **0.8** | 10.1 mins | 20.5 mins | 28.4 mins | 34.1 mins |
| **0.95** | 19.7 mins | 27.8 mins | 34.4 mins | 39.4 mins |
| **0.999** | 37.1 mins | 42.5 mins | 47.3 mins | 51.2 mins |

## Remarks
You may notice that the model begins to break down when approaching very high probabilities and very large numbers of people. In real life, people sometimes oversleep, get stuck in traffic jams, have emergencies that would result in them not being able to come. Our model does not account for that.

I've also pulled the values for the standard deviation out from thin air. They're probably on the high side, just to be safe. Further research could be done for more convincing values to use for the standard deviation. We could also properly consider what factors lead people have higher variance in arrival times.

# Conclusion
Well, that wasn't so bad now, was it? Next time, when I'm inviting 4 friends over for dinner at a restaurant, i'll be sure to reserve 7 minutes of waiting time.