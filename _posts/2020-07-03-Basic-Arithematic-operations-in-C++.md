---
layout: post
title:  "Basic Arithematic operations in C++"
category: C++
---

There are 5 basic arithematic operations in C++:

1. `+`: add
2. `-`: subtract
3. `*`: multiply
4. `/`: divide.
**Note: The second operand should not be zero and if both the operands are int then answer will rounded down to an integer , for decimal covert one of them to float.**
5. `%`:this gives the remainder.
**Note: The second operand should not be zero.**

{% capture code %}
#include<iostream>
using namespace std;
int main()
{
    int a,b;
    cout<<"enter a and b:\n";
    cin>>a>>b;
    cout<<"a+b="<<a+b<<"\n";
    cout<<"a-b="<<a-b<<"\n";
    cout<<"axb="<<a*b<<"\n";
    cout<<"a/b="<<a/b<<"\n";
    cout<<"a%b="<<a%b;
    return 0;
}
{% endcapture %}
{% include code.html code=code lang="cpp" %}

**OUTPUT:**

![output](/assets/Basic-Arithematic-operations-in-C++.png)