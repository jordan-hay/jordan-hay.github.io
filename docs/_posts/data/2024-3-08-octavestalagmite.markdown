---
layout: post
title:  "Optimizing the Stalagmite Function using Octave and Genetic Algorithm in Google Colab"
date:   2024-3-08 07:25:17 -0800
categories: jekyll update data
---
<a target="_blank" href="https://colab.research.google.com/github/jordan-hay/jordan-hay.github.io/blob/main/docs/assets/Genetic_Algorithm_Octave.ipynb
">
  
# Introduction 

In this blog post, we will explore the application of a Genetic Algorithm (GA) to optimize the Stalagmite function. The Stalagmite function is a mathematical model that involves multiple variables and is known for its complex behavior. We'll employ the GA to find the optimal input values that maximize the output of this function.

## Setting Up the Environment

Before diving into the optimization process, we need to set up our environment by installing the required packages. Run the following code to ensure everything is in place:

```python
!apt install octave &> /dev/nul
!pip install oct2py &> /dev/nul
import oct2py
%load_ext oct2py.ipython

!octave --eval "pkg install -forge ga"
```

Now that our environment is ready, let's define the Stalagmite function and visualize its behavior.

```python
%%octave
clear all
close all
clc
pkg load ga

function [output]=stalagmite(input_vector)
    x1=input_vector(1);
    x2=input_vector(2);
    f1x1=(sin(5.1*pi*x1+.5))^6;
    f1x2=(sin(5.1*pi*x2+.5))^6;
    f2x1=exp(-4*log(2)*(x1-.0667)^2/.64);
    f2x2=exp(-4*log(2)*(x2-.0667)^2/.64);
    [output]=-(f1x1*f2x1*f1x2*f2x2);
end
```

## Visualizing the Stalagmite Function

Now, let's visualize the Stalagmite function by creating a meshgrid of input values and calculating the corresponding function values.

```python
%%octave

x1s=linspace(0,.6,150);
x2s=linspace(0,.6,150);
num_cases=40;
[xx1 xx2]=meshgrid(x1s,x2s);
for i=1:length(xx1)
    for j= 1:length(xx2)
        input_vector(1)=xx1(i,j);
        input_vector(2)=xx2(i,j);
        f(i,j)=stalagmite(input_vector);
    end
end
```

## Applying the Genetic Algorithm

With a clear understanding of the Stalagmite function, let's apply the Genetic Algorithm to find the optimal input values that maximize the output.

```python
%%octave

for i=1:num_cases
    [inputs, fopt(i)]=ga(@stalagmite,2,[],[],[],[],[0;0],[1;1]);
    x1opt(i)=inputs(1);
    x2opt(i)=inputs(2);
end
```

## Visualizing the Optimization Results

Finally, let's visualize the optimization results by plotting the Stalagmite function surface and marking the optimal points found by the Genetic Algorithm.

```python
%%octave
figure(1)
subplot(2,1,1)
hold on
surfc(xx1,xx2,-f)
shading interp
plot3(x1opt,x2opt,-fopt,'marker','o','markersize',5,'markerfacecolor','r')
title('Stalagmite')
xlabel('X1 values')
ylabel('X2 values')
view(30,30)
subplot(2,1,2)
plot(-fopt)
xlabel('Iterations')
ylabel('Function Maximum')
```
## Conclusion
In this blog post, we've explored the optimization of the Stalagmite function using a Genetic Algorithm. The combination of visualizing the function and applying the GA provides insights into the behavior of the function and helps find optimal input values. This process is valuable in various fields where complex functions need to be optimized for better performance.

