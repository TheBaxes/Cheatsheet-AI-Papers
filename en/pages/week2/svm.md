# A Training Algorithm for Optimal Margin Classifiers


## Intuiton

Classifiers with a large number of adjustable parameters are likely to overfit with the training data and be hopeless with generalization; Conversely, a classifier with insufficient capacity might not be able to learn the task at all.
The paper describes a training algorithm that automatically tunes the capacity of the classication function by maximizing the margin between training examples and class boundary. This summary joins the paper ideas and the intuiton explained in the classroom.

The following image shows the main idea, lets say we have some examples, in the "right" side of the street we have positive examples and in the left side of the "street" we have negative examples.

We don't know the **W** vector yet, but we know that this vector is perpendicular to the gutters, so, the dot product between **W** and the unknown **U** vector will give us the proyection **P** that lead us to the following conclusion:

<img src="./images/margin_2.jpeg">

Now, we want to insist if the unknown vector is a positive example or a negative example must be as far as possible from the decision boundary, this can be achieved by the equation on the left, after that, lets apply mathematical plumbing by adding a new variable **Y** which is _-1_ when it is  a negative example, and _1_ when it is a positive example. And it turns out that we get the same equation!

<div style="text-align:center"><img src ="http://latex.codecogs.com/gif.latex?%5CLARGE%20W%20*%20%5Cvec%7BX%7D_&plus;%20&plus;%20b%20%5Cge%201%20%5Chspace%7B10mm%7D%20Y%20%28W%20*%20%5Cvec%7BX%7D_&plus;%20&plus;%20b%29%20%5Cge%201%20%5C%5C%20W%20*%20%5Cvec%7BX%7D_-%20&plus;%20b%20%5Cle%20-1%20%5Chspace%7B10mm%7D%20Y%28W%20*%20%5Cvec%7BX%7D_-%20&plus;%20b%29%20%5Cge%201"/></div

That can be expressed as follow for an example in the gutters:

<div style="text-align:center"><img src ="http://latex.codecogs.com/gif.latex?%5CLARGE%20Y%28W%20*%20%5Cvec%7BX%7D%20&plus;%20b%29%20%3D%201%20%5Chspace%7B10mm%7D%20%281%29"/></div

So far, we've defined a way to classify whether a example is a positive one or a negative one, also,we come up with a equation that defines the _support vector_ or a example inside the gutter.

Now, lets see the gutter width and how can be expressed. Regarding that **W** is a vector perpendicular to the street the following image explains the intuiton of the gutter.

![](./images/gutters.png)

## Maximizing the problem in the dual space

Our objective is to minimize the norm of **W** but in our problem we define earlier a constraint that must be fulfil  _[Equation 1]_, this objective can be transformed into the dual space by means of the Lagrangian like follows:

<div style="text-align:center"><img src ="http://latex.codecogs.com/gif.latex?%5Clarge%20L%20%3D%20%5Cfrac%7B1%7D%7B2%7D%20%7C%7CW%7C%7C%5E2%20-%20%5Csum_%7Bi%3D1%7D%5E%7Bp%7D%20%5Calpha_i%20%5By_i%28%5Cvec%7BW%7D%20*%20%5Cvec%7BX_i%7D%20&plus;b%29%29%5D%20%5C%5C%20%5Ctext%7BSubject%20to%20%7D%20%5Calpha_i%20%5Cge%200%20%5C%5C%20%5C%5C%20%5Cfrac%7B%5Cpartial%20L%7D%7B%5Cpartial%20%5Cvec%7BW%7D%7D%20%3D%20W%20-%20%5Csum_%7Bi%3D1%7D%5E%7Bp%7D%20%5Calpha_i%20y_i%20%5Cvec%7BX_i%7D%20%3D%200%20%5C%5C%20%5C%5C%20hence%2C%20%5Cvspace%7B23mm%7D%20W%20%3D%20%5Csum_%7Bi%3D1%7D%5E%7Bp%7D%20%5Calpha_i%20y_i%20%5Cvec%7BX_i%7D"/></div

<!---
Latex Snippet to the image above
[([L = \frac{1}{2} ||W||^2 - \sum_{i=1}^{p} \alpha_i [y_i(\vec{W * \vec{X_i} +b))] \\ \text{Subject to } \alpha_i \ge 0 \\ \\ \frac{\partial L}{\partial \vec{W}} =  W - \sum_{i=1}^{p} \alpha_i y_i \vec{X_i} = 0 \\ \\ hence, \vspace{23mm}  W = \sum_{i=1}^{p} \alpha_i y_i \vec{X_i}])]
-->

Now, we have figure out that the Lagrangian **L** doesn't deppens on the weight vector **W** but in the  linear combination of "some" examples, some examples because for some of them alpha will be zero.




