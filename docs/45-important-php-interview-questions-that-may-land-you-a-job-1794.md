# 45 个可能帮你找到工作的重要 PHP 面试问题

> 原文：<https://dev.to/fullstackcafe/45-important-php-interview-questions-that-may-land-you-a-job-1794>

[![45 Important PHP Interview Questions That May Land You a Job](img/6d0bb3e6e38901815e81924a896e3b66.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--_iVsD5Qi--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://images.pexels.com/photos/988914/pexels-photo-988914.jpeg%3Fauto%3Dcompress%26cs%3Dtinysrgb%26dpr%3D2%26w%3D500) 
澳洲 PHP 开发人员平均工资为每年 95000 美元或每小时 48.72 美元。入门级职位的起薪为每年 55，000 美元，而大多数有经验的员工的年薪高达 161，500 美元。跟着学习 45 个重要的 PHP 面试问题，它们可能会帮你找到工作。

> 最初发表于 [FullStack。永远不要再错过你的技术面试](https://www.fullstack.cafe)

### Q1:= =和= = = =有什么区别？

> 题目: **PHP**
> 难度:⭐

*   运算符`==`在两个不同类型之间转换，如果它们不同的话
*   `===`操作符执行一个“*类型安全比较*

这意味着只有当两个操作数具有相同的类型和相同的值时，它才会返回 true。

```
1 === 1: true
1 == 1: true
1 === "1": false // 1 is an integer, "1" is a string
1 == "1": true // "1" gets casted to an integer, which is 1
"foo" === "foo": true // both operands are strings and have the same value 
```

🔗**来源:**【stackoverflow.com】T2

### Q2:你如何通过引用传递一个变量？

> 题目: **PHP**
> 难度:⭐

为了能够通过**引用**来传递变量，我们在变量前面使用了一个*符号*，如下:

```
$var1 = &$var2 
```

🔗**来源:**【guru99.com】T2

### Q3:$ GLOBALS 是什么意思？

> 题目: **PHP**
> 难度:⭐

`$GLOBALS`是关联数组，包括对当前脚本全局范围内定义的所有变量的引用。

🔗**来源:**【guru99.com】T2

### Q4:ini _ set()有什么用？

> 题目: **PHP**
> 难度:⭐

PHP 允许用户使用 ini_set()修改 php.ini 中提到的一些设置。该函数需要两个字符串参数。第一个是要修改的设置的名称，第二个是要分配给它的新值。

给定的代码行将启用脚本的 display_error 设置，如果它被禁用的话。

`ini_set('display_errors', '1');`

我们需要将上面的语句放在脚本的顶部，这样，该设置会一直保持启用状态，直到最后。此外，通过 ini_set()设置的值仅适用于当前脚本。此后，PHP 将开始使用 php.ini 中的原始值。

🔗**来源:**【github.com/Bootsity】T2

### Q5:什么时候应该使用 require vs. include？

> 题目: **PHP**
> 难度:⭐⭐

`require()`功能与`include()`相同，除了它处理错误的方式不同。如果出现错误，`include()`函数会生成一个警告，但是脚本会继续执行。`require()`产生致命错误，脚本将停止。

我的建议是 99.9%的时间都用`require_once`就好。

相反，使用`require`或`include`意味着你的代码在其他地方**不可重用**，也就是说，你引入的脚本实际上是在执行代码，而不是提供一个类或一些函数库。

🔗**来源:**【stackoverflow.com】T2

### Q6:PHP 中的 stdClass 是什么？

> 题目: **PHP**
> 难度:⭐⭐

`stdClass`只是一个通用的“空”类，在将其他类型转换为对象时使用。`stdClass`是**而不是**PHP 中对象的基类。这很容易证明:

```
class Foo{}
$foo = new Foo();
echo ($foo instanceof stdClass)?'Y':'N'; // outputs 'N' 
```

它对匿名对象、动态属性等很有用。

考虑`StdClass`的一个简单方法是作为关联数组的替代。请看下面这个例子，它展示了`json_decode()`如何允许获取一个 StdClass 实例或一个关联数组。
在这个例子中也没有显示，`SoapClient::__soapCall`返回一个`StdClass`实例。

```
//Example with StdClass
$json = '{ "foo": "bar", "number": 42 }';
$stdInstance = json_decode($json);

echo $stdInstance - > foo.PHP_EOL; //"bar"
echo $stdInstance - > number.PHP_EOL; //42

//Example with associative array
$array = json_decode($json, true);

echo $array['foo'].PHP_EOL; //"bar"
echo $array['number'].PHP_EOL; //42 
```

🔗**来源:**【stackoverflow.com】T2

### Q7:PHP 中 die()和 exit()函数有什么区别？

> 题目: **PHP**
> 难度:⭐⭐

没有区别，它们是一样的。选择`die()`而不是`exit()`的唯一优势，可能是你可以节省时间多打一封信。

🔗**来源:**【stackoverflow.com】T2

### Q8:它们之间的主要区别是什么

> 题目: **PHP**
> 难度:⭐⭐

`const`和`define`的根本区别在于`const`在编译时定义常量，而`define`在运行时定义常量。

```
const FOO = 'BAR';
define('FOO', 'BAR');

// but
if (...) {
    const FOO = 'BAR';    // Invalid
}
if (...) {
    define('FOO', 'BAR'); // Valid
} 
```

同样在 PHP 5.3 之前，`const`无法在全局范围内使用。你只能在一个类中使用它。当您想要设置某种常量选项或与该类相关的设置时，应该使用这种方法。或者你想创建某种枚举。好的`const`用法的一个例子是去掉幻数。

`Define`可以用于同样的目的，但是只能在全局范围内使用。它应该只用于影响整个应用程序的全局设置。

除非您需要任何类型的条件或表达式定义，否则使用`consts`而不是`define()`——仅仅是为了可读性！

🔗**来源:**【stackoverflow.com】T2

### Q9:isset()和 array_key_exists()有什么区别？

> 题目: **PHP**
> 难度:⭐⭐

*   `array_key_exists`会告诉你一个键是否存在于一个数组中，当`$a`不存在时会报错。
*   如果键/变量存在**而不是`null`** ，`isset`将只返回`true`。当`$a`不存在的时候`isset`不会抱怨。

考虑:

```
$a = array('key1' => 'Foo Bar', 'key2' => null);

isset($a['key1']);             // true
array_key_exists('key1', $a);  // true

isset($a['key2']);             // false
array_key_exists('key2', $a);  // true 
```

🔗**来源:**【stackoverflow.com】T2

### Q10:var _ dump()和 print_r()有什么区别？

> 题目: **PHP**
> 难度:⭐⭐

*   `var_dump`函数显示变量/表达式的结构化信息，包括其**类型**和**值**。数组被递归地浏览，其中的值缩进以显示结构。它还显示哪些数组值和对象属性是引用。

*   `print_r()`以人类可读的方式显示变量的信息。数组值将以显示键和元素的格式呈现。类似的符号也用于对象。

考虑:

```
$obj = (object) array('qualitypoint', 'technologies', 'India'); 
```

`var_dump($obj)`将在屏幕中显示如下输出:

```
object(stdClass)#1 (3) {
 [0]=> string(12) "qualitypoint"
 [1]=> string(12) "technologies"
 [2]=> string(5) "India"
} 
```

并且，`print_r($obj)`将在屏幕中显示如下输出。

```
stdClass Object ( 
 [0] => qualitypoint
 [1] => technologies
 [2] => India
) 
```

🔗**来源:**【stackoverflow.com】T2

### Q11:解释不同的 PHP 错误是什么

> 题目: **PHP**
> 难度:⭐⭐

*   一个`notice`是一个非关键性的错误，表示在执行中出现了一些错误，比如一个未定义的变量。
*   当出现更严重的错误时，比如 include()命令检索不存在的文件，就会给出一个`warning`。在这两种情况下以及上述错误中，脚本将继续运行。
*   一个`fatal error`将终止代码。例如，未能满足 require()会产生这种类型的错误。

🔗**来源:**【pangara.com】T2

### Q12:如何在 PHP 中启用错误报告？

> 题目: **PHP**
> 难度:⭐⭐

检查 php.ini 中的“`display_errors`”是否等于“on”，或者在脚本中声明“`ini_set('display_errors', 1)`”。

然后，在代码中包含“`error_reporting(E_ALL)`”，以显示脚本执行期间的所有类型的错误消息。

🔗**来源:** [codementor.io](https://www.codementor.io/blog/php-interview-questions-sample-answers-du1080ext)

### Q13:用默认参数声明某个函数

> 题目: **PHP**
> 难度:⭐⭐

考虑:

```
function showMessage($hello = false){
  echo ($hello) ? 'hello' : 'bye';
} 
```

🔗**来源:** [codementor.io](https://www.codementor.io/blog/php-interview-questions-sample-answers-du1080ext)

### Q14:PHP 中支持多重继承吗？

> 题目: **PHP**
> 难度:⭐⭐

PHP 只支持单一继承；这意味着一个类可以使用关键字“extended”从一个单独的类扩展而来。

🔗**来源:**【guru99.com】T2

### Q15:PHP 中，对象是传值还是传引用？

> 题目: **PHP**
> 难度:⭐⭐

在 PHP 中，对象通过**值**传递。

🔗**来源:**【guru99.com】T2

### Q16:$ a 有什么区别！= $b 和$a！== $b？

> 题目: **PHP**
> 难度:⭐⭐

`!=`表示*不等式*(如果$a 不等于$b 则为真)`!==`表示*非同一性*(如果$a 不等于$b 则为真)。

🔗**来源:**【guru99.com】T2

### Q17:PHP 中的 PDO 是什么？

> 题目: **PHP**
> 难度:⭐⭐

**PDO** 代表 PHP 数据对象。

它是一组 PHP 扩展，提供了一个核心的 PDO 类和数据库，特定的驱动程序。它提供了一个独立于供应商的轻量级数据访问抽象层。因此，无论我们使用什么样的数据库，发出查询和获取数据的功能都是相同的。它侧重于数据访问抽象，而不是数据库抽象。

🔗**来源:**【github.com/Bootsity】T2

### Q18:解释一下我们在 PHP 中如何处理异常？

> 题目: **PHP**
> 难度:⭐⭐

当抛出异常时，语句后面的代码将不会被执行，PHP 将试图找到第一个匹配的 catch 块。如果一个异常没有被捕获，一个 PHP 致命错误将会以一个“未被捕获的异常”发出。PHP 可以抛出并捕获异常。

为了处理异常，代码可以放在一个`try`块中。
每次尝试必须至少有一个对应的`catch`块。可以使用多个 catch 块来捕获不同类别的异常。
异常可以在 catch 块中抛出(或再次抛出)。

考虑:

```
try {
    print "this is our try block n";
    throw new Exception();
} catch (Exception $e) {
    print "something went wrong, caught yah! n";
} finally {
    print "this part is always executed n";
} 
```

🔗**来源:**【github.com/Bootsity】T2

### Q19:区分回声和打印()

> 题目: **PHP**
> 难度:⭐⭐

`echo`和`print`差不多。它们都用于向屏幕输出数据。

不同之处在于:

*   echo 没有返回值，而 print 的返回值为 1，因此可以在表达式中使用。
*   echo 可以接受多个参数(尽管这种用法很少见)，而 print 可以接受一个参数。
*   echo 比 print 快。

🔗**来源:**【github.com/Bootsity】T2

### Q20:什么时候应该使用 require_once 与 require？

> 题目: **PHP**
> 难度:⭐⭐⭐

`require_once()`语句与`require()`相同，除了 PHP 会检查文件是否已经被包含，如果是，就不再包含(要求)它。

我的建议是 99.9%的时间都用`require_once`就好。

相反，使用`require`或`include`意味着你的代码在其他地方**不可重用**，也就是说，你引入的脚本实际上是在执行代码，而不是提供一个类或一些函数库。

🔗**来源:**【stackoverflow.com】T2

### Q21:检查 PHP 数组是否关联

> 题目: **PHP**
> 难度:⭐⭐⭐

考虑:

```
function has_string_keys(array $array) {
  return count(array_filter(array_keys($array), 'is_string')) > 0;
} 
```

如果至少有一个字符串键，`$array`将被视为一个*关联数组*。

🔗**来源:**【stackoverflow.com】T2

### Q22:如何将变量和数据从 PHP 传递到 JavaScript？

> 题目: **PHP**
> 难度:⭐⭐⭐

实际上有几种方法可以做到这一点:

*   使用 AJAX 从服务器获取所需的数据。想想 get-data.php:

```
echo json_encode(42); 
```

考虑 **index.html:**

```
<script>
    function reqListener () {
      console.log(this.responseText);
    }

    var oReq = new XMLHttpRequest(); // New request object
    oReq.onload = function() {
        // This is where you handle what to do with the response.
        // The actual data is found on this.responseText
        alert(this.responseText); // Will alert: 42
    };
    oReq.open("get", "get-data.php", true);
    //                               ^ Don't block the rest of the execution.
    //                                 Don't wait until the request finishes to
    //                                 continue.
    oReq.send();
</script> 
```

*   将数据回显到页面的某个地方，并使用 JavaScript 从 DOM 中获取信息。

```
<div id="dom-target" style="display: none;">
    <?php
        $output = "42"; // Again, do some operation, get the output.
        echo htmlspecialchars($output); /* You have to escape because the result
                                           will not be valid HTML otherwise. */
    ?>
</div>
<script>
    var div = document.getElementById("dom-target");
    var myData = div.textContent;
</script> 
```

*   将数据直接回显到 JavaScript。

```
<script>
    var data = <?php echo json_encode("42", JSON_HEX_TAG); ?>; // Don't forget the extra semicolon!
</script> 
```

🔗**来源:**【stackoverflow.com】T2

### Q23:有没有把一个 PHP 数组复制到另一个的函数？

> 题目: **PHP**
> 难度:⭐⭐⭐

在 PHP 中，数组是通过复制来赋值的，而对象是通过引用来赋值的，所以 PHP 默认会复制数组。PHP 中的引用必须是显式的:

```
$a = array(1,2);
$b = $a; // $b will be a different array
$c = &$a; // $c will be a reference to $a 
```

🔗**来源:**【stackoverflow.com】T2

### Q24:这段代码会返回什么？

> 题目: **PHP**
> 难度:⭐⭐⭐

考虑代码:

```
$a = new stdClass();
$a->foo = "bar";
$b = clone $a;
var_dump($a === $b); 
```

什么会回显到控制台？

* * *

具有等效成员的同一类的两个实例与`===`运算符不匹配。所以答案是:

```
bool(false) 
```

🔗**来源:**【stackoverflow.com】T2

### Q25:这段代码会返回什么？解释结果。

> 题目: **PHP**
> 难度:⭐⭐⭐

考虑代码。结果会返回什么？

```
$something = 0;
echo ('password123' == $something) ? 'true' : 'false'; 
```

* * *

答案是`true`。你不应该使用`==`进行字符串比较。即使你在比较字符串和字符串，PHP 也会隐式地将它们转换成浮点数，如果它们是数字，就进行数字比较。`===`还行。

例如

```
'1e3' == '1000' // true 
```

也返回 true。

🔗**来源:**【stackoverflow.com】T2

### Q26:array _ map、array_walk、array_filter 的区别到底是什么？

> 题目: **PHP**
> 难度:⭐⭐⭐

*   `array_walk`取一个数组和一个函数 F，并用 F(x)替换每个元素 x 来修改它。
*   `array_map`做了与**完全相同的事情，除了**之外，它将返回一个包含已转换元素的新数组，而不是原地修改。
*   `array_filter`用函数 F，而不是变换元素，将移除 F(x) **不为真的任何元素**

🔗**来源:**【stackoverflow.com】T2

### Q27:解释 exec() vs system() vs passthru()的区别？

> 题目: **PHP**
> 难度:⭐⭐⭐

*   `exec()`用于调用系统命令，或者自己处理输出。
*   `system()`用于执行一个系统命令并立即显示输出——大概是文本。
*   `passthru()`用于执行一个系统命令，您希望从该命令返回原始数据——大概是二进制数据。

🔗**来源:**【stackoverflow.com】T2

### Q28:你如何使用 PHP 创建一个单例类？

> 题目: **PHP**
> 难度:⭐⭐⭐

```
/**
 * Singleton class
 *
 */
final class UserFactory {
    /**
     * Call this method to get singleton
     *
     * @return UserFactory
     */
    public static
    function Instance() {
        static $inst = null;
        if ($inst === null) {
            $inst = new UserFactory();
        }
        return $inst;
    }

    /**
     * Private ctor so nobody else can instantiate it
     *
     */
    private
    function __construct() {

    }
} 
```

要使用:

```
$fact = UserFactory::Instance();
$fact2 = UserFactory::Instance(); 
```

但是:

```
$fact = new UserFactory() 
```

抛出一个错误。

🔗**来源:**【stackoverflow.com】T2

### Q29:PDO 的 query()和 execute()有什么区别？

> 题目: **PHP**
> 难度:⭐⭐⭐

*   `query`运行一个标准的 SQL 语句，并要求你对所有数据进行适当的转义，以避免 SQL 注入和其他问题。
*   `execute`运行一条预准备语句，允许您绑定参数，以避免转义或引用参数。如果多次重复一个查询，execute 的性能也会更好。

最佳实践是坚持使用准备好的语句并执行以提高安全性。除了它在客户端提供的转义，一个*准备好的语句在服务器端编译一次*，然后在每次执行时可以传递不同的参数。

🔗**来源:**【stackoverflow.com】T2

### Q30:Null Coalesce 运算符有什么用？

> 题目: **PHP**
> 难度:⭐⭐⭐

如果 Null 合并运算符存在且不为 NULL，则返回其第一个操作数。否则，它返回第二个操作数。

示例:

```
$name = $firstName ?? $username ?? $placeholder ?? "Guest"; 
```

🔗**来源:**【github.com/Bootsity】T2

### Q31:区分异常和错误

> 题目: **PHP**
> 难度:⭐⭐⭐

*   无法从`Error`中恢复。错误的唯一解决方案是终止执行。其中，您可以通过使用 try-catch 块或者将异常返回给调用者来从`Exception`中恢复。
*   您将无法使用 try-catch 块来处理`Errors`。即使您使用 try-catch 块处理它们，如果它们发生，您的应用程序也不会恢复。另一方面，`Exceptions`可以使用 try-catch 块来处理，如果它们发生，可以使程序流正常。
*   `Exceptions`与应用程序相关，而`Errors`与应用程序运行的环境相关。

🔗**来源:**【github.com/Bootsity】T2

### Q32:异常类函数有哪些？

> 题目: **PHP**
> 难度:⭐⭐⭐

从`Exception`类可以使用以下功能。

*   `getMessage()`—异常信息
*   `getCode()`—异常代码
*   `getFile()`—源文件名
*   `getLine()`—源线
*   `getTrace()`—`backtrace()`的 n 阵列
*   `getTraceAsString()`—格式化的跟踪字符串
*   `Exception::__toString`给出异常的字符串表示。

🔗**来源:**【github.com/Bootsity】T2

### Q33:区分参数化和非参数化函数

> 题目: **PHP**
> 难度:⭐⭐⭐

*   **非参数化函数**在调用时不带任何参数。
*   **参数化函数**在调用时接受一个或多个参数。当输出取决于运行时给定的动态值时，在程序运行时使用这些参数。有两种方法可以访问参数化函数:
    1.  *按值调用*:(这里我们直接传值)
    2.  *通过引用调用*:(这里我们传递存储值的地址位置)

🔗**来源:**【github.com/Bootsity】T2

### Q34:参照解释函数调用

> 题目: **PHP**
> 难度:⭐⭐⭐

在引用调用的情况下，如果在函数内部修改了实际值，则实际值也会被修改。在这种情况下，我们需要使用带有形式参数的符号`&`。`&`表示变量的引用。

示例:

```
function adder(&$str2) {  
    $str2 .= 'Call By Reference';  
}
$str = 'This is ';  
adder($str);  
echo $str; 
```

输出:

```
This is Call By Reference 
```

🔗**来源:**【github.com/Bootsity】T2

### Q35:我们为什么要用 extract()？

> 题目: **PHP**
> 难度:⭐⭐⭐

`extract()`函数将变量从数组导入局部符号表。
这个函数使用数组键作为变量名，使用值作为变量值。对于每个元素，它将在当前符号表中创建一个变量。
该函数返回成功提取的变量个数。

示例:

```
$a = "Original";
$my_array = array("a" => "Cat","b" => "Dog", "c" => "Horse");
extract($my_array);
echo "\$a = $a; \$b = $b; \$c = $c"; 
```

输出:

```
$a = Cat; $b = Dog; $c = Horse 
```

🔗**来源:**【github.com/Bootsity】T2

### Q36:解释 PHP 中什么是闭包，为什么要使用“use”标识符？

> 题目: **PHP**
> 难度:⭐⭐⭐⭐

考虑这个代码:

```
public function getTotal($tax)
{
    $total = 0.00;

    $callback =
        function ($quantity, $product) use ($tax, &$total)
        {
            $pricePerItem = constant(__CLASS__ . "::PRICE_" .
                strtoupper($product));
            $total += ($pricePerItem * $quantity) * ($tax + 1.0);
        };

    array_walk($this->products, $callback);
    return round($total, 2);
} 
```

你能解释为什么使用它吗？

* * *

这就是 PHP 如何表达一个**闭包**。基本上，这意味着您允许匿名函数“捕获”局部变量(在本例中，是`$tax`和对`$total`的引用)*在它的*范围之外，并将它们的值(或者在$total 的情况下，是对$total 本身的引用)保存为匿名函数本身的状态。

闭包是一个独立的名称空间，通常，你不能访问在这个名称空间之外定义的变量。

*   `use`允许你访问(使用)闭包内的后续变量。
*   `use`是早期绑定。这意味着变量值在定义闭包时被复制。所以在闭包内部修改$tax 没有外部影响，除非它是一个指针，就像对象一样。
*   你可以像在`&$total`的情况下一样将变量作为指针传入。这样，修改`$total`的值确实有外部影响，原始变量的值会改变。

🔗**来源:**【stackoverflow.com】T2

### Q37:PHP 中的后期静态绑定到底是什么？

> 题目: **PHP**
> 难度:⭐⭐⭐⭐

基本上，它归结为一个事实，即`self`关键字没有遵循相同的继承规则。`self`总是解析到使用它的类。这意味着，如果你在父类中创建一个方法，并从子类中调用它，`self`不会像你预期的那样引用子类。

后期静态绑定引入了关键字`static`的新用法，解决了这个特殊的缺点。当你使用`static`时，它代表你第一次使用它的类，即。它“绑定”到运行时类。

考虑:

```
class Car {
    public static
    function run() {
        return static::getName();
    }

    private static
    function getName() {
        return 'Car';
    }
}

class Toyota extends Car {
    public static
    function getName() {
        return 'Toyota';
    }
}

echo Car::run(); // Output: Car
echo Toyota::run(); // Output: Toyota 
```

🔗**来源:**【stackoverflow.com】T2

### Q38:如何测量 PHP 脚本的执行次数？

> 题目: **PHP**
> 难度:⭐⭐⭐⭐

我想知道 PHP while-loop 执行需要多少毫秒。能帮帮忙吗？

* * *

为此，您可以使用`microtime`功能。

考虑:

```
$start = microtime(true);
while (...) {

}
$time_elapsed_secs = microtime(true) - $start; 
```

🔗**来源:**【stackoverflow.com】T2

### Q39:合并两个 PHP 对象的最好方法是什么？

> 题目: **PHP**
> 难度:⭐⭐⭐⭐

```
//We have this:
$objectA->a;
$objectA->b;
$objectB->c;
$objectB->d;

//We want the easiest way to get:
$objectC->a;
$objectC->b;
$objectC->c;
$objectC->d; 
```

* * *

此作品:

```
$obj_merged = (object) array_merge((array) $obj1, (array) $obj2); 
```

你也可以使用`array_merge_recursive`来进行*深度复制*行为。

还有一种方法是:

```
foreach($objectA as $k => $v) $objectB->$k = $v; 
```

这比 PHP 版本中的第一个答案要快。

🔗**来源:**【stackoverflow.com】T2

### Q40:比较 mysqli 或 pros 利弊如何？

> 题目: **PHP**
> 难度:⭐⭐⭐⭐

让我们列举一些:

*   PDO 是标准，这是大多数开发者希望使用的。

*   将应用程序从一个数据库移动到另一个数据库并不常见，但是迟早您会发现自己正在使用不同的 RDBMS 进行另一个项目。如果你在家和 PDO 在一起，那么在那一点上至少会少学一样东西。

*   PDO 的一个非常好的地方是你可以获取数据，并自动注入到一个对象中。

*   PDO 有一些有助于对抗 SQL 注入的特征

*   就执行速度而言，MySQLi 胜出，但是除非你有一个使用 MySQLi 的好的包装器，否则它处理预准备语句的功能很糟糕。inserts——几乎相等，select——MySQL 对于非预处理语句快 2.5%，对于预处理语句快 6.7%。

🔗**来源:**【stackoverflow.com】T2

### Q41:飞船操作员有什么用？

> 题目: **PHP**
> 难度:⭐⭐⭐⭐

该`<=>`运算符将提供组合比较，因为它将:

*   如果两边的值*相等*则返回 0
*   如果左侧*上的值大于*，则返回 1
*   如果右侧*上的值大于*，则返回-1

考虑:

```
//Comparing Integers
echo 1 <= > 1; //outputs 0
echo 3 <= > 4; //outputs -1
echo 4 <= > 3; //outputs 1

//String Comparison

echo "x" <= > "x"; // 0
echo "x" <= > "y"; //-1
echo "y" <= > "x"; //1 
```

🔗**来源:**【github.com/Bootsity】T2

### Q42:PHP 有线程吗？

> 题目: **PHP**
> 难度:⭐⭐⭐⭐

标准 php 不提供任何多线程，但是有一个(实验性的)扩展确实提供了多线程- `pthreads`。下一个最好的方法是通过 CLI 让一个脚本执行另一个脚本，但这有点初级。根据你要做的事情和它的复杂程度，这可能是也可能不是一个选项。

🔗**来源:**【github.com/Bootsity】T2

### Q43:PHP 是单线程还是多线程？

> 题目: **PHP**
> 难度:⭐⭐⭐⭐

PHP 本质上不是单线程的。然而，事实是，unix 系统上最常见的 PHP 安装是单线程设置，最常见的 Apache 安装也是如此，nginx 没有任何基于线程的架构。在最常见的 Windows 设置和一些更高级的 unix 设置中，PHP 可以在一个进程中操作多个解释器线程。

PHP 作为一个解释器，从 2000 年开始支持多线程。

🔗**来源:**【github.com/Bootsity】T2

### Q44:提供一些在 PHP 中模仿多个构造函数的方法

> 题目: **PHP**
> 难度:⭐⭐⭐⭐⭐

众所周知，你不能在一个 PHP 类中放两个带有唯一参数签名的 __construct 函数，但是我想这样做:

```
class Student 
{
   protected $id;
   protected $name;
   // etc.

   public function __construct($id){
       $this->id = $id;
      // other members are still uninitialised
   }

   public function __construct($row_from_database){
       $this->id = $row_from_database->id;
       $this->name = $row_from_database->name;
       // etc.
   }
} 
```

在 PHP 中实现这一点的最好方法是什么？

* * *

我可能会这样做:

```
class Student
{
    public function __construct() {
        // allocate your stuff
    }

    public static function withID( $id ) {
        $instance = new self();
        $instance->loadByID( $id );
        return $instance;
    }

    public static function withRow( array $row ) {
        $instance = new self();
        $instance->fill( $row );
        return $instance;
    }

    protected function loadByID( $id ) {
        // do query
        $row = my_awesome_db_access_stuff( $id );
        $this->fill( $row );
    }

    protected function fill( array $row ) {
        // fill all properties from array
    }
} 
```

然后如果我想要一个我知道 ID 的学生:

```
$student = Student::withID( $id ); 
```

从技术上来说，你不是在构建多个构造函数，只是静态的帮助器方法，但是你可以通过这种方式避免在构造函数中出现大量杂乱的代码。

另一种方式是使用**工厂和流畅风格的组合** :

```
class Student
{
    protected $firstName;
    protected $lastName;
    // etc.

    /**
     * Constructor
     */
    public function __construct() {
        // allocate your stuff
    }

    /**
     * Static constructor / factory
     */
    public static function create() {
        $instance = new self();
        return $instance;
    }

    /**
     * FirstName setter - fluent style
     */
    public function setFirstName( $firstName) {
        $this->firstName = $firstName;
        return $this;
    }

    /**
     * LastName setter - fluent style
     */
    public function setLastName( $lastName) {
        $this->lastName = $lastName;
        return $this;
    }
}

// create instance
$student= Student::create()->setFirstName("John")->setLastName("Doe"); 
```

🔗**来源:**【stackoverflow.com】T2

### Q45:如何在 PHP 中实现方法重载？

> 题目: **PHP**
> 难度:⭐⭐⭐⭐⭐

你不能重载 PHP 函数。函数签名仅基于它们的名称，不包括参数列表，因此不能有两个同名的函数。

然而，您可以声明一个接受可变数量参数的**变量函数**。您可以使用`func_num_args()`和`func_get_arg()`来传递参数，并正常使用它们。

考虑:

```
function myFunc() {
    for ($i = 0; $i < func_num_args(); $i++) {
        printf("Argument %d: %s\n", $i, func_get_arg($i));
    }
}

/*
Argument 0: a
Argument 1: 2
Argument 2: 3.5
*/
myFunc('a', 2, 3.5); 
```

🔗**来源:**【github.com/Bootsity】T2

> 谢谢🙌阅读，祝你面试好运！
> *如果你喜欢这篇文章，请分享给你的开发者伙伴！*
> *查看更多全栈面试问题&答案上👉[www . full stack . cafe](https://www.fullstack.cafe)T9】*