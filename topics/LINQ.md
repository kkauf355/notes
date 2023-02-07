# LINQ
Language-Integrated Query (LINQ) is a powerful set of technologies based on the integration of query capabilities directly into the C# language. LINQ Queries are the first-class language construct in C# .NET, just like classes, methods, events. The LINQ provides a consistent query experience to query objects (LINQ to Objects), relational databases (LINQ to SQL), and XML (LINQ to XML).

## Examples

### OrderBy
#### OrderBy
```c#
// Query
list = (from prod in products
        orderby prod.Name
        select prod).ToList();
// Method
list = products.OrderBy(prod => prod.Name).ToList();
```
#### OrderBy Two Fields 
```c#
// Query
list = (from prod in products
              orderby prod.Color descending, prod.Name
              select prod).ToList();
// Method
list = products.OrderByDescending(prod => prod.Color)
                      .ThenBy(prod => prod.Name).ToList();
```

### Where
#### Where
```c#
// Query
list = (from prod in products
              where prod.Name.StartsWith("S")
              select prod).ToList();
// Method
list = products.Where(prod => prod.Name.StartsWith("S")).ToList();
```
#### Where Two Fields
```c#
// Query
list = (from prod in products
              where prod.Name.StartsWith("L") && prod.StandardCost > 200
              select prod).ToList();
// Method
list = products.Where(prod => prod.Name.StartsWith("L") &&
                        prod.StandardCost > 200).ToList();
```

### Single
#### First or Default with Default Method
```c#
// Query
value = (from prod in products
        select prod)
        .FirstOrDefault(prod => prod.Color == "Red",
                            new Product { ProductID = -1, Name = "PRODUCT NOT FOUND" });
// Method
value = products.FirstOrDefault(prod => prod.Color == "Red",
                                      new Product { ProductID = -1, Name = "NOT FOUND" });
```
#### Last of Default
```c#
// Query
value = (from prod in products
               select prod)
               .LastOrDefault(prod => prod.Color == "Red");
// Method
value = products.LastOrDefault(prod => prod.Color == "Red");
```
#### Single or Default
```c#
// Query
value = (from prod in products
               select prod)
              .SingleOrDefault(prod => prod.ProductID == 706);
// Method
value = products.SingleOrDefault(prod => prod.ProductID == 706);
```

### Partition Distinct
#### Take
Use Take() to select a specified number of items from the beginning of a collection
```c#
// Query
list = (from prod in products
              orderby prod.Name
              select prod).Take(5).ToList();
// Method
list = products.OrderBy(prod => prod.Name).Take(5).ToList();
```
#### Take Range
Use Take() to select a specified number of items from the beginning of a collection
```c#
// Query
list = (from prod in products
              orderby prod.Name
              select prod).Take(5..8).ToList();
// Method
list = products.OrderBy(prod => prod.Name).Take(5..8).ToList();
```
#### Take While
Use TakeWhile() to select a specified number of items from the beginning of a collection based on a true 
```c#
// Query
list = (from prod in products
              orderby prod.Name
              select prod).TakeWhile(prod => prod.Name.StartsWith("A")).ToList();
// Method
list = products.OrderBy(prod => prod.Name)
                      .TakeWhile(prod => prod.Name.StartsWith("A")).ToList();
```
#### Skip
Use Skip() to move past a specified number of items from the beginning of a collection
```c#
// Query
list = (from prod in products
              orderby prod.Name
              select prod).Skip(30).ToList();
// Method
list = products.OrderBy(prod => prod.Name).Skip(30).ToList();
```
#### Skip While
Use SkipWhile() to move past a specified number of items from the beginning of a collection based on a true condition
```c#
// Query
list = (from prod in products
              orderby prod.Name
              select prod).SkipWhile(prod => prod.Name.StartsWith("A")).ToList();
// Method
list = products.OrderBy(prod => prod.Name)
        .SkipWhile(prod => prod.Name.StartsWith("A")).ToList();
```
#### Distinct
The Distinct() operator finds all unique values within a collection.
```c#
// Query
list = (from prod in products
              select prod.Color)
              .Distinct().OrderBy(c => c).ToList();
// Method
list = products.Select(p => p.Color).Distinct().OrderBy(c => c).ToList();
```
#### Distinct By
The DistinctBy() operator finds all unique values within a collection using a property.
```c#
// Query
list = (from prod in products
              select prod)
              .DistinctBy(prod => prod.Color)
              .OrderBy(p => p.Color).ToList();
// Method
list = products.DistinctBy(prod => prod.Color, default)
                      .OrderBy(p => p.Color).ToList();
```
#### Chunk
Chunk() splits the elements of a larger list into a collection of arrays of a specified size where each element of the collection is an array of those items.
```c#
// Query
list = (from prod in products
              select prod).Chunk(5).ToList();
// Method
list = products.Chunk(5).ToList();
```

### Contains
#### All
Use All() to see if all items in a collection meet a specified condition
```c#
// Query
bool value = (from prod in products
               select prod)
                .All(prod => prod.ListPrice > prod.StandardCost);
// Method
bool value = products.All(prod => prod.ListPrice > prod.StandardCost);
```
#### Any
Use Any() to see if at least one item in a collection meets a specified condition
```c#
// Query
bool value = (from sale in sales
               select sale)
                .Any(sale => sale.LineTotal > 10000);
// Method
bool value = sales.Any(sale => sale.LineTotal > 10000);
```
#### Contains
Use the Contains() operator to see if a collection contains a specific value
```c#
// Query
bool value = (from num in numbers
               select num).Contains(3);
// Method
bool value = numbers.Contains(3);
```
#### Contains Comparer
Use the Contains() operator to see if a collection contains a specific value
```c#
ProductIdComparer pc = new();
// Query
bool value = (from prod in products
               select prod)
                .Contains(new Product { ProductID = 744 }, pc);
// Method
bool value = products.Contains(new Product { ProductID = 744 }, pc);
```

### Compare
#### Sequence Equal for Integers
SequenceEqual() compares two different collections to see if they are equal
When using simple data types such as int, string, a direct comparison between values is performed
```c#
// Query
bool value = (from num in list1
               select num)
               .SequenceEqual(list2);
// Method
bool value = list1.SequenceEqual(list2);
```
#### Sequence Equal for Objects
When using a collection of objects, SequenceEqual() performs a comparison to see if the two object references point to the same object. For this reason, we need a comparer.

#### Sequence Equal using Comparer
Use an EqualityComparer class to determine if the objects are the same based on the values in properties
```c#
// Query
bool value = (from prod in list1
               select prod)
               .SequenceEqual(list2, pc);
// Method
value = list1.SequenceEqual(list2, pc);
// Product Comparer
public override bool Equals(Product x, Product y)
{
    // Compare each property to the other to determine equality
    return (x.ProductID == y.ProductID &&
            x.Name == y.Name &&
            x.Color == y.Color &&
            x.Size == y.Size &&
            x.ListPrice == y.ListPrice &&
            x.StandardCost == y.StandardCost);
}
public override int GetHashCode(Product obj)
{
    string value = obj.ProductID.ToString() + 
    obj.Name + 
    obj.Color + 
    obj.Size + 
    obj.ListPrice.ToString() + 
    obj.StandardCost.ToString();

    return value.GetHashCode();
}
```
#### Except for Integers
Find all values in one list that are not in the other list
```c#
// Query
List<int> list = (from num in list1
              select num)
              .Except(list2).ToList();
// Method
List<int> list = list1.Except(list2).ToList();
```
#### Except for Objects
Find all products that do not have sales
```c#
// Query
list = (from prod in products
              select prod.ProductID)
              .Except(from sale in sales select sale.ProductID).ToList();
// Method
list = products.Select(prod => prod.ProductID)
              .Except(sales.Select(sale => sale.ProductID)).ToList();
```
#### Except using Comparer
Find all products that are in one list but not the other using a comparer class
```c#
// Query
List<Product> list = (from prod in list1
              select prod)
              .Except(list2, pc).ToList();
// Method
List<Product> list = list1.Except(list2, pc).ToList();
```
#### Except By
ExceptBy() finds products within a collection that DO NOT compare to a List<string> against a specified property in the collection.
The default comparer for ExceptBy() is 'string'
```c#
// Query
List<Product> list = (from prod in products
              select prod)
              .ExceptBy(colors, p => p.Color).ToList();
// Method
List<Product> list = products.ExceptBy(colors, p => p.Color).ToList();
```
#### Except by for Objects
Find all products that do not have sales
Change the default comparer for ExceptBy()
```c#
// Query
List<Product> list = (from prod in products
              select prod)
              .ExceptBy<Product, int>(
                from sale in sales select sale.ProductID, 
                prod => prod.ProductID).ToList();
// Method
List<Product> list = products.ExceptBy<Product, int>(sales.Select(s => s.ProductID), prod => prod.ProductID).ToList();
```
#### Intersect for Integers
Intersect() finds all values in one list that are also in the other list
```c#
// Query
List<int> list = (from num in list1
              select num)
              .Intersect(list2).ToList();
// Method
List<int> list = list1.Intersect(list2).ToList();
```
#### Intersect for Objects
Find all products that have sales
```c#
// Query
List<int> list = (from prod in products
              select prod.ProductID)
              .Intersect(from sale in sales select sale.ProductID).ToList();
// Method
List<int> list = products.Select(prod => prod.ProductID)
              .Intersect(sales.Select(sale => sale.ProductID)).ToList();
```
#### Intersect using Comparer
Intersect() finds all products that are in common between two collections using a comparer class
```c#
// Query
List<Product> list = (from prod in list1
              select prod)
              .Intersect(list2, pc).ToList();
// Method
List<Product> list = list1.Intersect(list2, pc).ToList();
```
#### Intersect By
Find products within a collection by comparing a List<string> against a specified property in the collection.
```c#
// Query
List<Product> list = (from prod in products
              select prod)
              .IntersectBy(colors, p => p.Color).ToList();
// Method
List<Product> list = products.IntersectBy(colors, p => p.Color).ToList();
```
#### Intersect By for Objects
Find all products that have sales using a 'int' key selector
Change the default comparer for IntersectBy()
```c#
// Query
List<Product> list = (from prod in products
              select prod)
              .IntersectBy<Product, int>(from sale in sales select sale.ProductID, prod => prod.ProductID).ToList();
// Method
List<Product> list = products.IntersectBy<Product, int>(sales.Select(s => s.ProductID), prod => prod.ProductID).ToList();
```

###

```c#
// Query

// Method

```

### c# LINQ Min() method
```c#
List<Product> products = GetProducts();
decimal value = (from prod in products
                    select prod.ListPrice).Min();
```