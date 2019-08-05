*首先分析该问题，看数据大小，应当是一道dp题目，本题求得是最小值*
#### 状态分析
```dp[i][j]```表示，**字符串A**前```i```个字符到**字符串B**前```j```个字符的编辑距离
#### 转移方程：
![](https://upload-images.jianshu.io/upload_images/15974891-310458b0531d631b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/15974891-53074d37c4189087.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 附上Cpp代码
```cpp
#include <cstdio>
#include <iostream>
#include <cstring>
#define maxn 4003
#define maxx 0x3f3f3f3f
char a[maxn],b[maxn];
int dp[maxn][maxn];
int al,bl;
int minn(int ma,int mb,int mc){
	return std::min(std::min(ma,mb),mc);
}
int main(){
	std::cin >> a >> b;
	al = strlen(a);
	bl = strlen(b);
	for(int i=0;i<=al;++i){
		for(int j=0;j<=bl;++j){
			dp[i][j] = maxx;
		}
	}
	for(int i=0;i<=al;++i){
		dp[i][0] = i;
	}
	for(int j=0;j<=bl;++j){
		dp[0][j] = j;
	}
	for(int i=1;i<=al;++i){
		for(int j=1;j<=bl;++j){
			if(a[i-1] == b[j-1]){
				dp[i][j] = dp[i-1][j-1];
			}
			else{
				dp[i][j] = minn(dp[i-1][j],dp[i][j-1],dp[i-1][j-1])+1;
			}
		}
	}				
	std::cout << dp[al][bl] ;
	return 0;
}
```
