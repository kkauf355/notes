# LINQ
Language-Integrated Query (LINQ) is a powerful set of technologies based on the integration of query capabilities directly into the C# language. LINQ Queries are the first-class language construct in C# .NET, just like classes, methods, events. The LINQ provides a consistent query experience to query objects (LINQ to Objects), relational databases (LINQ to SQL), and XML (LINQ to XML).



### c# LINQ where clause
```c#
List<Product> products = GetProducts();
var list = (from prod in products
            where prod.ListPrice > 1000
            select prod).ToList();
```

### c# LINQ Distinct() method
```c#
List<Product> products = GetProducts();
var colors = (from prod in products
                select prod.Color).Distinct().ToList()
```

### c# LINQ Min() method
```c#
List<Product> products = GetProducts();
decimal value = (from prod in products
                    select prod.ListPrice).Min();
```