![image1]()
```cpp
#include<stdio.h>
#include<iostream>
#include<cmath>
#include<vector>
#include<algorithm>
using namespace std;
int main(){
	int n,m;
	cin>>n>>m;
	string s1,s2;
	cin>>s1>>s2;
	int a[n+1][m+1];
	//初始化 
	for(int i=0;i<=n;i++){
		for(int j=0;j<=m;j++){
			a[i][j]=0;
		}
	}
	//dp
	//a[i][i]表示是s1前i个字符和s2前j个字符的最长公共子序列 
	for(int i=1;i<=n;i++){
		for(int j=1;j<=m;j++){
			if(s1[i-1]==s2[j-1]){
				a[i][j]=a[i-1][j-1]+1;
			} 
			else{
				a[i][j]=max(a[i-1][j],a[i][j-1]); 
			}
		}
	} 
	cout<<a[n][m];
	
	return 0;
}
/* 
Points：
		a[i][i]表示是s1前i个字符和s2前j个字符的最长公共子序列 
		if(s1[i-1]==s2[j-1]){
				a[i][j]=a[i-1][j-1]+1;
			} 
			else{
				a[i][j]=max(a[i-1][j],a[i][j-1]); 
			}
*/
```
