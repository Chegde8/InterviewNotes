<script type="text/javascript" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

<style>
.mjx-align {
  text-align: left !important;
}
</style>

---
title: Linear Regression
---
# My Notes

Linear regression finds the best line that fits data. This is achieved by minimizing sum of squares (least squares).
First, let us understand how to fit the best line to given data.
## Fitting line to data - Simple linear regression
We want to fit a line to the data as shown in the figure and want to ensure that it is the best fitting line, i.e. the distance from the line and all data points is as minimal as possible.
The equation of a line is \\(y = mx + c\\) where \\(m\\) is the slope of the line and \\(c\\) is the y-intercept.
The distance between the line and a point \\((x_i, y_i)\\) is:

$$ \begin{aligned} |(mx_i + c) - y_i)| \end{aligned}$$

Suppose there are \\(N\\) data points. We want to know the distance between each point and the line so that we can ensure the line fits well by taking into consideration all the data points. For this, we can sum up the distance between each point and line:

$$ \begin{aligned} f(m,c) = \sum_{i=1}^{N} (mx_i + c - y_i)^2 \end{aligned}$$

The distances between the points and the line are called residuals. The above is the **sum of squared residuals**. The sum of squared residuals is a measure of how well a line fits the data. Squaring helps ensure that the direction of difference between the line and points does not affect calculation. It also makes the function easily differentiable.

To find the best values of \\(m\\) and \\(c\\), that is when the sum of squared residuals is least. This method of finding the best values of \\(m\\) and \\(c\\) is called **least squares**. We can achieve this by differentiating the function \\(f\\) with respect to \\(m\\) and \\(c\\) and sent the differentials to 0. We start with the sum of squared residual equations:

$$ \begin{aligned} f(m,c) = \sum_{i=1}^{N} (mx_i + c - y_i)^2 = (mx_1 + c - y_1)^2 + (mx_2 + c - y_2)^2 + ... \end{aligned}$$

Setting derivatives to 0 and solving:

$$  
\begin{align*}
\frac{\partial f}{\partial c} = 2(mx_1 + c - y_1) + 2(mx_2 + c - y_2) + ... \\
= 2\sum_{i=1}^{N}(mx_i + c - y_i) = 0 \\
m\sum_{i=1}^{N}x_i + Nc - \sum_{i=1}^{N}y_i = 0 \\
Nc = \sum_{i=1}^{N}y_i - m\sum_{i=1}^{N}x_i \\
c = \frac{\sum_{i=1}^{N}y_i}{N} - \frac{m\sum_{i=1}^{N}x_i}{N} \\
c = \bar{y} - m\bar{x} 
\end{align*}
$$

Where \\(\bar{y}\\) and \\(\bar{x}\\) are means of \\(y\\) and \\(x\\).

$$
\begin{align*}
\frac{\partial f}{\partial m} = 2(mx_1 + c - y_1)x_1 + 2(mx_2 + c - y_2)x_2 + ... \\
= 2\sum_{i=1}^{N}(mx_i + c - y_i)x_i = 0 \\
m\sum_{i=1}^{N}x_i^2 + c\sum_{i=1}^{N}x_i - \sum_{i=1}^{N}x_iy_i = 0 \\
\end{align*}
$$

Substituting for c,

$$
\begin{align*}
m\sum_{i=1}^{N}x_i^2 + (\bar{y} - m\bar{x})\sum_{i=1}^{N}x_i - \sum_{i=1}^{N}x_iy_i = 0 \\
m\sum_{i=1}^{N}x_i^2 + \bar{y}\sum_{i=1}^{N}x_i - m\bar{x}\sum_{i=1}^{N}x_i - m\sum_{i=1}^{N}x_iy_i = 0 \\
m(\sum_{i=1}^{N}x_i^2 + \bar{x}\sum_{i=1}^{N}x_i) = \sum_{i=1}^{N}x_iy_i - \bar{y}\sum_{i=1}^{N}x_i \\
m = \frac{\sum_{i=1}^{N}x_iy_i - \bar{y}\sum_{i=1}^{N}x_i}{\sum_{i=1}^{N}x_i^2 + \bar{x}\sum_{i=1}^{N}x_i} \\
\end{align*}
$$

More eligantly, 

$$
\begin{align*}
m = \frac{\sum_{i=1}^{N}(x_i - \bar{x})(y_i - \bar{y})}{\sum_{i=1}^{N}(x_i - \bar{x}^2)}
\end{align*}
$$

:)
