# C# 发展史

## Intro

> C#，读作C Sharp，是微软推出的一种基于.NET平台的、面向对象的高级编程语言。是微软公司在2000年发布的一种新的编程语言，主要由安德斯·海尔斯伯格（Anders Hejlsberg）主持开发，它是第一个面向组件的编程语言，其源码会编译成msil再运行。它借鉴了Delphi的一个特点，与COM(组件对象模型)是直接集成的，并且新增了许多功能及语法糖。

## C# 1.x

自 2000 年 C#1.0 发布之后，微软在2003年4月又发布了 C# 1.1 主要是修复BUG，这里统称为1.x

- 面向对象
- 内存自动回收，GC
- 属性
- 反射

## C# 2

- 泛型
- 分部类
- 静态类型
- 迭代器（yield return）
- 匿名方法（lambda 表达式）
- 可空类型
- 委托的协变逆变
- 属性访问器可以被单独设置访问级别
- `??`表达式

## C# 3

- Linq
- 类型初始化器
- 集合初始化器
- 匿名类型
- 局部变量类型推断(`var`)
- Lambda 表达式
- 自动属性
- 扩展方法
- 分部方法
- 表达式树（Expression Tree）

## C# 4

- 动态编程（`dynamic`）
- 具名参数与可选参数
- 泛型的协变和逆变
- TPL任务并行库，基于Task的异步编程

## C# 5

- 异步编程(`async`&`await`)
- 调用方信息特性(`CallerMemberName`&`CallerFilePath`&`CallerLineNumber`)

## C# 6

- 静态导入（`using static`）
- 异常过滤器（`when(ex.ExceptionCode == 111)`）
- 属性初始化器（`public int PageIndex {get;} = 1;`）
- 字典初始化器

    ``` csharp
    private Dictionary<int, string> webErrors = new Dictionary<int, string>
    {
        [404] = "Page not Found",
        [302] = "Page moved, but left a forwarding address.",
        [500] = "The web server can't come out to play today."
    };
    ```

- 字符串插值（`$"abc{123}def"`）
- nameof 运算符
- null判断传播运算符（`a?SomeProperty?.Abc??"abcd"`）
- 表达式体方法（`int Add(int a,int b) => a+b;`）
- catch和finally子句中支持 await
- 只读自动属性（`public int Count {get;}`）

## C# 7

- out 变量（`int.TryParse("123", out var num);`）
- 优化元祖支持，支持变量名（`(int max,int min) top = (3,1);`）
- 废弃变量（`if(int.TryParse("123",out _))`）
- 模式匹配（`if(abc is int num)`switch...case支持模式匹配）
- ref local and ref return（`ref return 123;`）
- 本地方法（局部方法）
- 更多的支持表达式体方法（增加支持属性和索引器上实现构造函数、终结器以及 get 和 set 访问器）
- throw表达式
- 数字文本语法改进

  误读的数值常量可能使第一次阅读代码时更难理解。 当这些数字被用作位掩码或其他符号而非数字值时，通常会发生这种情况。 C# 7.0 包括两项新功能，使得更容易以最可读的方式写入数字来用于预期用途：二进制文本和数字分隔符

  ``` csharp
  public const int Sixteen =   0b0001_0000;
  public const int ThirtyTwo = 0b0010_0000;
  public const int SixtyFour = 0b0100_0000;
  public const int OneHundredTwentyEight = 0b1000_0000;

  public const long BillionsAndBillions = 100_000_000_000;

  public const double AvogadroConstant = 6.022_140_857_747_474e23;
  public const decimal GoldenRatio = 1.618_033_988_749_894_848_204_586_834_365_638_117_720_309_179M;
  ```

## C# 7.1

- 异步Main方法（`async Main()`）
- 默认常值表达式（`Func<string, bool> whereClause = default;`）
- 推断元组元素名称

  ``` csharp
  // C# 7
  int count = 5;
  string label = "Colors used in the map";
  var pair = (count: count, label: label);

  // C# 7.1
  int count = 5;
  string label = "Colors used in the map";
  var pair = (count, label); // element names are "count" and "label"
  ```

## C# 7.2

- 语言版本选择(支持在项目中指定要使用的C#版本)
- 数值文字中的前导下划线

  C# 7.0 中实现了对数字分隔符的支持，但这不允许文字值的第一个字符是 `_`。 十六进制文本和二进制文件现可以 `_` 开头。

  ``` csharp
  int binaryValue = 0b_0101_0101;
  ```

- private protected 访问修饰符（可通过包含同一程序集中声明的类或派生类来访问成员）

## C# 7.3(Preview)

- 元组支持相等性比较
- 新的泛型约束（Enum,Delegate,unmanaged）
- Ref 局部变量重新分配（Ref 局部变量和 ref 参数现在可通过 ref 分配运算符重新分配 `= ref`）
- Stackalloc 初始化表达式

  ``` csharp
  Span<int> x = stackalloc[] { 1, 2, 3 };
  ```

- 初始化表达式和查询中的表达式变量
- 支持字段的特性

  允许自动实现的属性上的 [field: …] 特性定位其支持字段

  ``` csharp
  // C# 7.3
  [Serializable]
  public class Foo {
    [field: NonSerialized]
    public string MySecret { get; set; }
  }

  // above code equals the code below
  [Serializable]
  public class Foo {
    [NonSerialized]
    private string MySecret_backingField;

    public string MySecret {
        get { return MySecret_backingField; }
        set { MySecret_backingField = value; }
    }
  }
  ```

## C# 8(Preview)

- 可空引用类型（引用类型默认不可为空，如果需要为可空则需要显示声明`string? abc = null;`）

## Reference

- <https://docs.microsoft.com/zh-cn/dotnet/csharp/whats-new/csharp-version-history>
- <https://docs.microsoft.com/zh-cn/dotnet/csharp/whats-new/csharp-6>
- <https://docs.microsoft.com/zh-cn/dotnet/csharp/whats-new/csharp-7>
- <https://docs.microsoft.com/zh-cn/dotnet/csharp/whats-new/csharp-7-1>
- <https://docs.microsoft.com/zh-cn/dotnet/csharp/whats-new/csharp-7-2>
- <https://docs.microsoft.com/zh-cn/visualstudio/releasenotes/vs2017-relnotes#csharp>
- <https://github.com/dotnet/csharplang>
- <https://baike.baidu.com/item/c%23/195147>
- <https://zh.wikipedia.org/wiki/C%E2%99%AF>    