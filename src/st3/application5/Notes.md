# 3.5 应用
## 1. 符号表的选择
    各种符号表实现的渐进性能的总结

<table>
    <tr>
        <th rowspan="2">算法（数据结构）</th>
        <th colspan="2">最坏情况下的运行时间的增<br>长数量级（N次插入之后）</th>
        <th colspan="2">平均情况下的运行时间的增<br>长数量级（N次插入之后）</th>
        <th rowspan="2">关键接口</th>
        <th rowspan="2">内存使用（字节）</th>
    </tr>
    <tr>
        <th>查找</th>
        <th>插入</th> 
        <th>查找命中</th>
        <th>插入</th>        
    </tr>
    <tr>
        <td>顺序查询（无序链表）</td>
        <td align="center">N</td>
        <td align="center">N</td>
        <td align="center">N/2</td>
        <td align="center">N</td>
        <td>equals()</td>
        <td>48N</td>
    </tr>
    <tr>
        <td>二分查找（有序数组）</td>
        <td align="center">lgN</td>
        <td align="center">N</td>
        <td align="center">lgN</td>
        <td align="center">N/2</td>
        <td>compareTo()</td>
        <td>16N</td>
    </tr>
    <tr>
        <td>二叉树查找（二叉查找树）</td>
        <td align="center">N</td>
        <td align="center">N</td>
        <td align="center">1.39lgN</td>
        <td align="center">1.39lgN</td>
        <td>compareTo()</td>
        <td>64N</td>
    </tr>
    <tr>
        <td>2-3树查找（红黑树）</td>
        <td align="center">2lgN</td>
        <td align="center">2lgN</td>
        <td align="center">1.00lgN</td>
        <td align="center">1.00lgN</td>
        <td>compareTo()</td>
        <td>64N</td>
    </tr>
    <tr>
        <td>拉链法（链表数组）</td>
        <td align="center">&lt;lgN</td>
        <td align="center">&lt;lgN</td>
        <td align="center">N/(2M)</td>
        <td align="center">N/M</td>
        <td>equals()<br>hashCode()</td>
        <td>48N+64M</td>
    </tr>
    <tr>
        <td>线性探测法（并行数组）</td>
        <td align="center">clgN</td>
        <td align="center">clgN</td>
        <td align="center">&lt;1.5</td>
        <td align="center">&lt;2.5</td>
        <td>equals()<br>hashCode()</td>
        <td>在32N和128N之间</td>
    </tr>
</table>
    对于典型的应用程序，应该在散列表和二叉查找树之间进行选择。
    第一选择是散列表，在其他因素更重要时才会选择红黑树。
    
### 1）使用原始数据类型，而不是引用类型。
### 2）符号表有时需考虑重复键的可能性。

## 2. 集合的API
数学中的**集合**的实现
    集合数据类型的一组基本API
public class|SET&lt;KEY>|说明
-:|:-|-
&nbsp;|SET()|创建一个空的集合
void|add(Key key)|将键加入集合
void|delete(Key key)|从集合中删除键key
boolean|contains(Key key)|键key是否在集合之中
boolean|isEmpty()|集合是否为空
int|size()|集合中键的数量
String|toString()|对象的字符串表示
### 过滤器应用：
- ### dedup
    去重过滤器的原型是一个调用SET或者HashSET来去掉输入流中的重复项的程序。
- ### 白名单与黑名单
## 3. 字典类用例
## 4. 索引类用例
  索引：用来描述一键和多值相关联的符号表。
  反向索引：是指用值来查找键的操作。
## 5. 稀疏向量
  矩阵和向量的乘法是$N^2$级的。
  对于稀疏矩阵，可用稀疏向量算法来提高性能：
  不再使用a[i][j]来访问矩阵中第i行第j列的元素，而是使用a[i].put(j,val)来表示矩阵中的值并使用a[i].get(j)来获取它。
