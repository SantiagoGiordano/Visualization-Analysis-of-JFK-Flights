Effects of the Covid-19 Pandemic on Flights from JFK
================
Santiago Giordano
11/24/2021

![](Blogpost-Flights-Topic-github_files/figure-gfm/2) a) ii) Plot
precovid visualization-1.png)<!-- -->

Back in the early months of 2020, when many of us found ourselves in
‘lockdown’ due to the novel coronavirus, the prospect of a pandemic that
would last beyond the summer was a frightening thought. We all hoped it
would subside quickly but this was probably wishful thinking. An
industry that certainly shared our anxieties regarding the effects of
the Covid-19 pandemic was the aviation industry. Facing these lockdowns
all over the globe and myriad travel restrictions, where flights were
still allowed, airlines saw their traffic drop precipitously starting in
March of 2020. In this blogpost I would like to explore some these
consequences, specifically on flights and airport traffic. I will look
at flight data from John F. Kennedy International Airport (JFK) in New
York City. The data was sourced from the `anyflights` package in R,
which itself sources from the Bureau of Transportation Statistics
website, and it includes all domestic departures from JFK during 2019
and 2020.

With an event as consequential as the pandemic, we certainly expect
drastic changes in flight patterns overall. The question, however, is
not whether changes took place but rather what kind. A good starting
point is to graph flight routes throughout the United States both before
the pandemic and after its onset. I decided to define this latter period
as starting on March 13th of 2020 (the date when a national emergency
concerning the outbreak was declared in the US) and it extends up to the
end of 2020. Conversely, the pre-pandemic period is defined as the same
range in months and days but during 2019 (i.e., March thorough
December). With these time periods, we can compare flight patterns in
the midst of the pandemic with an equivalent time period before its
onset. The visualization above represents all flight routes departing
from JFK in the pre-pandemic period, where the thicker lines represent
routes with higher frequencies. And the figure below shows all flights
that departed during the pandemic.

![](Blogpost-Flights-Topic-github_files/figure-gfm/2) b) ii) Plotting
pandemic viz-1.png)<!-- -->

A first impression may be these visualizations look oddly similar.
However, these figures convey two trends. The first is flight routes
remained virtually unchanged - two routes were actually added during the
pandemic. Second, the proportion of flights per route remained
relatively the same during both periods. Since the thickness of the
lines is representative of the frequency of flights within the same
period (i.e., pre-pandemic or during), we can tell which routes had the
highest and lowest frequencies in each period but we cannot tell how
these frequencies changed. For example, we can see that the route to Los
Angeles had a higher frequency than the route to New Orleans, both
before and during the pandemic, but we cannot infer how the number of
flights to each destination changed with the onset of the virus. This
exemplifies one of the main shortfalls of this type of visualization,
which is visually appealing and good for storytelling but is not as well
suited to show precise empirical details about the data.

To visualize the variations in flights we can look instead at the
following line graph, where we compare the number of departures per
month during 2019 and 2020:

![](Blogpost-Flights-Topic-github_files/figure-gfm/3) b) line graph of
flights per month-1.png)<!-- -->

We see that during 2019, the number of flights per month remained
relatively stable, hovering between 9,000 and 10,000 monthly departures.
The first two months of 2020 show a similar trend, with a slight dip in
the number of flights in February due to the end of the holiday season.
Starting in March of 2020, however, we see a stark drop caused by the
pandemic. The monthly departures during the pandemic are reduced to
about one third of the pre-pandemic levels, with April and May showing
the largest decreases. The following bar chart displays the same trend:

![](Blogpost-Flights-Topic-github_files/figure-gfm/4) Bar chart of
flight frequency per month-1.png)<!-- -->

To explore some of the impacts on consumers, we can look at the changes
in departure delays associated with the pandemic. The scatter plot below
graphs the average departure delay in minutes for each month, and we can
compare the averages of 2020 with those of 2019 to measure how delays
fluctuated. Additionally, we can run a regression to get an estimate of
the effect on delays associated with the virus.

![](Blogpost-Flights-Topic-github_files/figure-gfm/5) Jitter for
departure delays per month-1.png)<!-- -->

    ## 
    ## ===========================================================
    ##                                 Departure Delays           
    ## -----------------------------------------------------------
    ## Pandemic Flights                   -11.413***              
    ##                                     (0.212)                
    ##                                                            
    ## Non-Pandemic Flights               11.460***               
    ##                                     (0.141)                
    ##                                                            
    ## N                                   172,422                
    ## R2                                   0.008                 
    ## ===========================================================
    ## Notes:               ***Significant at the 1 percent level.
    ##                       **Significant at the 5 percent level.
    ##                       *Significant at the 10 percent level.

In the scatter plot we see a clear drop in delays during the pandemic,
on average. For the first half of 2019, flights departed JFK with delays
hovering around ten to fifteen minutes, whereas during 2020 the average
delays were close to zero. In fact, after the month of March, the
average delay was negative, meaning the actual departure time was
earlier than the scheduled time. We see this trend persist throughout
most of 2020, with a slight increase in delays during the summer months
and as the winter holiday season approached as well. In 2019, the rise
in delays during summer is significantly sharper, with delay times more
than doubling from May to August. When looking at the regression, we
find its results support this trend. The coefficient for the
non-pandemic flights, 11.5, indicates that flights departing JFK airport
before the pandemic had an average delay of eleven and a half minutes.
Conversely, the regression coefficient for flights departing during the
pandemic indicates they were associated with delays eleven minutes
shorter, on average. In other words, flights departing after March 13th
of 2020 had an average delay of about 0.05 minutes - in essence, there
was no delay. An important caveat are some possible shortfalls of the
regression. The pandemic is not the only factor affecting flight
departure times, but due to limitations in the available data used for
the analysis, I decided to keep the regression simple. Thus, we cannot
use this regression to draw direct causal effects but rather it serves
as part of the evidence supporting the overall trends shown by the data.

One of the aspects aspects of the Covid-19 pandemic that makes it so
unique and unprecedented was its scope - virtually everyone around the
globe felt its effects, and the air travel industry was no exception.
While the initial blow to the industry might have lessened as travel
restrictions were lifted, the effects of the pandemic, both on airlines
and travelers, will resonate for years to come. Our preliminary analysis
of flight data shows travel conditions for consumers saw some type of
improvement through reduced delays. Whether this trend is foreshadowing
changes to come or whether it is purely caused by the reduced air
traffic is to be seen - for now, we can say that it is the time for
delay-averse travelers to enjoy flying.
