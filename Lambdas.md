# Lambdas

Lambdas are written with a single space before and after the `=>`:

```csharp
// Great.
Func<int, int> square = i => i * i;

// Terrible.
Func<int, int> square = i=>i * i;
```

Always prefer lambdas, `Func<>`, and `Action<>` types to `delegate`. The only recommended use of `delegate` is when the body of your anonymous method doesn't reference any of its arguments:

```csharp
thing.EventWithSenderAndEventArgs += delegate {
	Console.WriteLine ("EventWithSenderAndEventArgs raised.");
};
```

If your lambda takes a single argument, omit the parentheses around the argument list:

```csharp
// Great!
var admins = Users.Select (user => user.IsAdministrator);

// Silly.
var admins = Users.Select ((user) => user.IsAdministrator);
```

Whenever possible, omit types from lambda argument lists, and use simple names:

```csharp
// Great:
list.OnScroll += (sender, e) => {
	...
};

// Passé:
list.OnScroll += (object sender, EventArgs e) => {
	...
};
```

When the body of a lambda is a simple statement or expression, don't use a block:

```csharp
// Excellent!
var averageSalary = employees.Average (employee => employee.Salary);

// Inconceivable!
var averageSalary = employees.Average (employee => { return employee.Salary; });
```

It is acceptable to use single-character argument names in lambdas if the receiver is an `IEnumerable` and is named in such a way as to make the lambda argument obvious, and the lambda argument name is the first character of the receiver's identifier:

```csharp
// Acceptable:
var averageSalary = employees.Average (e => e.Salary);

// Acceptable:
var averageSalary = employees.Average (employee => employee.Salary);
```
