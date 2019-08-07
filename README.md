# Auto-Regressive Integrated Moving Average
![](https://github.com/PosamSaiTeja/ARIMA-notes./blob/master/download.png)

##   ARIMA models: 
Auto-Regressive Integrated Moving Averages 
Are an adaptation of discrete-time filtering methods developed in 1930’s-1940’s by electrical engineers (Norbert Wiener et al.) 
Statisticians George Box and Gwilym Jenkins developed systematic methods for applying them to business & economic data in the 1970’s (hence the name “Box-Jenkins models”)
ARIMA -A series which needs to be differenced to be made stationary is an “integrated” (I) series.

 A time series is “stationary” if all of its statistical properties mean,variance,autocorrelations, etc.are constant in time. Thus, it has no trend, no heteroscedasticity, and a constant degree of “wiggliness.”


 ARIMA-Lags of the stationarized series are called “autoregressive” (AR) terms.
ARIMA-Lags of the forecast errors are called “moving average” (MA) terms.

**ARIMA terminology:**
A non-seasonal ARIMA model can be (almost) completely summarized by three numbers:
p = the number of autoregressive terms
d = the number of nonseasonal differences
q = the number of moving-average terms
This is called an “ARIMA(p,d,q)” model
The model may also include a constant term (or not)

**ARIMA forecasting equation**
* Let Y denote the original series
* Let y denote the differenced (stationarized) series
* No difference (d=0): y t = Y t
* First difference (d=1): y t = Y t -Y t-1
* Second difference (d=2):
 y t = (Y t - Y t-1 ) - (Y t-1 - Y t-2 )
     = Y t - 2Y t-1 + Y t-2

Note that the second difference is not just the change relative to two
periods ago, i.e., it is not Y t – Y t-2 . Rather, it is the change-in-the-change,
which is a measure of local “acceleration” rather than trend.


**Do you need both AR and MA terms?**

In general, you don’t: usually it suffices to use only one type or the other.
Some series are better fitted by AR terms, others are better fitted by MA terms (at a given level of differencing).

**Rough rules of thumb:**

If the stationarized series has positive autocorrelation at lag 1,AR terms often work best. If it has negative 
 autocorrelation at lag 1,
 MA terms often work best.
An MA(1) term often works well to fine-tune the effect of anonseasonal difference, while an AR(1) term often 
 works well to compensate for the lack of a nonseasonal difference, so the choice between them may depend on 
 whether a difference has been used.

**Interpretation of AR terms**

A series displays autoregressive (AR) behavior if it apparently feels a “restoring force” that tends to pull it back toward its mean.
* In an AR(1) model, the AR(1) coefficient determines how fast the series tends to return to its mean. If the 
 coefficient is near zero, the series returns to its mean quickly; if the coefficient is near 1, the series 
 returns to its mean slowly.
* In a model with 2 or more AR coefficients, the sum of the coefficients determines the speed of mean reversion, 
 and the series may also show an oscillatory pattern.

**Interpretation of MA terms**

* A series displays moving-average (MA) behavior if it apparently undergoes random “shocks” whose effects are felt in two or more consecutive periods.
* The MA(1) coefficient is (minus) the fraction of last period’s shock that is still felt in the current period.
* The MA(2) coefficient, if any, is (minus) the fraction of the shock two periods ago that is still felt in the current period, and so on.

**AR or MA? It depends!**

* Whether a series displays AR or MA behavior often depends on the extent to which it has been differenced.
* An “underdifferenced” series has an AR signature (positive autocorrelation)
* After one or more orders of differencing, the auto-correlation will become more negative and an MA signature will emerge.
* Don’t go too far: if series already has zero or negative auto-correlation at lag 1, don’t difference again


**Model-fitting steps**

1. Determine the order of differencing
2. Determine the numbers of AR & MA terms
3. Fit the model—check to see if residuals are
“white noise,” highest-order coefficients are
significant (w/ no “unit “roots”), and forecasts
look reasonable. If not, return to step 1 or 2.
In other words, move right or left in the “autocorrelation
spectrum” by appropriate choices of differencing and
AR/MA terms, until you reach the center (white noise).


**Technical issues**

_Backforecasting:_

Estimation algorithm begins by forecasting backward into the past to get start-up values
_Unit roots:_

Look at sum of AR coefficients and sum of MA coefficients—if they are too close to 1 you may want to consider higher or lower of differencing.

_Overdifferencing:_

A series that has been differenced one too many times will show very strong negative auto-correlation and a strong MA signature,probably with a unit root in MA coefficients.


***
