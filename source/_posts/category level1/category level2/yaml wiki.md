#基本语法
YAML 使用键值对的形式记录信息，标准格式是

key: value
键: 值
#基本规则
大小写敏感
使用缩进表示层级关系
禁止使用 tab 缩进，只能使用空格键
缩进长度没有限制，只要元素对齐就表示这些元素属于一个层级
使用 # 表示注释
字符串可以不用引号标注（但是建议你最好还是加上引号）


三种数据结构
- scalar 纯量
scalar 不可再分割的量，这个你无需了解，因为了解了也没什么卵用。

- map 散列表
键值对的集合，只要是出于同于缩进级别下的键值对，都可以称为一个 map

map 有两种写法，最简单，也是最常用的就是前面的那种写法，如

hexo-tag-dplayer:
  cdn: value
  default: value
等价于

{hexo-tag-dplayer: {cdn: value, default: value}}
#或者是
hexo-tag-dplayer: {cdn: value, default: value}


- list 数组
划重点，这是本篇文章最有用的一节

list 的表示形式同样有两种

key:
  - value1
  - value2
或者

key: [value1, value2]
map 和 list 可以相互嵌套使用