# Overview
graphics package contains a wide variety of functions for plotting data.
#### charts included in the graphics package include
barplot, dotchart, hist, density, stripchart, qqnorm, xplot, qqplot, etc

## Scatter Plots

- ### plot()
```R
plot(x,y,...)
```
parameters: type (type of plot - p for points), xlim, ylim (limits of the axes), log (which axes should be plotted on a logarithmic scale), main (main title of plot), sub (subtitle of plot), xlab, ylab (labels of axes), etc

#### To identify and/or label plot points
 - **locator()** 
 type locator(1) and click on a point in open graphics window
 
- **identify()**
allows users to interactively identify and label data points or features in a plot
```R
identify(x, y = NULL, labels = NULL, n = Inf, plot = TRUE, ...)
```
parameters: labels (char vector containing labels of data pts), plot (shld plot be displayed before identifying pts), n (no of points to be identified)

- **text()**
allows you to place text at specified coordinates on a graph to provide labels, titles, or any other textual information related to the plot.
```R
text(x, y, labels, pos = NULL, offset = 0.5, adj = NULL, col = NULL, cex = 1, ...)
```
parameters: pos (relative positioning of labels next to points), offset (specifies the distance from the specified coordinates where the text will be placed), col (colour), cex (to specify size of text relative to default size)

- ### matplot()
used when you have more columns of data to plot, or ie *multiple plots in one graph*
```R
matplot(x, y, type, lty, lwd, pch, col, cex, bg, xlab, ylab, xlim, ylim, add, verbose, ...)
```
parameters: lty (vector of line types), lwd (vector of line widths), pch (vector of plotting characters), col (vector of colours), cex (vector of character expansion sizes), bg (vector of background colors), add (whether to add to current plot or generate new plot), verbose (whether to put info on console bout wt matplot did)

- ### smoothScatter()
plots the density of points by shading different regions of the plot different shades, depending on the density of points in each region
```R
smoothScatter(x, y = NULL, nbin , bandwidth, colramp, nrpoints , pch = ".", cex = 1, col = "black", xlab = NULL, ylab = NULL, xlim, ylim, ...)
```
parameters: colramp (color ramp or palette for the plot)
![[Pasted image 20230717213754.png]]



- ### pairs()
grid of scatterplots that displays the relationships between multiple pairs of variables in a data frame
```R
pairs(x, ...)
```
parameters: x (dataframe or matrix)

![[Pasted image 20230717213657.png]]


## Plotting time series

- ### plot()
When you use the "plot" function with a time series object, such as those created using the `ts()` function or other time series classes in R, it automatically recognizes the time dimension and creates a plot that represents the data over time.
```R
#example
# Create a simple time series data
dates <- as.Date(c("2023-07-01", "2023-07-02", "2023-07-03", "2023-07-04", "2023-07-05"))
values <- c(10, 15, 20, 18, 25)
time_series <- ts(values, start = min(dates), frequency = 1)

# Create a time series plot
plot(time_series, main = "Time Series Plot", xlab = "Date", ylab = "Values", type = "o")
```
`type = "o"` argument is used to display both points and lines in the plot.
![[Pasted image 20230717213323.png]]


- ### autocorrelation plot - acf()
*aka correlogram*
the plot shows how correlated points are with each other, by difference in time
```R
acf(turkey.price.ts)
```

![[Pasted image 20230717213543.png]]

## Barcharts

- ### barplot()
used to display the relationship between a numeric and a categorical variable
can’t work with a data frame
```R
barplot(H, xlab, ylab, main, names.arg, col)
```
parameters: names.arg (vector of names appearing under each bar), width (width of bar), space (amt of space between bars), legend.text (logical value (legend is created using row names) or char vector (the character values are used as legend)), beside (if columns should be stacked or drawn beside one another), etc
![[Pasted image 20230717223555.png]]
to add legend, use **legend()**
```R
#example
legend("topleft", regions, cex = 1.3, fill = colors)
```

## Pie Charts

### using pie()
```R
pie(x, labels, radius, main, col, clockwise)
```
parameters: labels (description of the slices), radius (radius of circle of pie), clockwise (if slices are drawn cw or acw)
![[Pasted image 20230717223407.png]]

## Plotting Categorical data

- ### conditional density plot - cdplot()
examine the relationship between a continuous and categorical variable which shows how the conditional distribution of the former changes over different values of the latter.

it also uses the density function to compute kernel density estimates across the range of numeric values and then plots these estimates
```R
cdplot(x, y, plot = TRUE, tol.ylab = 0.05, ylevels = NULL, n = 512, from = NULL, to = NULL, col = NULL, border = 1, main = "", xlab, ylab, xlim, ylim ...)
```
parameters: tol.ylab (tolerance parameter for y axis labels), ylevels (specifies order in which levels should be plotted), from, to (lowest and highest point at which density is estimated), n (no. of points at which density is estimated), plot (if conditional densities shld be plotted or not)

![[Pasted image 20230717222853.png]]

- ### mosaic plot - mosaic()
to plot the proportion of observations for two different categorical variables
it draws a rectangle, and its height represents the proportional value.
it shows a set of boxes corresponding to different factor values.
```R
mosaic(x, shade=NULL, legend=NULL, main=, ....)
```
parameters: shade (if we want a colored plot or not)
![[Pasted image 20230717223333.png]]

- ### spine plot - spineplot()
shows different boxes corresponding to the number of observations associated with two factors
```R
spineplot(formula=, data=)
```
![[Pasted image 20230717223817.png]]

## Three dimensional data

- ### using persp()
```R
persp(x, y, z, xlim, ylim, zlim, theta, phi)
```
parameters: theta (azimuthal direction of viewing angle), phi (colatitude of viewing angle)

![[Pasted image 20230717224410.png]]

- ### using image()
```R
image(x, y, z, zlim, xlim, ylim, col = heat.colors(12), add = FALSE, xaxs = "i", yaxs = "i", xlab, ylab, breaks, oldstyle = FALSE, ...)
```

- ### using heatmap()
it plots a grid, where each box is encoded with a different color depending on the size of the dependent variable
It may also plot a tree structure (called a dendrogram) to the side of each plot showing the hierarchy of values. 
```R
heatmap(x, Rowv=NULL, Colv=if(symm)"Rowv" else NULL, distfun = dist, hclustfun = hclust, symm = FALSEscale=c("row", "column", "none"), ...)
```
parameters: rowv and colv (control the clustering of rows and columns, respectively), scale (how the data will be scaled before plotting), symm (if matrix shld be treated as symmetric), distfun and hclustfun (to specify custom functions for calculating the distance matrix and performing hierarchical clustering)

- ### contour()
```R
contour(x, y, z, nlevels, levels, labcex = 0.6, method = "flattest", frame.plot = axes, col = par("fg"), lty = par("lty"), lwd = par("lwd"), ...)
```
parameters: nlevels (no of contour levels), levels (levels at which to draw lines), labels (labels for the contour lines), method (where to draw contour labels)

![[Pasted image 20230717225839.png]]

## Plotting distributions

- ### histogram - hist()
```R
hist(x, breaks = "Sturges", freq = TRUE, include.lowest = TRUE, ...)
```
![[Pasted image 20230718015135.png]]

- ### density plot
When combined with the `density()` function, `plot()` is commonly used to create density plots or kernel density plots. Density plots visualize the probability density function of a continuous variable, providing insights into its underlying distribution.
```R
plot(density(...), ...)
```
`rug()` can also be added to the density plot
![[Pasted image 20230718015104.png]]

- ### quantile - quantile plot - **qqnorm()**
it compares the distribution of the sample data to the distribution of a theoretical distribution (often a normal distribution).
If the sample data is distributed the same way as the theoretical distribution, all points will be plotted on a 45° line from the lower-left corner to the upperright corner.
```R
qqnorm(data)
```
![[Pasted image 20230718015408.png]]

- ### box plots
box shows IQR, line shows median
```R
boxplot(boxplot(x, data = NULL, formula = NULL, at = NULL, axes = TRUE, outline = TRUE, horizontal = FALSE, ....)
```
parameters: formula (its of the form y ~ group where y is variable to be plotted and grp is variable describing set of diff plotting groups)
many can be plotted together
![[Pasted image 20230718015537.png]]

![[Pasted image 20230718020618.png]]

# Customizing charts

### Common arguments to chart functions

| *argument*   | *description*                                 |
|------------|---------------------------------------------|
| add        | if plot shld be added to existing plots     |
| axes       | will axes be plotted on chart               |
| log        | will points be plotted on logarithmic scale |
| type       | type of graph being plotted                 |
| xlab, ylab | labels                                      |
| main       | title                                       |
| sub        | subtitle                                    |

# Graphical Parameters

*this section describes the graphical parameters available in the graphics package*
**par()** fn can also be used to set parameters for these functions
```R
my_graphics_params <- function () { par(some graphics parameters) }
```
To get a vector showing all graphical parameters, simply call par with no arguments.

- ### Annotations 
**ann**
*titles and labels* are called annotations

- ### Margins
to control the *size of the margin* around a plot.
    - **mai** : to specify margin size in inches
	- **mar** : to specify margin size in lines of text. *mex* can also be used to control text size in margin
	- **mgp** : to control margin around titles and labels

- ### Multiple plots
    - to plot multiple charts within the same chart area
    - **mfcol**
```R
par(mfcol=c(3,2))
```
Each time a new figure is plotted, it will be plotted in a different row or column within the device, starting with the top-left corner. 
Plots are then added one at a time, first filling each column from top to bottom, and moving to the next column to the right when each column is filled.

***extras:***
- To find the size of the current plot area (within the grid), check the parameter *pin*. 
- To get the coordinates of the plot region, check the parameter *plt*. 
- To find the dimensions of the current plot area using normalized device coordinates, use the parameter *fig*.

- ### Text properties
    - #### Text size
        - **ps** - point size of text
        - **cex** - default scaling factor for text
        - use the read-only parameters cin, cra, csi, and cxy to check the size of character

    - #### Typeface
        - **font** 

    - #### Alignment and spacing
        - **adj** - controls how text is aligned
        - **lheight** - control spacing  bw lines of text

    - #### Rotation
        - **crt** - to rotate each character
        - **srt** - to rotate each string

- ### Line properties
    - **lend** - to change line end style
    - **lmiter** - to change line join style
    - **lty** - line type
    - **lwd** - line width
    - **bty** - to change the way boxes are drawn around plots

- ### Colors
    - **bg** - background color
    - **fg** - foreground color
    - **col**
    *colors* function used to get list of valid color names
    *palette* function used to view or change a color palette

- ### Axes
	- **lab** - to control how axes are annotated
	- **las** -  to change axis label style
	- **xaxs and yaxs** - to change the way intervals are calculated
	- **xaxt**="n" or **yaxt**="n" - to remove the axes

- ### Points
**pch** - to change symbol used for points

## Graphical parameters by name

> Important graphical parameters that can be set with `par()` in R:
1. **family**: Font family used for text.
2. **cex**: Size scaling factor for text and symbols.
3. **col**: Default color for plotting symbols, text, and lines.
4. **bg**: Background color used in plotting regions.
5. **lty**: Line type for lines in the plot.
6. **lwd**: Line width.
7. **pch**: Plotting symbol for points.
8. **xlab**, **ylab**: Labels for x-axis and y-axis, respectively.
9. **main**: Title of the plot.
10. **xlim**, **ylim**: Limits of the x-axis and y-axis, respectively.
11. **las**: Orientation of axis labels (0 for parallel to axis, 1 for horizontal).
12. **mar**: Margin sizes (bottom, left, top, right) in lines of text.
13. **oma**: Outer margin sizes (bottom, left, top, right) in lines of text.
14. **mfcol**, **mfrow**: Parameters to arrange multiple plots in a grid layout.

# Basic Graphics functions

It is possible to use these functions to either modify an existing chart or to draw a chart yourself from scratch

- ### Points
    - #### points()
    ```R
    points(x, y = NULL, type = "p", ...)
	```
	very useful for adding an additional set of points to an existing plot (typically a scatter plot), usually with a different color or plot symbol
	other useful arguments: pch, col, cex, lwd
  - #### matpoints()
```R
  matpoints(x, y, type = "p", lty = 1:5, lwd = 1, pch = NULL, col = 1:6, ...)
```
to add points to an existing matrix plot

- ### Lines
	- #### lines()
		```R
		lines(x, y = NULL, type = "l", ...)
		 ```
		used to add to an existing plot.
		other useful arguments: lty, lwd, col, end, 
	- #### matlines()
	```R
	  matlines (x, y, type = "l", lty = 1:5, lwd = 1, pch = NULL, col = 1:6, ..
	```
	to add lines to an existing plot

- ### Curve()
```R
curve(expr, from = NULL, to = NULL, n = 101, add = FALSE, type = "l", ylab = NULL, log = NULL, xlim = NULL, ...)
```
parameters: expr (expression to plot), from and to (lowest and highest point at which expr is calculated), n (no of values at which to evaluate expr between the limits)

- ### Text()
to add text to an existing plot
```R
text (x, y = NULL, labels = seq_along(x), adj = NULL, pos = NULL, offset = 0.5, vfont = NULL, cex = 1, col = NULL, font = NULL, ...)
```

- ### abline()
plot a single line across the plot area
```R
abline(a = NULL, b = NULL, h = NULL, v = NULL, reg = NULL, coef = NULL, untf = FALSE, ...)
```
parameters: a (line intercept), b (line slope), h and v (numeric vector of y/x values for horizontal/vertical lines)

- ### polygon()
```R
polygon(x, y = NULL, density = NULL, angle = 45, border = NULL, col = NA, lty = par("lty"), ..
```
parameters: x and y (specify the vertices of the polygon)
```R
#example - to draw a 2 × 2 square on a graph centered at (3, 3)
polygon(x=c(2, 2, 4, 4), y=c(2, 4, 4, 2))
```
*rect()* is for rectangle

- ### segments()
To draw a set of line segments connecting pairs of points
```R
segments(x0, y0, x1, y1, col = par("fg"), lty = par("lty"), lwd = par("lwd"), ... )
```

- ### legend()
To add legend to chart
```R
legend(x, y = NULL, legend, fill = NULL, col = par("col"), ....)
```
parameters: x and y (coordinates at which legend will be positioned), legend (char vector to appear in legend), fill (color associated with each legend label)

- ### title()
it adds a main title (main), a subtitle (sub), an x-axis label (xlab), and a y-axis label (ylab).
```R
title(main = NULL, sub = NULL, xlab = NULL, ylab = NULL, line = NA, outer = FALSE, ...)
```
parameters: outer (TRUE if ud like to place labels in the outer margin)

- ### axis()
```R
axis(side, at = NULL, labels = TRUE, tick = TRUE, line = NA, pos = NA, outer = FALSE,..)
```
parameters: tick (if tick values and an axis will be drawn)

- ### box()
to draw a box around the current figure region
```R
box(which = "plot", lty = "solid", ...)
```
parameters: which (where to draw the box - plot, figure, inner, or outer)

- ### mtext()
to add text to a margin of a plot
```R
mtext(text, side = 3, line = 0, outer = FALSE, at = NA, adj = NA, padj = NA, cex = NA, col = NA, font = NA, ...)
```
parameters: side (where to plot the text, side = 1 for bottom, side = 2 for left, side = 3 for top, and side = 4 for right), line (where to write the text in terms of margin lines)

- ### trans3d()
To add lines or points to a perspective plot (from persp)
```R
trans3d(x,y,z, pmat)
```
parameters: pmat (perspective matrix that is used for translation)
it takes vectors of points x, y, and z and translates them into the correct screen position





