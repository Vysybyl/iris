+++
title = 'The normalized log-log plot'
date = 2024-09-15
image = '/iris/images/2024-07-08_bidston_observatory_terrace.jpg'
categories = ['science']
tags = ['data-science', 'maths']
languages = ['en']
draft = true
+++

The normalized log-log plot is a clear, simple yet rich way to descibe 
the allocation of a measurable quantity over a population.  

## Backstory

A couple of years ago, working as a consultant, I was hired by a start-up
to give them an overview of their user base composition and behaviour.

One of the core aspects of their business consisted in engaging the users 
in different **challenges**, lasting from a few weeks to a few months. 
A typical challenge would work like this: at the end of every week, 
specific users' actions were rewarded with points used to compile a
scoreboard, and the top users at the end of the challenge period would receive 
various kinds of prizes.

The start-up needed a quick way to analyze challenges, and in particular:
- **To confirm that the game was still on**, and that users who joined late or were less active
during the initial weeks of the challenge could still win
- **To compare challenges of different size**. Since not all users engaged in every
challenge, they needed analytical tools to be robust with respect to the
number of users, the duration of the challenge or the number of allocated
points.
- **To ensure that the game was fair**, that no one was cheating or exploiting 
loopholes in the game mechanics. 

## The data
I used the scoreboards as input data. Each scoreboard consisted of a list
of user IDs and user scores (that is, users' point counts).

For each completed challenge, I had both the final scoreboard and 
the partial (weekly) ones. I could also easily compute the live 
scoreboard for ongoing challenges. 

## The normalized log-log plot (NLL-plot)
The data representation I was happier with consisted in plotting the normalized point
allocation over the normalized population size on a log-log scale[^1].

> Note: It should probably be called *twice-normalized log-log* plot or 2NLL plot, but let's not 
be too fussy.

[^1]: I could not find any explicit examples of this plot online, but [here](https://johnwickerson.wordpress.com/2016/08/06/ratios-on-logarithmic-scales/) you have some thoughs on log-log plots by John Wickerson.

To obtain it you have to:
- Group together the users with the same score (or within the same score braket)
- Divide each group's individual score by the total allocated points
- Divide each group size by the total number of users
- Finally, plot the result with the score percentage on the *x* axis and 
the user percentage on the *y* axis, using a logarithmic scale on both axes.

I ignored users with zero points.

### Bar plot vs. line plot vs. scatter plot
My first visualization attempt was a histogram (a bar plot), but I soon discarded
it as the bar areas in a log-log scale seemed very misleading. 

The purest way to represent the data is a scatter plot, but that proved 
hard to read, especially if you want to compare different challenges.

I ended up using a scatter plot with an additional line connecting the markers.
If the markers are too close together, it is a good idea to bin the data. 

## Reading NLL plots
These plots only show *ratios*, since all information about the original scales is
lost. Nevertheless, several visual features of these plots are easily interpreted.

### Raising or falling graphs
A raising graph indicates that very few users have collected most of the points,
while a falling graph means that a large amount of users with very few points exist.

> A note on straight lines: one of the most common usages of log-log plots 
is to spot power-law distributions, which in these plots appear as straight lines. 
Due to the normalization this property is lost in NLL-plots.

### The ends: head and tail
The first and last markers are important. The first marker to the left
indicates the percentage of users with the fewest points (typically just one point).
These users are poorly engaged and probably just not active.

![targets](/images/2024-09-17_unengaged_users.png?size=0.1)

On the other end, the last marker to the right indicates the point
percentage of the top user(s). If it is too far to the right, 
you might be looking at a cheat or maybe at an unbalanced game.

If few users at the top of the scoreboard have large amounts of points,
they will appear as a long "right tail". This is a good way to 
identify outsiders (the so-called "whales")

![targets](/images/2024-09-17_whales.png)

### The body
If the markers are concentrated together, that means that most users
have about the same number of points. In my use case, this was a
desirable feature, since it meant that the challenge was still open for 
most of the users.

![targets](/images/2024-09-17_open_challenge.png)

### Floor and quantization
The minimum allowed height of the graph is inversely proportional to
the total number of users. Hence, if the graph minima are far from the
horizontal axis, the number of users is small.

In other words, if the graph seems to "float" or "stand" on a ledge

The number of users has also an effect on all possible y-values of the graph,
not just the floor.

![targets](/images/2024-09-17_high_floor.png)

## Other use cases

Since I first used these plots, I have been curious of their possible
application to other use cases. 

Here are a few suggestions that I would be happy to see implemented:
- Social sciences: for instance to compare wealth distribution among
the populations of different countries.
- Biology: a few plots may track the concentration of a pollutant
within a population over time. The normalization allows us to compare 
populations of different sizes.
- Finance: how spread are the share of different companies among their shareholders?


## Code

Here is the Python code to render an NLL plot.
```python

```