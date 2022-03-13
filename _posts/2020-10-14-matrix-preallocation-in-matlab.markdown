---
layout: distill
title: How does matrix preallocation in MATLAB affect computation speed?
date: 2020-10-14 09:00:00
description: A simple demonstration to show the effect of preallocation in MATLAB
authors:
  - name: Tirtharaj Dash
    url: "https://tirtharajdash.github.io/"
    affiliations:
      name: APPCAIR </br> BITS Pilani, Goa Campus
---

Recently, I was asked by a friend "why do your MATLAB codes contains a preallocation line for matrices?... Isn't it easy to just do things in place and let MATLAB understand what the initialisation of the matrix should be." "Well, it would work; but, have you ever thought about how would it affect the computation speeed (in a way, the overall code running efficiency)", I said.

So, to address the above question, I wanted to demonstrate it visually using a small MATLAB code that has both preallocation and non-preallocation routines. The problem is simple. Show the effect of preallocation on continous array appends and updates. If you are comfortable in looking at the code, here is it:

{% highlight matlab %}

%A baby program to show you the effect of preallocation in MATLAB
%By: Tirtharaj Dash

close all; %you may comment this

rng(1);

hold on;
grid on;
box on;
xlabel('n');
ylabel('time(s)');
title('Method 1: blue, Method 2: red');

%test for various sizes
for n = 1:100:10000
    
    %Method 1: without preallocating
    tic;
    A = []; %empty matrix but doesn't preallocate
    for i = 1:n
        A = [A; rand(10,2)]; %append A
    end
    etime = toc;
    plot(n,etime,'bo');
    
    %Method 2: with preallocation
    tic;
    A = double.empty(2,0); %create an empty matrix of class double
    for i = 1:n
        A(:,end+1:end+10) = rand(2,10); %append A (notice!!!)
    end
    etime = toc;
    plot(n,etime,'ro');
    drawnow();
end

{% endhighlight %}
<div class="col three caption">
    Please let me know if you think there is any bug in this program.
</div>

The method 1 is without preallocation, and method 2 is with preallocation. The preallocation in method 2 is nothing but start with an empty matrix and keep appending a random numbered array to it. See the speed difference yourself.

<div class="img_row">
    <center>
    <img class="four" src="{{ site.baseurl }}/assets/img/prealloctest.jpg">
    <img class="four" src="{{ site.baseurl }}/assets/img/prealloctest.gif"/>
    </center>
</div>
<div class="col three caption">
    Method 1 (without preallocation) is way slower than Method 2 (with preallocation)
</div>

Now, you may be thinking, so what? It is just a matter of few seconds. Well, I want to share with some numbers:

*A program that I wrote **without preallocation** took roughly **18Hr** in a machine with 64GB memory, and 16-core Intel Xeon CPU. And, the exact same program **with preallocation** finished the execution in **5Min** in the same machine. Convinced?*

<br/>

Let me know, if this post helped you. Also, you may be interested in going through the official page of Mathworks on <a rel="external nofollow" href="https://in.mathworks.com/help/matlab/matlab_prog/preallocating-arrays.html" target="_blank">Preallocation</a>. Cheers!
