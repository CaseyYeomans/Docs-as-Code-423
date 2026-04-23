# Creating FilterExpression Properties

The FilterExpression property allows the caller to specify one or more filter criteria that are applied essentially as a **WHERE** clause when the database is searched for the members that meet the specified criteria.

The FilterExpression can be made use of by using **Profisee.MasterDataMaestro.Services.Contracts.DataContracts.Common.Expression.Filter**

- *static* Filter.On() - starts a filter. Can take another Filter, an Expression (i.e. FilterExpression), or take in an attribute name, operator, and value(s)
- *static* Filter.OnGroup() - starts a filter with a group immediately, takes another Filter or Expression
- And() - combines the filter using AND with another Filter, Expression, or attributeName/operator/value(s)
- Or() - combines the filter using OR with another Filter, Expression, or attributeName/operator/value(s)
- AndGroup() - combines the filter using AND with another Filter or Expression (usually a grouped filter)
- OrGroup() - combines the filter using OR with another Filter or Expression (usually a grouped filter)
- FilterExpression - gets the Expression the Filter class has built

The basic parameters of a filter are as follows:

1. *attributeName* - the name of the attribute for the specified entity that will be examined from a filtering perspective
2. *operator* - one of the following 3 Enums:

- Profisee.MasterDataMaestro.Services.DataContracts.UnaryOperator
- Profisee.MasterDataMaestro.Services.DataContracts.BinaryOperator
- Profisee.MasterDataMaestro.Services.DataContracts.TernaryOperator

For more information regarding the operator Enums see the [Filter Operators Overview](5bbf9ea5-9629-4052-aeb6-b4eb12c802eb.htm) topic.
3. *comparisonValue* - the value or pattern being compared to the specified attribute

In order to create a FilterExpression, you need to use the Filter helper class. Start out by including this using in your using block:

```
1| using Profisee.MasterDataMaestro.Services.Contracts.DataContracts.Common.Expression;
```

After this we can start working with FilterExpressions. Let's start with a simple filter:

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i29e7c82a49f6babd.png)

Using a FilterExpression would look like this:

```
1| Filter.On("Name", BinaryOperator.Contains, "Bike").FilterExpression;
```

The Filter.On starts the filter and the .FilterExpression converts it to a FilterExpression.

A bigger filter would look like this:![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i17c712ca13f62f5d.png)

Using a FilterExpression would look like this:

```
1 Filter.On("Name", BinaryOperator.Contains, "Bike")
2 .And("Color", BinaryOperator.Equals, "BLK")
3 .And("SellStartDate", BinaryOperator.GreaterThan, new DateTime(1990, 1, 1))
4 .And("MSRP", TernaryOperator.Between, 0, 1000)
5 .And("Picture", UnaryOperator.NotBlank).FilterExpression;
```

The next example shows the same filter, but with a group:![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i3ac548e07a57a5c.png)

Using a FilterExpression would look like this:

```
1 Filter.On("Name", BinaryOperator.Contains, "Bike")
2 .AndGroup(Filter.On("Color", BinaryOperator.Equals, "BLK")
3 .Or("Color", BinaryOperator.Equals, "BLU"))
4 .And("SellStartDate", BinaryOperator.GreaterThan, new DateTime(1990, 1, 1))
5 .And("MSRP", TernaryOperator.Between, 0, 1000)
6 .And("Picture", UnaryOperator.NotBlank).FilterExpression;
```