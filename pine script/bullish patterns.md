Pine script to detect bullish patterns
===

Here's an example of Pine script code to detect the following bullish candlestick patterns: Hammer, Inverse Hammer, Bullish Engulfing, Piercing Line, Morning Star, Three White Soldiers, and Doji:

```pine
study("Bullish Candlestick Patterns")

// Define the patterns
isHammer(open, close, high, low) =>
    close > open and high > close and 2 * close > high + low
isInverseHammer(open, close, high, low) =>
    close < open and high > close and 2 * close > high + low
isBullishEngulfing(open, close, priorOpen, priorClose) =>
    close > open and close > priorClose and open < priorOpen
isPiercingLine(open, close, priorOpen, priorClose) =>
    close > priorOpen and close > (2 * open + priorClose) / 3 and open < priorClose / 2
isMorningStar(open1, close1, high1, low1, open2, close2, high2, low2, open3, close3, high3, low3) =>
    close1 < open1 and close2 > open2 and close3 > open3 and
    close2 > close1 and open2 < open1 and close3 > close2 and
    high2 < low1 and close3 > (open2 + close2) / 2
isThreeWhiteSoldiers(open1, close1, high1, low1, open2, close2, high2, low2, open3, close3, high3, low3) =>
    close1 < open1 and close2 > open2 and close3 > open3 and
    close1 < close2 and close2 < close3 and
    open1 < open2 and open2 < open3
isDoji(open, close, high, low) =>
    close >= open and high > close and low < open and high - low <= 2 * (close - open)

// Apply the patterns to the current bar
hammer = isHammer(open, close, high, low)
inverseHammer = isInverseHammer(open, close, high, low)
bullishEngulfing = isBullishEngulfing(open, close, priorOpen, priorClose)
piercingLine = isPiercingLine(open, close, priorOpen, priorClose)
morningStar = isMorningStar(open[2], close[2], high[2], low[2], open[1], close[1], high[1], low[1], open, close, high, low)
threeWhiteSoldiers = isThreeWhiteSoldiers(open[2], close[2], high[2], low[2], open[1], close[1], high[1], low[1], open, close, high, low)
doji = isDoji(open, close, high, low)

// Plot the patterns
plot(hammer or inverseHammer ? 1 : 0, style = plot.style_circles, color = green, linewidth = 5)
plot(bullishEngulfing or piercingLine or morningStar or threeWhiteSoldiers ? 1 : 0, style = plot.style_circles, color = green, linewidth = 5)
plot(doji ? 1 : 0, style = plot.style_circles, color = green, linewidth = 5)

```
