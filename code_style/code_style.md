# Code style

Best resource to start from: [coding-style.md at dotnet/corefx](https://github.com/dotnet/corefx/blob/master/Documentation/coding-guidelines/coding-style.md). 

Although there are some more controversial points than other. Namely:
* Prefixing internal and private static fields with `s_` and thread static fields with `t_`. More common suggestion would be to prefix them only with `_` like other private and internal fields.