# Shell编程

vim helloworld.sh

## 1.1 Shell名词解释

- Kernel

  - linux内核主要是为了和硬件打交道

- shell

  - 命令解释器(command interpreter)
  - shell是一个用C语言编写的程序，它是使用Linux的桥梁，shell即是一种命令语言，又是一种程序设计语言
  - shell是指一种应用程序，这个应用程序提供了一个界面，用户通过这个界面访问操作系统内核的服务

- shell两大主流

  - sh
  - csh

- #! 声明

  - 告诉系统其后路径所指定的程序即是解释此脚本文件的shell程序
  - #!/bin/bash

  ​           echo 'Hello world'

## 1.2 shell脚本的执行

 



变量



运算符



逻辑语句  逻辑，顺序，循环



方法-函数       将实现某一功能的代码封装到一起



世界观



应用



框架



中间件    解决框架不能解决的问题



整个语言的学习流程就是这样的





## shell运算符

- for 当变量值在表里，for循环即执行一次所有命令，使用变量名获取列表中的当前取值

- 命令可为任何有效的shell命令和语句，In列表可以包含替换、字符串和文件名

- in列表是可选的，如果不用它，for循环使用命令行的位置参数

- ```shell
  for var in item1 item2 ....itemN
  do
    command1
    command2
    command3
  done
  ```

- ```shell
  for loop in 1 2 3 4 5
  do
    echo "The value is : $loop"
  done
  ```



### 3.4.4 while循环

- while循环用于不断执行一系列命令，也用于从输入文件中读取数据；命令通常为测试条件

- ```shell
  while condition
  do
    command
  done
  ```

  

## 3.5 shell函数

- linux shell可以用户定义函数，然后在shell脚本中可以随便调用

- 可以带function fun()定义，也可以直接fun()定义，不带任何参数

- 参数返回，可以显示加：return返回，如果不加，将以最后一条命令运行结果，作为返回值。return后跟数值n(0-255)

- #！/bin/bash

- ```shell
  #! /bin/bash
  domoFun(){
   echo "这是我的第一个shell函数"
  }
  
  echo "----函数开始执行---"
  domoFun
  echo "----函数执行结束---"
  echo 'fdsfasdfsadf'
  ```

- ```shell
  #! /bin/bash
  funWithReturn(){
   echo "这个函数对输入的两个数字进行相加运算"
   echo "输入第一个数字"
   read aNum
   echo "输入第二个数字"
   read anotherNum
   echo "两个数字分别是 $aNum 和 $anotherNum!"
   return $(($aNum + $anotherNum))
  }
  
  funWithReturn
  echo "输入的两个数字之和为 $?"
  
  
  ```

-  



## 4

分时日月周     * * * * *











