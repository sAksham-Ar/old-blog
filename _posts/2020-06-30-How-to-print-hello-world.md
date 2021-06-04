---
layout: post
title:  "How to print Hello World"
category: C++
---

Today we will learn to print hello world in C++.First we would include the library iostream which has the cout which is needed to print.then we write `int main()` which is the function where we write the main code we need to run.The curly brackets are inside which we write our code. Then we write the `cout` command to print hello world.The semicolon represents the end of one line of code.As we used `int main()` the function requires us to return an integer so we use `return 0`.

{% capture code %}
#include<iostream>
using namespace std;
int main()
{
    cout<<"Hello World!";
    return 0;
}
{% endcapture %}
{% include code.html code=code lang="cpp" %}

**OUTPUT:**

![output](/assets/How-to-print-hello-world.png)