OVS对象型视图服务数据库模型系统
=

OVS DB MODEL 对象型视图服务数据库模型系统

背景
==
**O对应编程语义中的Object 表示应用表示数据等对象，一般情况下采用JSON格式**
**V对应View 作用于Object的规则**
**S对应Server 表示具体的服务，协议等**
***
* 在OVS模式中传统数据库模型中的表中记录，大字段，大对象等数据与OVS中的Object对应
* 而OVS中的Object与面向对象编程界内的对象语义相似
* 其中Object从广义上面表示，传统数据库中的数据。
* V与传统数据库中的建立在数据模型上面的表，视图，函数，存储过程类似。
* 在OVS系统中View 是全局唯一的，且不同的View之间可以通过继承复用。
* 在OVS系统中V主要作用与O之上，使Object通过View的规则作用产生，新的Object，新的
* Object与原来的Object之间存在继承关系。

**V规则对O对象进行抽取产生新的O2对象**

例如原O的对象有

>O={“姓名”:”张三”,”年龄”:27,”住址” : { “城市” : “上海”  , ”街道” : “南京路” }}

V规则抽取O对象中所有的姓名和年龄的集合形成新的O对象

>new O ={“姓名”:”张三”,”年龄”:27,”住址” }

**表达式：集合O1通过规则V1的作用生成O2**

* 旧的O对象与新的O2对象可以存在继承的关系。
* 在新的O2对象中出现的字段若来自旧的O对象中，可以说改字段继承来自O对象。

**而在O2对象中来自O对象的字段可以采用两种方式**
* 引用
>O2对象中的字段引用O对象中的字段，当O对象该字段被更新的时候，O2对象中引用的该字
段同时也被更新。当O对象中被引用的字段被删除是，O中引用的字段状态将被置为对空对象
的引用，可以修改View来改变修改引用规则。

* 克隆
>O2对象中的字段克隆了O对象中的字段，在O2对象中的字段与O对象中的字段无关。


***
**V规则作用于多个O对象，生成一个新的O对象**

通过View规则将多个O对象合并成一个新的对

例如
>O1={“姓名”:”张三”,”年龄”:27}

>O2={“姓名”:”张三”,”性別”:"男"}

>O3={ “城市” : “上海”  , ”街道” : “南京路” }

V規則將O1對象和O2對象合併，且將O2集成到新的對象中

>O={“姓名”:”张三”,”年龄”:27,“性別”:“男”,”住址” : { “城市” : “上海”  , ”街道”
: “南京路” }}

**表达式：集合O1,O2,O3通过规则V1的作用生成集合O**


***
* 兩個對象間可以通過進行交，併，差等集合運算


