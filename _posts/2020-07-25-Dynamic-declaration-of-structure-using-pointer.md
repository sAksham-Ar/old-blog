---
layout: post
title:  "Dynamic declaration of structure using pointer"
category: C++
---

We can dynamically declare sturrcture is C++ using just new and the name of the structure.To access its inner variables we have to use `->` instead of `.` as it is a pointer ,however we can us `.` with `*` behind the pointer so that  it becomes a structure variable.

{% capture code %}
#include<iostream>
using namespace std;
struct boy
{
    char name[80];
    int age;
};
int main()
{
    boy *b1;
    b1= new boy;
    cout<<"Enter name:\n";
    cin>>b1->name;
    cout<<"Enter age:\n";
    cin>>b1->age;
    cout<<"Name is: "<<(*b1).name<<" Age is: "<<(*b1).age;
    return 0;
} 
{% endcapture %}
{% include code.html code=code lang="cpp" %}

**OUTPUT:**

![output](/assets/Dynamic-declaration-of-structure-using-pointer.png)
