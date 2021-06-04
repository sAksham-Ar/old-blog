---
layout: post
title:  "Basic Logical Operations"
category: C++
---

The are 3 basic logical operations in C++ i.e. `&&`(AND), `||` (OR) and `!`(NOT).AND means that  if and only if both of the statements are true then the result is true, while OR means that if only one of the statements is true then the result is true and NOT just reverses the result.

{% capture code %}
#include<iostream>
using namespace std;
int main()
{
    int a;
    cout<<"Enter the number:\n";
    cin>>a;
    if((a>50)&&(!(a>75)))
    {
        cout<<"The number is between 50 and 75";
    }
    else
    {
        cout<<"The number is not between 50 and 75";
    }
    return 0;
}
{% endcapture %}
{% include code.html code=code lang="cpp" %}

**OUTPUT:**

![output](/assets/Basic-Logical-Operations.png)
