---
title: Basic Query
author: rowanmiller
ms.author: rowmil
manager: rowanmiller
ms.date: 10/27/2016
ms.topic: article
ms.assetid: ab6e35f1-397f-41c0-9ef4-85aec5466377
ms.prod: entity-framework-core
uid: querying/basic
---
# Basic Query

> [!WARNING]
> This documentation is for EF Core. For EF6.x and earlier release see [http://msdn.com/data/ef](http://msdn.com/data/ef).

Entity Framework Core uses Language Integrate Query (LINQ) to query data from the database. LINQ allows you to use C# (or your .NET language of choice) to write strongly typed queries based on your derived context and entity classes.

> [!TIP]
> You can view this article's [sample](https://github.com/aspnet/EntityFramework.Docs/tree/master/samples/Querying) on GitHub.

## 101 LINQ samples

This page shows a few examples to achieve common tasks with Entity Framework Core. For an extensive set of samples showing what is possible with LINQ, see [101 LINQ Samples](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).

## Loading all data

<!-- [!code-csharp[Main](samples/Querying/Querying/Basics/Sample.cs)] -->
````csharp
using (var context = new BloggingContext())
{
    var blogs = context.Blogs.ToList();
}
````

## Loading a single entity

<!-- [!code-csharp[Main](samples/Querying/Querying/Basics/Sample.cs)] -->
````csharp
using (var context = new BloggingContext())
{
    var blog = context.Blogs
        .Single(b => b.BlogId == 1);
}
````

## Filtering

<!-- [!code-csharp[Main](samples/Querying/Querying/Basics/Sample.cs)] -->
````csharp
using (var context = new BloggingContext())
{
    var blogs = context.Blogs
        .Where(b => b.Url.Contains("dotnet"))
        .ToList();
}
````
