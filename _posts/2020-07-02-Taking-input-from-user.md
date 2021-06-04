---
layout: post
title:  "Taking input from user"
category: C++
---

Today we will learn how to take input from user in C++.We will do this using `cin` in iostream library.`cin` takes input from keyboard and stores it in a variable like num.`\n` is used for going to next line so that output looks nice.

{% capture code %}
#include<iostream>
using namespace std;
int main()
{
   int num;
   char ch;
   cout<<"enter number:\n";
   cin>>num;
   cout<<"enter character:\n";
   cin>>ch;
   cout<<"number="<<num<<"\n";
   cout<<"character="<<ch;
   return 0;
}
{% endcapture %}
{% include code.html code=code lang="cpp" %}

**OUTPUT:**

![output](/assets/Taking-input-from-user.png)