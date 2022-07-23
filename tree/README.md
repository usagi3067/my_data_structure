# 树：

概念： 极小连通图 +  极大无环图

属性： 深度（根深度或为1 或为0） 高度   –> 某点到根（叶子）路径长度  特别注意空树的高度深度值。   笔者自身可加以规定没有严格说明。

当节点结构由自身属性（data)和父节点(parent)属性构成， 可引出一个简单算法： 并查集。

> 树自身构成一个极小连通图，极大无环图， 故每个结点都有唯一一个相同的根节点， 树与树之间可等价看作一个又一个的不同的集合。 

```c++
struct Node {
    int data;
    Node* parent;
};

//当存储结点为1~N时， 初始化时每个结点的父节点为自己
for(int i = 1; i <= N; i ++) Node[i].parent = &Node[i];

//返回结点i的祖宗节点
//假设已知结点i的父节点的祖宗结点， 去找结点i的祖宗结点
Node* find(int i) {
    if (Node[i].parent != &Node[i]) Node[i].parent = find(Node[i].parent);
    return Node[i].parent;
}

//合并i j所在的两个集合
ppi = find(i), ppj = find(j);
if (ppi != ppj) ppi->parent = ppj;
```



