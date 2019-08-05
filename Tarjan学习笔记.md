_在最近学习中遇到了几次题解使用Tarjan的情况，便查了一些资料。_
### 算法简介
一种由Robert Tarjan提出的求解有向图强连通分量的线性时间的算法。
#### 前置解释
1.如果**有向图**两个顶点可以相互通达，则称两个顶点**强连通**_(strongly connected)。_  
2.如果有向图G的**每**两个顶点都强连通，称G是一个**强连通图**。  
3.有向图的极大强连通子图，称为**强连通分量**_(strongly connected components)_。
### 举个例子
![图1](https://upload-images.jianshu.io/upload_images/15974891-78551b7cbac95322.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

在图1中，图{1,2,3,4}为一个强连通分量，因为1，2，3，4，都可以**两两到达**，当然｛5｝，｛6｝也是两个强连通分量。  
而我们Tarjan算法的**目的**就是求解有向图的强连通分量  
  
Tarjan算法是基于对图**深度优先搜索的算法**，每个强连通分量为搜索树中的一棵子树。搜索时，把当前搜索树中**未处理的节点**加入一个**堆栈**，回溯时可以判断栈顶到栈中的节点是否为一个强连通分量。  
#### 图解模拟有如下定义。

DFN[ i ] : 在DFS中该节点被搜索的次序(时间戳)

LOW[ i ] : 为i或i的子树能够追溯到的最早的栈中节点的次序号

当DFN[ i ]==LOW[ i ]时，为i或i的子树可以构成一个强连通分量。  

------------

以1号节点为Tarjan 算法的起始点，以DFS序开始搜  
![](http://upload-images.jianshu.io/upload_images/15974891-a7129d4f146e06b0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
顺次DFS搜到节点6，同时更新DFN,LOW  
![](https://upload-images.jianshu.io/upload_images/15974891-fe580fda93de2c94.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

开始回溯，发现LOW[ 5 ]==DFN[ 5 ] ,  LOW[ 6 ]==DFN[ 6 ] ,则{ 5 } , { 6 } 为两个强连通分量。  
![](http://upload-images.jianshu.io/upload_images/15974891-fd9366e8a8ebb4d3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
拓展节点1 ， 发现1在栈中更新LOW[ 4 ]，LOW[ 3 ] 的值为1  
![](http://upload-images.jianshu.io/upload_images/15974891-cce4f65071f0569b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
回溯节点1，拓展节点2  
![](http://upload-images.jianshu.io/upload_images/15974891-b6b9387633a740cf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
至此，Tarjan Algorithm 结束，{1 , 2 , 3 , 4 } , { 5 }　,  { 6 } 为图中的三个强连通分量。  
![](http://upload-images.jianshu.io/upload_images/15974891-e9c7879fefaf5c00.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  

### 时间复杂度
##### O（E+V）
每个顶点都被访问了一次，且只进出了一次堆栈，每条边也只被访问了一次
### 参考代码
**伪代码**
```tex
tarjan(u)
{
    DFN[u]=Low[u]=++Index//为节点u设定次序编号和Low初值
    Stack.push(u)//将节点u压入栈中
    for each(u,v) in E//枚举每一条边
        if (visnotvisted)//如果节点v未被访问过
            tarjan(v)//继续向下找
            Low[u]=min(Low[u],Low[v])
        else if (vinS)//如果节点v还在栈内
                Low[u]=min(Low[u],DFN[v])
    if (DFN[u]==Low[u])//如果节点u是强连通分量的根
    repeat{
        v=S.pop//将v退栈，为该强连通分量中一个顶点
        printv
        until(u==v)
    }
}
```
**C++代码**
```cpp
    void tarjan(int x){
        dfn[x]=low[x]=++tot;//入栈 
        sta[++num]=x;insta[x]=true;
        for(int i=head[x];i;i=edge[i].next){
            if(!dfn[edge[i].to]){
                tarjan(edge[i].to);
                low[x]=min(low[x],low[edge[i].to]);
            }
            else if(insta[edge[i].to])
            low[x]=min(low[x],dfn[edge[i].to]);
        }
        if(low[x]==dfn[x]){
            sa=0;
            do{sa++;insta[sta[num--]]=false;}//弹栈 
            while(x!=sta[num+1]);
            if(sa==2){puts("2");exit(0);}//到2就没必要继续了 
            if(sa>1)ans=min(ans,sa);//取最小值 
        }
    }
```
**以下列出参考的文章**，感谢这些作者提供的文章。
1.[Tarjan 算法&模板](http://www.cnblogs.com/shadowland/p/5872257.html)  
2.[P2661 信息传递 tarjan](https://www.luogu.org/blog/caonibb/p2661-xin-xi-zhuan-di-tarjan)  
3.[百度百科-tarjan算法](https://baike.baidu.com/item/Tarjan%E7%AE%97%E6%B3%95/10687825)
