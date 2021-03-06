# Statistics

Navaz Alani
_Spring 2020_

****

## Introduction

The statistcial sciences are concerned with all aspects of _empirical studies_.
An empirical study is one in which one learns by means of observation or
experimentation. At a high level, the process works by first collecting data to
increase the knowledge of the world around us and/or make decisions. Evidently,
this process is an inductive one, working from smaller bits of data collected
empirically to high-level matters/decisions concerning the world.

A key feature of these empirical studies is that they involve __uncertainty__.
That is, if the experiment is repeated, the identical results are not
guaranteed. The main goal is to use the probability models learnt in Stat 231
to try and model this uncertainty.

## Key Definitions

The following definitions are aimed at obtaining a certain level of abstraction
over empirical studies in order to get a handle for working with the general
empirical study.

* __Population__: This is a collection of units. The word "units" is an
  abstraction over the constituents of a population. Examples include
  "Population of all students taking Stat 231 this term". In this population,
  a single unit is a student taking Stat 231 this term. In the "population of
  all people aged 18-25 living in Ontario right now", a single unit is a person
  who, at this point in time, is in the age gap 18-25 and lives in Ontario.

* __Process__: This is a system by which units are produced. An example of such
  a system would be a "car insurance policy". In this abstract system, the units
  generated by this process could be the "claims made by the car insurance policy
  holders". Here is a key distinction between a process and a population.

  1. In a process, units are produced over time
  2. In the case of a population, the definition is made with respect to a
    particular moment in time

* __Variates__: These are characteristics possessed by units in a population.
They are typically represented by letters such as $x,y,z$. There are different
types of variates:

  1. _Continuous_ variates: examples include height, weight, lifetime of an
    electrical component, time until the reoccurrence of a disease after medical
    treatment. These are all real numbers.
  2. _Discrete_ variates: examples include the number of defective smart phones
    produced by a phone manufacturer, the number of deaths per year on a dangerous
    highway/bridge. These are integers, usually non negative.
  3. _Categorical_ variates: examples include university, hair colour, marital
    status, citizenship, etc. These are used when the units can be grouped based
    on the variate.
  4. _Complex_ variates: examples include images, open ended responses to survey
    questions, etc.

* __Attribute__: of a population/processs is a function of a variate which is
  defined for all of the units in a population. Examples include:

  * The mean, mode, variance and other statistical measured (to be discussed)
    later are examples of attributes
  * In the population of persons aged 18-25 living in Ontario, a possible
    attribute of interest is the proportion of people who own a smart phone.
    Another one is the mean annual income for the population
  * In the process by which claims are made by car insurance policy holders,
    an attribute of interest is the proportion of claims exceeding $1 Million.
    Another one is the average claim value.

## Approaches to Data Collection

1. __Sample surveys__: This is when information about a finite population is
  obtained by selecting a "representative" sample of units from the population
  and determining variates of interest for each unit in the sample.
2. __Observational studies__: Information about a population or process is
  collected without any attempt to change one or more of the variates for the
  sampled units. These kinds of studies involve some sort of measurement.

   * Example: In a study on the drinking habits of univeristy students, blood
    alcohol levels were measured from blood samples taken from students at the
    beginning of an 8:30 AM Monday lecture.

3. __Experimental studies__: This is when the experimenters intervene and
  change/set the value of the variates for the units in the study.

   * Example: We continue the example from the observational study. Now suppose
    the blood samples are taken similarly from two classes. In one class,
    the experimenters warned/informed the class in advance of the blood samples
    to be taken to measure alcohol levels. This intervention now qualifies this
    empirical study to be an experimental study.

__Notes on these approaches__:

* Sample surveys, observational studies and experimental studies are not
  mutually exclusive.
* __\[Sample survey  VS Observational study\]__
  Sometimes it is unclear whether a study is a sample survey or an
  observational study since for both cases, one determines variate values for
  the sampled units by observation. If variate values are determined,
  specifically by asking questions, then the study would be called a sample
  survey.
* Have a look at this study: "Participant in a health and diet survey fill out
  a questionaire on their eating habits. Suppose also that a blood sample is
  drawn to determine the participant's cholesterol and glocose levels." So far,
  this is an observational study since measurements (glucose and cholesterol
  levels) are taken on the units.

  Now suppose that the paticipants are randomly assigned to either an increased
  fruit and vegetable diet or a vegetarian diet. Their glucose and cholesterol
  levels are then re-measured after 6 months. Now, this is an experimental
  study since the researchers control who is assigned to what diet regimen.

## Summarizing Data

There are two kinds of data summaries: Numerical and Graphical summaries.
We focus on numerical summaries first.

## Numerical Summaries for Univariate Data

There are three types of numerical measures. They all attempt to represent/
capture some aspect of the data.

1. Measures of location (sample mean, sample median, sample mode)
2. Measures of variability & dispersion (sample variance & standard deviation,
range and interquartile range (IQR))
3. Measures of shape (skewness, kurtosis)

### Measures of Location

A formal definition can be made in terms of a data set $\{y_1,\dots, y_n\}$
where $y_i$ is a real number.

* __Sample mean/average__: It is denoted $\bar{y}$ and is defined as
$\bar{y} = \frac{y_1+\dots + y_n}{n}=\frac{1}{n} \sum_{i=0}^n y_i$.
* __Sample median__: In order to define the sample median, one needs to first
  define the __order statistic__ (a.k.a. ordered sample) of a data set. The
  order statistic is denoted $y_{(1)},\dots, y_{(n)}$ where
  $y_{(1)}\leq y_{(2)}\leq\dots\leq y_{(n)}$. As a result, one may see that
  $y_{(1)}=\min(y_1,\dots,y_n)$ and $y_{(n)}=\max(y_1,\dots,y_n)$. Essentially,
  the order statistic is a reordering of the numeric data set to put it into
  monotonically increasing order.

  Now, to define the sample median, there are two cases. First is when the
  data set contains an odd number of observations. In this case, the sample
  mean (denoted $\hat{m}$) is defined $\hat{m} = y_{(\frac{n+1}{2})}$.
  
  In the case of an even number of observations in the data set, the average of
  the two middle observations is taken for convenience (not all statistical
  software do this, but it is the convention in this course):
  $\hat{m} = \frac{1}{2} \left( y_{(\frac{n}{2})} + y_{(\frac{n+1}{2})} \right)$.

  Compared to the sample mean, the sample median is a more "robust" measure of
  location because it is not affected by extreme observations/outliers in the
  dataset.
* __Sample mode__: This is simply the most common value in the dataset. If all
  observations in the data set are unique, the sample mode does not exist.
  The sample mode is most useful for discrete cases or categorized data with a
  relatively small number of possible values.

  For continuous variates, the data can be grouped into classes/intervals and
  the median can be taken with respect to the frequency of the classes. This
  is called the __sample modal class__.

  * It is possible for the mode of a dataset to be non-unique.
  * Modal classes need not be unique either
  * From a frequency table for grouped data, the mean and median are not
    determinable. It may be possible to determine the class/interval in which
    the median lies.

### Measures of Variability / Dispersion

These measures aim at quantifying the variability/spread of the data. If every
observation were the same, then there would be no variability/spread.
Let $\{y_1,\dots, y_n\}$ be a dataset where $y_i$ is a real number.

* __Sample variance & Standard deviation__: The sample variance is denoted
  $s^2$ and is defined as follows:

  $s^2 = \frac{1}{n-1}\sum_{i=1}^n (y_i - \bar{y})^2 = \frac{1}{n-1}\left[
  \sum_{i=1}^n y_i^2 - n(\bar{y})\right]$

  The formula on the far right hand side is more often used for calculation.
  The reason for using $n-1$ will be explained later. Note that since $n$ has
  to be a positive integer, and the variance formula is essentially summing the
  squares of the differences of each observation with the population mean, the
  variance itself has to be positive real number. This allows the following:

  As for the standard deviation, which is denoted $s$ is defined to be the
  square root of the variance, $s^2$.

  > What are the units of variance and standard deviation?

  The sample mean and standard deviation can be used to summarize unimodal and
  roughly symmetrical (about the mean) data (e.g. the normal distribution).
  If the data is unimodal and roughly symmetric, we can say the following:

  * Approx. 68% of the data will lie in interval $(\bar{y}-s,\bar{y}+s)$
  * Approx. 95% of the data will lie in interval $(\bar{y}-2s,\bar{y}+2s)$

  > Why can we say the above? What is known about the normal distribution?

* __Range__: Simply, $\text{range} = \max(y_1,\dots,y_n) - \min(y_1,\dots,y_n)$.
  This is a very crude measure of the spread of the data. Datasets with the
  same minimum and maximum values for observations will have the same range
  but may look completely different with respect to variability.

* __Interquartile Range (IQR)__: In order to define IQR, we need the following:
  
  __Percentiles and Quartiles__

  * The $p^{th}$ percentile of a dataset is the value such that $p\%$ of the
    data fall at or below it.
  * Formally, the $p_{th}$ quantile (a.k.a. $100p^{th}$ percentile) is a
    value, $q(p)$, determined as follows:

    * let $m=(n+1)p$ where $n$ is the sample size
    * If $m\in\{1,2,\dots,n\}$, then take the $m^{th}$ smallest value:
      $q(p) = y_{(m)}$, where $y_{(m)}$ is from the ordered statistic.
    * If $m\notin\{1,2,\dots,n\}$ but $1<m<n$, then determine the closest
      integer $j$ such that $j<m<j+1$ and set
      $q(p)=\frac{1}{2}\left[y_{(j)} + y_{(j+1)}\right]$

  * There are 3 quartiles which are special enough to be given their own
    names:

    * __First/lower quartile__: $q(0.25)$ is the 25th percentile, or the
      median of the observations below the median.
    * __Median__: $q(0.50)$ is the 50th percentile
    * __Third/upper quartile__: $q(0.75)$ is the 75th percentile, or the
      median of the observations above the median.

  * Now, we are ready to define IQR.

  IQR is defined as $\text{IQR} = q(0.75) - q(0.25)$. It is more robust than
  sample variance since unlike range, it is not affected by extreme values or
  outliers in the dataset.

  Together, the minium, lower quartile, median, upper quartile and maximum of
  a data set form the __five number summary__ which can be used to get an idea
  of the distribution of data in the data set.

#### Measures of Shape

* __Sample Skewness__: this is a measure which attempts to quantify the
  asymmetry of the data. It is defined as:

  $\text{Sample skewness} = \frac{\frac{1}{n} \sum_{i=1}^n (y_i-\bar{y})^3}
  {\left[\frac{1}{n} \sum_{i=1}^n (y_i-\bar{y})^2\right]^{\frac{3}{2}}}$

  Note the exponent 3, which means that the value for skewness can be negative.

  Data that looks symmetric (normal/uniform) will have sample skewness close
  to zero. On the other hand, a positive sample skewness value indicates that
  the right tail of the data is longer than the left tail of the data. Finally,
  a negative skewness indicates that the left tail of the data is longer than
  the right tail.

  > What are the units of sample skewness?

* __Sample kurtosis__: is a measure for whether the data is concerntrated in a
  central peak or in the tails. It is defined as:

  $\text{Sample kurtosis} = \frac{\frac{1}{n} \sum_{i=1}^n (y_i-\bar{y})^4}
  {\left[\frac{1}{n} \sum_{i=1}^n (y_i-\bar{y})^2\right]^{2}}$

  The even exponent tells us that the kurtosis will be positive.

  Data that looks bell shaped/normal has sample kurtosis close to 3.
  Data that is very peaked has a sample kurtosis larger than 3. Finally,
  data that looks uniform has a sample kurtosis close to 1.2.

  Note that some statistical software actually subtract 3 from the kurtosis
  since 3 is what is expected for normal data.

## Graphical Summaries for Univariate Data

__Reminders__: When utilizing a graph to present data, one should consider the
following:

* Appropriate sizing for graphs
* Concise self-explanatory titles
* Axes should be labelled and units provided (if applicable)
* Scales of the axes should be reasonable and suited to the data
* Graphical presentations for data may not always be the best solution so
  be sure that the usage is appropriate

__Histograms__:

The gist of histograms is to present data in a way that it can be compared
to a probability density function (PDF -in the continuous case) and probability
function (PF -in the discrete case).
The comparison to a PDF/PF can be useful when determining which distribution
works best for the data being presented.

Suppose $\{y_1,y_2,\dots,y_n\}$ is an observed data set. In order to present
this data using a histogram, it needs to be pre-processed as detailed here:

* Obtain the minimum and maximum observations in the data set, say $m$ and $M$
  respectively. Partition the interval $[m,M]$ into $k$ disjoint intervals
  $I_j = [a_{j-1}, a_j]$ for where $a_j\in [m,M]$ for all $1\leq j\leq k$.
* Let $f_j = |\{y_i | y_i\in I_j\}|$, for all $1\leq j\leq k$. In other words,
  let $f_j$ be the number of observations from the data set that lie in the
  interval $I_j$. These $f_j$ are called the __observed frequencies__.
  Also, the __relative frequency__ of an interval is $f_j/n$.
* Now, above each interval in the partition, draw a rectangle above it whose
  height is proportional to the observed frequency for that interval.
  This can also be done using the relative frequency instead.

In a __standard__ histogram, the intervals are of equal width and the heights
are equal to the observed/relative frequencies. In a __relative frequency__
histogram, the intervals may not be of the same width. In such a histogram,
the height of each rectangle is set to $\frac{f_j/n}{a_j - a_{j-1}}$ so that
the rectangle's area is equal to $\frac{f_j}{n}$. Doing this ensures that the
sum of the areas of all the rectangles is 1. This is important because to
achieve the goal of comparing the presented data to a PDF, the histogram must
be a relative frequency one.

__Empirical Cummulative Distribution Functions (emprical CDF)__:

Similar to a histogram, the gist of an empirical CDF is finding an object which
presents the data, but can also be used for comparison with the CDF of a random
variable, to determine how well it models the observations.

It is a very simple object, really, which is used to answer the question:
"What is the probability, if a random observation was picked from the dataset,
that it would be less than or equal to some $y$"? This is the same question
the CDF of a random variable answers.

In the case of empircal observations, the empirical CDF, denoted $\hat{F}$, is
defined, for all $y\in \mathbb{R}$ as:

$\hat{F}(y) = \frac{|\{ y_i | y_i \leq y \}|}{n}$

In other words, for every real number $y$, the empirical CDF evaluated at that
value, gives the number of observations less than or equal to $y$, divided by
the total number of observations.

When plotted, $\hat{F}$ should look somewhat staircase like.

__Box Plots__:

A box plot is a method of data presentation which brings out the distribution
of the data set. This is done through the use of the five number summary, with
some slight modifications.

* Draw a box where the bottom is against the lower quartile ($q(0.25)$) and
  the top is against the upper quartile $q(0.75)$. One should deduce that the
  height of box therefore is the IQR of the data set (one of the measures of
  the spread of data).
* Draw a horizontal line through the box, across the median.
* From the bottom of the box, draw a line to the value
  $q(0.25) - (1.5\cdot IQR)$.
  From the top of the box, draw a line to the value
  $q(0.75) + (1.5\cdot IQR)$.
  This is done in order to account for outliers in the data set.
* Finally, plot all additional observations beyond the "whiskers" of the plot
  using symbols like '$+$' or '$*$'. These are called the __outliers__.

Because of how they end up looking, box plots are also called _box and whisker_
plot. They are great for comparing two data sets side by side.

Here are some observations:

* If the median line divides the box approximately into two, then the data is
  roughly symmetrical
* If the median line lies more towards the lower quartile, then half of the
  data is contained in the interval from the lower whisker to the median.
  This signifies that the data is positively skewed (with a right tail).
  This can be applied vice versa.

__Run Charts__:

These are particularly useful when plotting a variate measured against time.
It is simply a plot where the time is plotted on the
$x$-axis and the value of the observation of the variate at that time is
plotted on the $y$-axis. It allows one to see how the variate changes through
time, but it does not really summarize the dataset.

__Scatter Plots__:

The data being summarized so far (of the form $\{y_1,\dots,y_n\}$) is what
is called univariate- observations on a single variate of the sample.
What if one measures 2 variates of interest from the sample, like so:
$\{(x_1,y_1), (x_2, y_2), \dots, (x_n, y_n)\}$, where $x_i,y_i$ are real numbes
for all $1\leq i \leq n$. This is called __bivariate data__.
The $x_i$'s can be observations from one variate and the $y_i$'s are
observations of the other variate of interest.

One of the first approaches to presenting this data is through a scatter plot,
which just plots the observations of the first variate against the observations
of the other variate. So the observation $(x_i,y_i)$ is a point on the 2D
Cartesian plane.

From such a plot, one is able to see whether or not there are signs of a
relationship between the two variates of interest. There is actually a
numerical handle on such a relationship: the _sample correlation_.

For bivariate data of the form $\{(x_1,y_1),\dots,(x_n,y_n)\}$, the sample
correlation is defined through the sums of squares:

$S_{xx} = \sum_{i=1}^n (x_i - \bar{x})^2 = \sum_{i=1}^n x_i^2 - n\bar{x}^2$

$S_{xy} = \sum_{i=1}^n (x_i - \bar{x})(y_i -\bar{y}) = \sum_{i=1}^n x_i^2 - n\bar{x}\bar{y}$

$S_{yy} = \sum_{i=1}^n (y_i - \bar{y})^2 = \sum_{i=1}^n y_i^2 - n\bar{y}^2$

Notice that the first and last sums of squares are exactly the variances for
$\{x_1,\dots,x_n\}$ and $\{y_1,\dots,y_n\}$ respectively.
Together, these sums of squares are used to define the sample correlation, $r$

$r = \frac{S_{xy}}{\sqrt{S_{xx}S_{yy}}}$

__About the sample correlation__: It takes values between -1 and 1 and provides
a measure for the linear relationship between the variates. If $r$ is close to
1, the variates are said to have a strong linear relationship. Similarly, a
value close to -1 implies a strong negative relationship between the two
variates. Finally, $r$ close to 0 indicates that the variates have no
relationship.

__Bar Charts, Pie Charts__:

When data needs to be presented categorically, pie and bar charts shine.

A pie chart represents the relative frequency of the observations for a
category using the area of a sector on a circle. Every category will have a
sector in the circle, possibly even with an area of 0.

Bar graphs work similarly to histograms, where the intervals are replaced
with the categories.

## Probability Distributions and Statistical Models

Empirical studies collect data with the aim of gaining more knowledge and
answering questions about the population/process. This is done through the
use of a __statistical model__, which is essentially a mathematical model
that incorporates probabilities. An over-view of the kinds of questions that
statistical models aim to answer:

* Questions that can be formulated in terms of the parameters of the model
* Models work with random variables which provide a handle on the variation
  of variates in a population
* Drawing conclusions from statistical models involves some level of
  uncertainty, which probability helps to quantify/understand.
* Procedures for making decisions based on observed data can often be
  formulated in terms of models
* Models allow simulations of processes to be run by a computer (because it is
  cheaper and less time consuming)

We shall focus on using the numerical and graphical summaries of empirical data
in order to choose a statistical model and work out estimates for any unknown
parameters in the process.
