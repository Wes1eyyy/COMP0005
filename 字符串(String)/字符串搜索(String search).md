### 1. R-way Trie（R向Trie）
![[Pasted image 20240514062824.png]]
R-way Trie是一种基于字符集大小的树形数据结构，用于存储字符串集。在这种Trie中，每个节点可能有R个子节点，其中R是字母表的大小。例如，对于英文小写字母，R可能是26。

**结构**：
- 每个节点包含R个可能的子节点链接，每个链接对应字母表中的一个字符。
- 节点可能包含一个值，该值表示一个与该节点相对应的字符串（如果存在）。

**操作**：
- **插入**：将一个字符串插入到Trie中，从根节点开始，为字符串中的每个字符创建或遍历一个对应的链接。
![[Pasted image 20240514063127.png]]
- **搜索**：检查一个字符串是否存在于Trie中，遵循从根到叶的路径，每个字符指示下一个子节点的选择。
- **前缀查询**：找出所有以某个字符串为前缀的条目。

**优点**：
- 快速的搜索时间，理论上与要搜索的字符串长度成线性关系。
- 高效的空间使用，共享公共前缀。

**缺点**：
- 高内存消耗，尤其是当字母表很大时。

**伪代码**
![[Pasted image 20240514063452.png]]
![[Pasted image 20240514063512.png]]

### 2. 3-way Trie（三向切分Trie）
![[Pasted image 20240514064427.png]]
三向切分Trie（Ternary Search Trie, TST）是另一种用于字符串搜索的高效数据结构，通过将键存储在三向切分的树中来管理字符串。

**结构**：
- 每个节点包含一个字符、三个子节点链接（左子节点、中子节点、右子节点）、以及可能的值。
- 左子节点包含所有以较小字符开头的字符串，右子节点包含所有以较大字符开头的字符串，中子节点继续当前字符的下一个字符。

**操作**：
- **插入**：将一个字符串插入TST，根据字符比较结果选择左、中或右子树进行递归插入。
- **搜索**：遵循与插入相同的比较逻辑，查找字符串。
- **前缀查询**：类似于R-way Trie，但可以更灵活地只访问相关子树。

**优点**：
- 比R-way Trie更高的空间效率，尤其是在字母表较大或字符串长度变化较大时。
- 支持快速的近似匹配和排序操作。

**缺点**：
- 搜索操作可能涉及多个方向的比较，尤其是在深度较大或不平衡的TST中。


**总的来说，选择这两种Trie的结构取决于应用的具体需求。**
- R-way Trie适用于字符集较小且查询速度需求较高的应用，
- 三向切分Trie更适合处理字符集较大或键长度变化大的情况，需要更高的空间效率和灵活的查询操作。

#### Tries Extended API
![[Pasted image 20240514071004.png]]
![[Pasted image 20240514071108.png]]