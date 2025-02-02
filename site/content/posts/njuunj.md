---
title: "Fourier Analysis: Power Spectral Density of GME price cycles "
author: "positive_root"
date: "2021-05-24 10:33:26"
archived: "2021-06-08 09:58:13"
permalink: "http://reddit.com/r/Superstonk/comments/njuunj/fourier_analysis_power_spectral_density_of_gme/"
waybackpermalink: "https://web.archive.org/web/20210524124251/https://www.reddit.com/r/Superstonk/comments/njuunj/fourier_analysis_power_spectral_density_of_gme/"
weight: 242
---I'm trying a cross-post here, hope I'm doing this right, I made some slight improvements after some review on the DD sub.


So hi everybody, I've been lurking for a while, thought I might have something to contribute to the hive-mind. I'm submitting this late at night California time cause it took me a while, it turned out to be very long. Anyway, good morning Euro friends! Can't wait to visit you all again someday!


So I've seen a lot of speculation on FTD cycles of 20-something days, 30-something days, etc, plenty of people wonder if there's really something wonky with GME's price, it sure looks like there are some cycles there, but is there anyway to measure that in a quantitative way? Yes, it's called [Fourier Analysis](https://en.wikipedia.org/wiki/Fourier_analysis) [(wb)](https://web.archive.org/web/20210506225220/http://en.wikipedia.org/wiki/Fourier_Analysis), also known as looking at a plot of power [spectral density](https://en.wikipedia.org/wiki/Spectral_density) [(wb)](https://web.archive.org/web/20210306211113/https://en.wikipedia.org/wiki/Spectral_density).


I've heard some people use this phrase "technical analysis" of price movements, which I believe is called that because it is only just technically a form of analysis? Haha, ok but I seriously don't know why they call it that. I know I'm not the only science-type here, I have a background that does not involve finance but does involve using statistics and I will attempt to perform a statistical analysis. There will be some hand-waving by the end, and in that sense, this may remind you of a so-called technical analysis.


Here's a meme to explain some of the deep secrets of statistical analysis:


​


![](/img/kj5wzkrzo1171.jpg)
Ok so the first question here is how to slice and dice our data. A Fourier analysis requires an unbroken series of consecutive samples of the signal for which you wish to know the power associated with any variable cycles in that signal. That is, if you want to know how much amplitude power is associated with price movements on a 30-day time-scale, you would need an unbroken series of prices many times longer than 30 days. This is because if you only had a random stretch of 60 days, for example, you would only be likely to catch one 30 day-cycle in the middle. If you had data for a consecutive stretch of 120 trading days, you could see 3, maybe 4 cycles with 30-day periods depending on when the cycle starts.


​


So one thing to watch out for is the maximum length of a period under consideration in a Fourier analysis, and only trust power reported for cycles 2 to 4 times shorter than that stretch. So that said, we've got several long time periods of interest to choose from. For this analysis, I choose 3 main periods: The before times of 2016-2019, The Short Period when prices were very low in Q3,Q4 2019 - Q1,Q2 of 2020, and The Ape Days which are obviously the recent times in 2021, but appear to really begin in August 2020, so I will subset Aug - Dec 2020 as The Ape Days of 2020 to see if anything special was going on in the price movements during that time before the coverage became significant:


![](/img/2bgxsrkap1171.jpg)
I have tried slightly changing the boundaries of these time-frames, especially the boundaries around "The Short Period", and it does not have a significant effect on these results. We need to have a signal that is regularly sampled for Fourier Analysis, and I currently only have access to Open and Close price data. To get a uniformly spaced signal, I'm going to pretend the Open price for each trading day occurred at 6am and the Close price occurred at 6 pm, and those are my samples, 2 per day, equally spaced. If anyone has access to long stretches of hourly data they are willing to share, I would perform this analysis on it with interest. I interpolate across weekends to complete long stretches of consecutive calendar days. I am worried about how the interpolation over weekends may affect the conclusions, so I will focus on periods of consecutive trading days, but know that I've considered it. Look how the interpolation is a little wonky over the weekends depending on interpolation choice:


![](/img/d6408q0dp1171.jpg)
Now, a short primer on how to interpret the types of figures I'm about to show you. Prepare yourself, they look messy. They are best to view by kind of blurring your eyes and looking only briefly, you are not supposed to read too much into any of the many peaks, unless they look like a local maximum. We could come up with a series of ad-hoc criteria to determine local maxima and call it objective, but this is somewhat subjective. Here's the first one, no pressure, just get a feel for how it looks:


​


![](/img/mpl2q82gp1171.jpg)
What we see for the Before Times and the Short Period is a "spectrally flat" slope, consistent with statistical noise. There is no particular cycle with a peak that stands above the crowd, if you will. The power spectral densities (PSDs) plotted in blue and green above seem like they have a lot of noise for periods of a few days, and then become big loopy waves out at the long time scales of 100-day periods and beyond. The messiest part is over-sampled, but those long cycles are significant fractions of the total signal length, and power associated with a potential cycle at those long ranges can "alias" themselves out (under-sampled). So don't read too much into the far right side, but do consider the left side and the middle. We discussed this before when thinking about looking for a 30-day pattern with only a 60 day stretch, but here we have 400 and 800 day stretches of days. Note that 10\^0 = 1 day. I note this looks to me like [pink noise](https://en.wikipedia.org/wiki/Pink_noise) [(wb)](https://web.archive.org/web/20210508070315/https://en.wikipedia.org/wiki/Pink_noise), I have no idea what to make of that but I find it very interesting.


The y-axis shows the power per cycle associated with any cycle, and the x-axis shows the period of that cycle. The fact that the units on the y-axis are decibels per cycle per day is supposed to clue you in that dB is a type of log-scale. The x-axis is log scale too. What we see for both the Before Times and the Short Period is a generally constant slope of higher power at longer and longer timescales. Note that this doesn't tell us anything about the trend of price, whether generally up or down, Fourier analysis does not care about that. It only tells us the power associated with cycles of variable periods unrelated to background rising or falling trends. Before August 2020 there were no predictable cycles.


Now, the result you've been waiting for, here are the PSDs for the Ape Days, and the 2020 only subset, and a normal 200-day period, without annotations:


​


![](/img/ik7f3h8pp1171.jpg)
Here are some annotations to guide your eye and go with the following discussion:


![](/img/5qbabk5qp1171.jpg)
In the above figure, I color as orange the PSD of price movements during the most recent 200 trading days (Ape Days). In blue, I plot the PSD associated with 200 trading days during the Before Times, as a comparison to show what a normal 200-day period would look like. This helps us be sure that the Ape Days are indeed unusual. In black, I plot a shorter period of the 115 Ape Days of 2020 only.


While there are particular peaks at 24 trading days, and 35 trading days, it is difficult to be sure these peaks are really local maxima. Could be, say, 21 and 33, I mean, but not 20 and 40. In the shorter Ape Days of 2020 only period, it seems like the 30-day cycle is gone, and the 24 day cycle was longer at 26 days... this may be due to the shorter sampling period of only 115 days.


The peaks at 6, 7, 10, and 15 trading days are only slight local maxima. I imagine some of the power over these time periods is due to options activities, could be people closing out their weeklies or monthlies a various few days or weeks early. The peak around 4.15 days is curiously well resolved, I tried a lot of slicing and dicing and it kept showing up as 4.13, 4.16, but never just 4 days. I note that 4.17 ish days is exactly 100 hours. Could there be some fundamental finance cycle on that time scale... maybe it's algos? I need to find hourly data to have more insight.


But the number one thing I was surprised to see with this analysis is the wonky way the power seems shifted around the 2-day time period. It's almost as if price movements on shorter time-scales have been somehow damped. I only have 2 samples per day, so maybe it is aliasing... but it doesn't show up in any of the Before Times samples.


​


TL;DR: I basically turned GME's price into a sound, and during the before times, it was all [pink noise](https://en.wikipedia.org/wiki/Pink_noise) [(wb)](https://web.archive.org/web/20210508070315/https://en.wikipedia.org/wiki/Pink_noise)... and then sometime around the end of 2020, it starts to beat, at a rate curiously similar to the FTD cycle... power at 2.5 days, 20ish days, 30ish days, the beat is there

