![image0](https://github.com/Erunning/Algorithm_solutions/blob/master/image/image0.png)
```cpp
#include<stdio.h>
#include<iostream>
#include<cmath>
#include<vector>
#include<algorithm>
using namespace std;
int main(){
	int n;
	cin>>n;
	int s[n+1];
	for(int i=1;i<=n;i++){
		cin>>s[i];
	} 
	int dp[n+1];//定义dp[i]为以a[i]结尾的最长上升子序列
	for(int i=1;i<=n;i++){
		dp[i]=1;//最小为1 
	} 
	for(int i=1;i<=n;i++){
		for(int j=1;j<i;j++){
			if(s[j]<s[i]){
				dp[i]=max(dp[j]+1,dp[i]);
			}
		}
	} 
	int max=1;
	for(int i=1;i<=n;i++){ 
		if(dp[i]>max) max=dp[i];
	}
	cout<<max;
	return 0;
}
/* 
Points：
		最长上升子序列 
		定义dp[i]为以a[i]结尾的最长上升子序列
*/
```
