---
title: Differences Between MVT of Django and MVC
date: 2024-07-03 1:10:00 +0800
categories: [Fundamental, Software Architecture]
tags: [initial version]
description: While some may argue that so-called MVT pattern of Django is indeed a variant of MVC pattern, differences do exist between the two patterns. 
---

I was introduced to MVT pattern of Django first, and then the more general MVC pattern, in multiple Django tutorials. I was told that MVT is indeed a variant of MVC, so I've always tried to understand what MVC is based on how a typical Django app is structured. Finally I found that it's an improper, if it isn't wrong, way to understand since they are not that same even in naming. 

## TL; DR

Read the [explanation](https://docs.djangoproject.com/en/5.0/faq/general/#django-appears-to-be-a-mvc-framework-but-you-call-the-controller-the-view-and-the-view-the-template-how-come-you-don-t-use-the-standard-names) in Django Documentation for more accurate clarification. 

## My Principles 

Affected by the great pioneers of our industry, and being a developer rather than a scholar, **making things done takes priority**. In my opinions, acronyms, different naming conventions or the subtle differences among them aren't really matter when one is able to design powerful and efficient system that solves practical problems. 

But, on the other hand, understanding those acronyms and, more importantly, **the well-summarized methodology and valuable experience behind them helps us keep up with our pioneers' pace and build better systems**. 

## Differences

To understand what MVC and what MVT is and figure out the differences between them, I excerpted some description about them from two different documentations below, one of which is the Django documentation and the other is the ASP.NET documentation, both are listed in the references section. 

### MVT

> In our interpretation of MVC, **the “view” describes the data that gets presented to the user**. It’s not necessarily how the data looks, but which data is presented. **The view describes which data you see, not how you see it**. It’s a subtle distinction.
>
> So, in our case, **a “view” is the Python callback function for a particular URL**, because that callback function describes which data is presented.
>
> Furthermore, it’s sensible to separate content from presentation – which is where templates come in. **In Django, a “view” describes which data is presented, but a view normally delegates to a template, which describes how the data is presented**.
>
> **Where does the “controller” fit in, then? In Django’s case, it’s probably the framework itself**: the machinery that sends a request to the appropriate view, according to the Django URL configuration.

> A model is the single, definitive source of information about your data. **It contains the essential fields and behaviors of the data you’re storing. Generally, each model maps to a single database table.**

### MVC

> The Model-View-Controller (MVC) architectural pattern separates an application into three main groups of components: Models, Views, and Controllers. This pattern helps to achieve separation of concerns. Using this pattern, user requests are routed to a Controller which is responsible for working with the Model to perform user actions and/or retrieve results of queries. **The Controller chooses the View to display to the user, and provides it with any Model data it requires**.
>
> **Business logic should be encapsulated in the model**, along with any implementation logic for persisting the state of the application.
>
> There should be minimal logic within views, and **any logic in them should relate to presenting content**.
>
> Controllers shouldn't be overly complicated by too many responsibilities. **To keep controller logic from becoming overly complex, push business logic out of the controller and into the domain model**.

**As we can see, view in Django isn't directly responsible for presentation but through delegating a template to achieve this goal. Also, business logic is encapsulated in view rather than model. At the same time, controller isn't defined separately but acted by the framework itself**. 

## References

1. [FAQ: General - Django documentation - Django](https://docs.djangoproject.com/en/5.0/faq/general/#django-appears-to-be-a-mvc-framework-but-you-call-the-controller-the-view-and-the-view-the-template-how-come-you-don-t-use-the-standard-names)
2. [Models - Django documentation - Django](https://docs.djangoproject.com/en/5.0/topics/db/models/)
3. [Overview of ASP.NET Core MVC - Microsoft Learn](https://learn.microsoft.com/en-us/aspnet/core/mvc/overview?view=aspnetcore-8.0)

