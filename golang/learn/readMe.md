「说明」:这里是一个练习基础语法的文件夹，后面在提取出去。



```
按照类型来分：
			基本类型：int，float，string，bool
			复合类型：array，slice，map，struct，pointer，function，chan

按照特点来分：
			值类型：int，float，string，bool，array
				传递的是数据副本
			引用类型：Slice
				传递的地址,多个变量指向了同一块内存地址，

所以：切片是引用类型的数据，存储了底层数组的引用

```



```
defer的词义："延迟","推迟"
在go语言中，使用defer关键字来延迟一个函数或者方法的执行。

			1.defer函数或方法：一个函数或方法的执行被延迟了。

			2.defer的用法：
				A：对象.close(),临时文件的删除。。。
						文件.open()
						defer close()
						读或写

				B：go语言中关于异常的处理，使用panic()和recover()
					panic函数用于引发恐慌，导致程序中断执行
					recover函数用于恢复程序的执行，recover()语法上要求必须在defer中执行。


			3.如果多个defer函数:先延迟的后执行，后延迟的先执行。

			4.defer函数传递参数的时候：defer函数调用时，就已经传递了参数数据了，只是暂时不执行函数中的代码而已。

			5.defer函数注意点：
				defer函数：
		当外围函数中的语句正常执行完毕时，只有其中所有的延迟函数都执行完毕，外围函数才会真正的结束执行。
		当执行外围函数中的return语句时，只有其中所有的延迟函数都执行完毕后，外围函数才会真正返回。
		当外围函数中的代码引发运行恐慌时，只有其中所有的延迟函数都执行完毕后，该运行时恐慌才会真正被扩展至调用函数。
```



```
panic：词义"恐慌"，
		recover："恢复"
		go语言利用panic()，recover()，实现程序中的极特殊的异常的处理
			panic(),让当前的程序进入恐慌，中断程序的执行
			recover(),让程序恢复，必须在defer函数中执行
			
defer func() {
   if r := recover(); r != nil {
      if er, ok := r.(error); ok {
         err = er
      } else {
         err = errors.New("")
         fmt.Println("未知错误: ")
         fmt.Println(r)
      }
   }
}()
```
