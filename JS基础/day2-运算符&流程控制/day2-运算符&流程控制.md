小索引：

[TOC]

## 1	交换两个变量的值

```js
		//第一种方法：设置第三个变量
		var num1 = 'abc', num2 = 200;
        // 如何交换两个变量的值？设置一个用来中转的变量即可
        var temp = num1;
        num1 = num2;
        num2 = temp;
        console.log(num1, num2);
		
		//第二种方法，不允许设置第三个变量
		<script>
        	var a = 20,b = 30;
        	a = a+b;
        	b = a - b;
        	a = a - b;
        	console.log('a是'+a+'，b是'+b);   
    	</script>
```

## 2	运算符（操作符）

### 算数运算符

> +- \* / %   基本使用自己体会

- js中的小数计算精度问题
  - 避免方式：将小数通过计算变为整数，再进行加减等计算操作。

### 一元运算符

> 概念：一元指的是参与运算的操作数只有一个。

- 以前我们使用过哪些一元运算符： 正+负-号， typeof 

#### 自增自减运算：

- ++ 让变量的值自增1（自身的值+1）
  - 基本使用方式（单独使用）
  - 结合其他操作一起使用
    - 当++前置于操作数时，当前位置取自增后的值
    - 当++后置于操作数时，当前位置取原值
- -- 让变量的值自减1（自身的值-1）

```js
 <script>
        // ++ 让变量的值自增1

        // 1 单独使用时，前置与后置的功能相同，都是自增1
        /* var num1 = 100;
        num1++;
        console.log(num1); // 101

        var num2 = 100;
        ++num2;
        console.log(num2); // 101 */
    
        // 2 与其他运算结合的使用方式(了解)
        //  - 当++前置于操作数时，当前位置取自增后的值
        //  - 当++后置于操作数时，当前位置取原值

        /* var num1 = 100;
        console.log( num1++ + num1++ + num1++ ); // 303
        console.log(num1); // 103 */

        /* var num2 = 100;
        console.log( ++num2 + ++num2 + ++num2 ); // 306
        console.log(num2); // 103 */

        var num3 = 100;
        console.log( ++num3 + num3++ + num3++ + ++num3); // 408
        console.log(num3); // 104

    
    </script>
```



### 比较运算符

> 所有比较运算符都返回布尔类型值

- 普通比较运算符
  - \> < >= <= 
- 相等运算符
  - == === != !==
    - == 只比较值，不比较类型，会发生隐式转换
    - === 既比较值又比较类型，比较更为严谨 （推荐使用的方式）
  - 特殊的比较规则：
    - null == undefined   返回true
    - NaN和任意数据正向比较均为 false
      - isNaN(数据)   非数值返回true，  数值返回false

```js
 <script>
        // 基本比较运算符的操作：
        /* console.log( 3 > 8 ); // false
        console.log( 11 < 22 ); // true
        console.log( 5 >= 2); // true
        console.log( 7 <= 2 ); // false
        console.log( 2 <= 2 ); // true */
        
        // 相等运算符：
        //  == 相等比较 (不推荐使用，不严谨)
        //   - 只比较值，不比较类型（因为会发生隐式转换）
        // console.log( 100 == '100' ); // true

        // != 不相等
        /* console.log( 100 != 100 ); // false
        console.log( 100 != '100' ); // false */


        //  === 全等比较 (推荐的使用方式)
        //   - 既比较值 又比较类型
        /* console.log( 100 === '100' ); // false
        console.log( 100 === 100 ); // true
        console.log( '100' === '100' ); // true */

        // !== 不全等        
        /* console.log( 100 !== 100 ); // false
        console.log( 100 !== '100' ); // true */


        // 特殊的比较规则：(记忆)
        //  - null和undefined相等
        // console.log( null == undefined ); // true

        //  - NaN和任意数据进行正向比较都返回false
        /* console.log( NaN == NaN ); // false
        console.log( NaN === NaN ); // false

        console.log( NaN != NaN ); // true
        console.log( NaN !== NaN ); // true */

        // js中提供了一个功能用来检测NaN
        //   - isNaN(数据);
        //     - 数据为非数值，返回true，如果是数值返回false
        console.log( isNaN(NaN) ); // true
        console.log( isNaN('abc') ); // true
        console.log( isNaN('100') ); // false
        console.log( isNaN(200) ); // false
        
    </script>
```



### 逻辑运算符（略难）

- 逻辑与(逻辑且)  && 

- 逻辑或 ||

- 逻辑非 !

- 基本使用方式：

  - 所有的操作数均为布尔类型
    - 逻辑与
      - 格式：  操作数1 && 操作数2
      - 规则：两个操作数均为true，结果为true，任意一个为false，结果为false
    - 逻辑或
      - 格式：  操作数1 || 操作数2
      - 规则：两个操作数均为false，结果为false，任意一个为true，结果为true
    - 逻辑非
      - 格式：  !操作数1
      - 规则：取反，操作数为true，结果为false，操作数为false，结果为true

- 其他使用方式：

  - 任意操作数为非布尔类型（逻辑与和逻辑或的规则）

    1 从左往右查看
    2 如果操作数1位非布尔类型，会隐式转换
    3 当前操作数1如果能决定式子的结果，返回操作数1的**原值**

    ```
    - 返回的一定是操作数的原值，转换的目的只是为了判断而已。
    ```

      4 如果操作数1决定不了结果，返回操作数2的**原值**

    - 逻辑非：
      - 规则：隐式转换后取反，返回的是布尔值

```js
<script>
        // 逻辑与 &&
        /* console.log( true && true ); // true
        console.log( true && false ); // false
        console.log( false && true ); // false
        console.log( false && false ); // false */
        
        // 逻辑或 ||
        /* console.log( false || false ); // false
        console.log( true || true ); // true
        console.log( true || false ); // true
        console.log( false || true ); // true */
        
        // 逻辑非 !
        /* console.log( !false ); // true
        console.log( !true ); // false */

        // 其他使用方式演示：(逻辑与和逻辑或规则相同)
        //  1 从左往右查看
        //  2 如果操作数1位非布尔类型，会隐式转换
        //  3 当前操作数1如果能决定式子的结果，返回操作数1的原值
        //      - 返回的一定是操作数的原值，转换的目的只是为了判断而已。
        //  4 如果操作数1决定不了结果，返回操作数2的原值

        // console.log( undefined && 'abc' ); // undefined
        // console.log( 'hehehe' && 'abc' ); // 'abc'

        /* console.log( 0 && 200 ); // 0
        console.log( 200 && 0 ); // 0 */

        /* console.log( 200 || 0 ); // 200
        console.log( undefined || 'abc' ); // 'abc'
        console.log( undefined || true ); // true */

        // 逻辑非：
        /* console.log( !'abc' ); // false
        console.log( !undefined ); // true */

    </script>
```



### 三元运算符

> 三元运算符：指的是参与运算的操作数有3个

- 格式：  条件操作数 ?  操作数1 ： 操作数2;
- 规则：
  - 条件最终需要一个布尔类型值，根据布尔的结果，如果为true，执行操作数1，如果为false，执行操作数2
  - 根据条件结果，选择某个操作数作为结果返回

```javascript
		// 1 根据条件的结果执行某个操作：
        // 11 > 22 ? alert('第一个数大') : alert('第二个数大');
        // false ? alert('第一个数大') : alert('第二个数大');
        // '' ? alert('第一个数大') : alert('第二个数大');
        
        // 2 根据条件，选择某个操作数作为结果返回
        var result = 11 > 22 ? 11 : 22;
        console.log(result); // 22
```

### 赋值运算符

- = 普通的赋值运算
- += -= *= /= %=
  - 这些操作就是简化数据的+-*/%

### 运算符的优先级

> 运算符的优先级操作时不需要太过考虑，实际操作中不会在一段代码里书写多类的运算符

- 优先级从高到低为：
  - () 括号：用来提高运算的优先级
  - 一元运算符：正+负-号，typeof  ++ --  !
  - 算数运算符：先*/% 后+-
  - 比较运算符： > < >= <= == === != !==
  - 逻辑运算符：先&& 后|| 
  - 三元运算符
  - 赋值运算符

## 3	程序的流程控制

- 顺序结构：程序的默认结构，特点是从上往下一行一行执行
- 分支结构：根据不同的情况执行不同的操作
- 循环结构：可以让代码重复执行，简化操作

### 分支结构(选择结构)

#### if语句

- 语法形式：

```javascript
// 单分支结构(单if结构)
if (条件) { // 条件最终需要一个布尔类型值，如果条件为true，执行后续操作，false时忽略
	// {}的范围称为代码块：用来标识哪些代码属于if的操作范围
}

// 双分支结构(if..else结构)
if (条件) {
    // 条件为true，执行当前代码块
} else {
    // 条件为false，执行当前代码块
}

// 多分支（if..else if..else if..else）
//	- 规则：
//		if和elseif后都具有条件, 哪个条件满足就执行后面的对应代码块，执行完毕结束
//		else结构可以省略
if (条件1) {
    // 代码块1:
} else if (条件2) {
    // 代码块2：
} else if (条件3) {
    // 代码块3：
} else if (条件4) {
    // 代码块4：
} else {
    // else的代码块
}
```

#### switch语句

- 语法结构

```javascript
规则:
	将switch后的数据与每个case后的值依次进行 全等 比较，如果结果为true，执行后续代码
    每个case后都要设置break，执行break会结束switch操作
    如果每个case比较都失败了，最终执行default中的代码
switch (数据) {
	case 值1：
        // 代码区域1
        break;
    case 值2：
        // 代码区域2
        break;
    case 值3：
        // 代码区域3
        break;
    default:
        // default的代码区域
        break;
}
```

```js
<script>
        // 常规使用方式：
        // 例如：根据性别判断可以上什么厕所
        /* var myGender = '男';
        
        switch (myGender) {
            case '男':
                alert('请上男厕所');
                break;
            case '女':
                alert('请上女厕所');
                break;
            default:
                alert('不知道，也不敢问，自己解决吧!~');
                break;
        } */

        // 其他用法：通过switch进行值的范围检测(使用较少)
        //    - 如果进行范围检测，case后书写了条件，需要将switch后设置为true
        var myAge = 83;
        switch (true) {
            case myAge < 18:
                alert('欢快的去上学吧，哈哈哈');
                break;
            case myAge < 60:
                alert('跳广场舞，和相亲');
                break;
            default:
                alert('爱咋咋地');
                break;
        }    
    </script>
```



#### if和switch小结

- 两个语法的适用场景：

  - if语句适用于范围的检测
  - switch语句适用于单个值的检测(因为默认是全等的比较规则，严谨)

  上面只是推荐，实际操作时适用哪种更加取决于个人习惯。 

### for循环

- 语法形式：

```javascript
for (循环变量声明;循环条件;循环变量增减) {
    // 循环体：指的是循环的主体代码
}
```

```js
<script>
        // 1 基本使用：    
        /*
            for (循环变量声明;循环条件;循环变量增减) {
                // 循环体：指的是循环的主体代码
            }
        */
        
        // 通过观察发现，循环语句，可以让我们的重复代码书写更加简便
        /* for (var i = 0; i < 10; i++) {
            console.log('嘿嘿嘿');
        } */
        
        // 2 for循环每部分的执行顺序
        /*
            for (1循环变量声明;2循环条件;3循环变量增减) {
                // 4循环体：指的是循环的主体代码
            }

            - 首先执行步骤1：声明循环变量
            - 再执行步骤2：检测循环条件
            - 再执行步骤4：循环体代码
            - 再执行步骤3:循环变量增减
            - 接下来重复执行步骤243、243..直到结束为止
        */

        // 3 断点调试工具
        //  - 为了能够清晰的查看程序执行的细节，可以借助浏览器提供了断点调试工具
    </script>
```



- for循环的执行顺序
  - 首先执行步骤1：声明循环变量
  - 再执行步骤2：检测循环条件
  - 再执行步骤4：循环体代码
  - 再执行步骤3:循环变量增减
  - 接下来重复执行步骤243、243..直到结束为止
- 断点调试工具的使用步骤：
  - 写好代码后，在浏览器中运行
  - 点击F12，找到Sources面板
  - 从左侧列表中找到要调试的文件，中间区域会进行展示
  - 在找到要调试的代码，点击行号(点那个数)，就会生成一个断点
  - 刷新页面，程序会自动在断点位置暂停
  - 可以点击F10对应的按键，让程序一步一步执行(步进)
  - 还可以在右侧的Watch面板中监视某些变量，顺便看看for循环的执行顺序即可
  - 断点使用完毕，清除即可（再点击对应行号即可）

### 小练习集合

```js
<!-- <script>
        var name = prompt("姓名",name);
        var age = prompt("年龄",age);
        var gentle = prompt("性别",age);

        alert('姓名：'+name+'\n'+'年龄：'+age+'\n'+'性别：'+gentle);
        // prompt("姓名：");
    </script> -->
    <!-- <script>
            var num1 = prompt("数值1",num1);
            var num2 = prompt("数值2",num2);
            // var gentle = prompt("性别",age);
            var sum = Number(num1)+Number(num2);
            alert('num1+num2='+ sum);
            // prompt("姓名：");
        </script> -->
    <!-- <script>
        var res = Boolean(null);
        console.log(res); // 输出true
        console.log(typeof res); // 输出 boolean
    </script> -->
    <script>
        //求两个数最大值
        // var num1 =96,num2 = 36;
        // if (num1>num2) {
        //     alert(num1+'>'+num2);
        // } else {
        //     alert(num2+'>'+num1);
        // }




        //求三个数最大值
        // var a = Number(prompt('请填入a的值：',a));
        // var b = Number(prompt('请填入b的值：',b));
        // var c = Number(prompt('请填入c的值：',c));
        // if (a>=b) {
        //     if(a<=c){
        //         alert('最大值是c，值为：'+c+'\n其中a的值为'+a+'，b的值为'+b+'，c的值为'+c);
        //     }else if(a>c){
        //         alert('最大值是a，值为：'+a+'\n其中a的值为'+a+'，b的值为'+b+'，c的值为'+c);
        //     }
        // } else if(a<b){
        //     if(b<=c){
        //         alert('最大值是c，值为：'+c+'\n其中a的值为'+a+'，b的值为'+b+'，c的值为'+c);
        //     }else if(b>c){
        //         alert('最大值是b，值为：'+b+'\n其中a的值为'+a+'，b的值为'+b+'，c的值为'+c);
        //     }
        // }


        // ==
        // var x = '36';
        // var z = 36;
        // if( x == z){
        //     console.log('true');
        // }else{
        //     console.log('fasle');
        // }







            // 及格
            // var score = Number(prompt('请输入你的成绩:'));
            // if (score<60) {
            //     alert('你不及格！');
            // } else if(score>=60 && score <= 79){
            //     alert('刚及格！');
                
            // }else if(score>=80 && score <= 90){
            //     alert('良好');
                
            // }else if(score>90 && score <= 100){
            //     alert('秀儿就是你！');
                
            // }else{
            //     alert('输入正常点~');
            // }

















        // var d = prompt('今天周几？', d);
        // switch (d) {
        //     case '周一':
        //         alert('今天是周一！该去玩吃鸡了！');
        //         break;
        //     case '周二':
        //         alert('今天是周二！该去玩cf了！');
        //         break;
        //     case '周三':
        //         alert('今天是周三！该去玩cf了！');
        //         break;
        //     case '周四':
        //         alert('今天是周四！该去玩吃鸡了！');
        //         break;
        //     case '周五':
        //         alert('今天是周五！该去玩吃鸡了！');
        //         break;
        //     case '周六':
        //         alert('今天是周六！该去玩吃鸡了！');
        //         break;
        //     case '周日':
        //         alert('今天是周日！该去玩cf和吃鸡了！');
        //         break;
        //     default:
        //         alert('输入错误！！！');
        //         break;
        // }

















            //一到一百偶数和
            // var sum =0;
            // for (let i = 0; i <=100; i++) {
            //    if(i%2==0){
            //     sum =sum+i;
            //    }
                
            // }
            // alert('sum的值为：'+sum);


            






    //九九乘法表
    //三角形
    for(var i = 1;i<=9;i++){
        for(var x = 1;x <= i;x++){
            document.write('*');
        }
        document.write('<div></div>');
       
    }            


    //九九乘法表
    document.write('<table border = "1" style = "padding:20px 16px;">');
    for(var i = 1;i<=9;i++){
        document.write('<tr>');
        for(var x = 1;x <= i;x++){
            document.write('<td>');
            document.write(x+'*'+i+'='+x*i+'       ');
            document.write('</td>');
        }
        document.write('</tr>');
       
    }   
    document.write('</table>');
    </script>
```

