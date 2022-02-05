# Masmali
```c++
# Masmali
#include<iostream>
#include<map>
using namespace std;
#define ull unsigned long long int
ull c(ull n, ull k){
	ull l=1,i=k, j=n-k;
	if(k==0 || k==n) return 1;
	if(k==1 || k==n-1) return n;
	while(n>0){
		l*=n; //n!
		while(l%i==0 && i>1){//k!
			l/=i;
			i--;
			}
		while(l%j==0 && j>1){  //(n-k)!
			l/=j;
			j--;
			}
		n--;
	}
	return l;
}
ull I,O,v,o, dp[220][220];
ull n; string s; ull sum=1;
int main(){
	//purely combinatorics
	cin>>n>>s;
	for(int j=0; j<s.length(); j++)
		if(s[j]=='I') v++;
		else o++;
	ull nn=n;
	n-=o; //reduce n by number of balanced parentheses in the initial sequence
	I=n-v; //relevant Is (initial)n-v+o
	O=n;	
	v-=o;
	//relevant Os n-o
	if(O<v) cout<<c(I+O,O);
	else if(v==nn) cout<<1;
	else if(v>1 && O>=v) cout<<c(I+O, O)-c(I+O-1,O-v-1); 
	// (number of sequences in which number of O's does not surpass number of I's by v+1 or more)
	else cout<<c(2*n, n)-c(2*n, n+1);  //catalan number for unbalanced n 
	return 0;
	
}

```
