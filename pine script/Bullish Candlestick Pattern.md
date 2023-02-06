# Bullish Candlestick Pattern

In this script, the isBullishCandlestick function checks if the current bar is a bullish candlestick pattern, which is characterized by a close price that is higher than the open price, and a high price that is also higher than the close price, while the low price is lower than the open price.

The plot function then plots the result of the pattern on the chart, with green circles for bullish patterns and red circles for non-bullish patterns.

```
study("Bullish Candlestick Pattern")

// Define the bullish candlestick pattern
isBullishCandlestick(open, close, high, low) =>
    close > open and high > close and low < open

// Apply the pattern to the current bar
bullishPattern = isBullishCandlestick(open, close, high, low)

// Plot the pattern
plot(bullishPattern ? 1 : 0, style = plot.style_circles, color = bullishPattern ? green : red, linewidth = 5)

```
