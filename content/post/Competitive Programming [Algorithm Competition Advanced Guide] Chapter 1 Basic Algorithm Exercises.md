---
layout:     post
title:      "Competitive Programming [Algorithm Competition Advanced Guide] Chapter 1 Basic Algorithm Exercises"
date:     2022-08-24
author:  Jacky Tang
categories: ["Computer Science"]
tags:
    - Competitive Programming
    - C++
URL: "/2022/08/24/algorithm-competition-advanced-guide-ch1/"
---
![Coverpage2](/img/algorithm-competition-advanced-guide-ch1/cover.jpg)

## POJ1995 (Bitwise Operation)
https://vjudge.net/problem/POJ-1995
```#include <iostream>
#include <cstdio>
#define ll long long
using namespace std;
ll mod;
ll ans;
int Z,M,H;
ll power(ll a, ll n, ll p)
{
    int ans = 1%p;
    for(; n; n>>=1){
        if(n & 1) ans = (long long) ans * a % p;
        a = (long long) a * a % p;
    }
    return ans;
}

int main()
{
    cin>>Z;
    while(Z--)
    {
        ans=0;
        cin>>M>>H;
        mod=M;
        for(int i=0;i<H;i++)
        { 

            ll a,b;
            cin>>a>>b;
            ans+=power(a, b, mod);
        }
        ans = power(ans, 1, mod);
        cout << ans << endl;
    }
}
```

## CH0102/AcWing90 (Bitwise Operation)
https://www.acwing.com/problem/content/92/
```
#include <bits/stdc++.h>

using namespace std;

int main(){
    long long a, b, p, ans=0;
    cin >> a >> b >> p;
    for(; b; b >>= 1){
        if(b & 1) ans = (ans + a) % p;
        a = a * 2 % p;
    }
    cout << ans << endl;
}
```
## CH0103/AcWing91 (Bitwise Operation)
https://www.acwing.com/problem/content/93/
```
#include<bits/stdc++.h>
using namespace std;

int f[1 << 20][20];
int hamilton(int n, int weight[20][20]){
    memset(f, 0x3f, sizeof(f));
    f[1][0] = 0;
    for(int i=0; i < 1<<n; i++){
        for(int j=0; j<n; j++)  if (i >> j & 1)
                for(int k=0; k < n; k++) if((i^1<<j) >> k & 1)
                         f[i][j] = min(f[i][j], f[i^1 << j][k] + weight[k][j]);
            }
    return f[(1 << n) - 1][n-1];
}
int main(){
   int n;
   int weight[20][20];
   cin >> n;
   for(int i=0; i<n; i++)
       for(int j=0; j<n; j++) {
           cin >> weight[i][j];
           weight[j][i] = weight[i][j];
       }
   cout << hamilton(n, weight) << endl;
}
```
## CH0301/AcWing92 (Recursion)
https://www.acwing.com/problem/content/description/94/
```
#include<bits/stdc++.h>

using namespace std;

vector<int> chosen;
int n;
void calc(int x){
    if(x == n+1){
        for(int i=0; i< chosen.size(); i++){
            printf("%d ", chosen[i]);
        }
        puts("");
        return;
    }
     calc(x+1);
     chosen.push_back(x);
     calc(x+1);
     chosen.pop_back();
}
int main(){
    cin >> n;
    cout << " " << endl;
    calc(1);
}
```
## CH0303/AcWing94 (Recursion)
https://www.acwing.com/problem/content/96/
```
#include <bits/stdc++.h>

using namespace std;
int order[20];
bool chosen[20];
int n;
void calc(int k){
    if(k == n+1){
        for(int i=1; i<=n; i++)
            printf("%d ", order[i]);
        puts("");
        return;
    }
    for(int i=1; i <= n; i++){
        if(chosen[i]) continue;
        order[k] = i;
        chosen[i]=1;
        calc(k+1);
        chosen[i]=0;
    }
}

int main(){
    cin >> n;
    calc(1);
}
```
## POJ1958/AcWing96 (Recurrence Relation)
https://vjudge.net/problem/POJ-1958
```
#include <iostream>
#include <cmath>
#include <cstring>
using namespace std;

int main(){
    int d[15],  f[15];
    d[1]=1;f[0]=0;
    memset(f,0x3f,sizeof(f));
    f[0]=0;
    for(int i=2; i<=12; i++)
        d[i] = d[i-1]*2+1;
    for(int i=1; i<=12; i++)
       for(int j=0; j<i; j++){
           f[i] = min(f[i], f[j]*2 + d[i-j]);
       }
    for(int i=1; i<=12; i++)
        cout << f[i] << endl;
}
```

## POJ3889/AcWing98 (Fractals, Recursion)
https://vjudge.net/problem/POJ-3889
```
#include<cstdio>
#include<iostream>
#include<cstring>
#include<cmath>
#include<algorithm>
#define ll long long
using namespace std;
int T;
pair<ll,ll> calc(ll n,ll m){
    if(n == 0) return {0,0};
    ll len = 1ll<<(n-1),num = 1ll<<2*(n-1);
    pair<ll,ll> temp = calc(n-1,m%num);
    ll x = temp.first,y = temp.second;
    ll z = m/num;
    if(z == 0) return {y,x};
    if(z == 1) return {x,y+len};
    if(z == 2) return {x+len,y+len};
    else return {2*len-1-y,len-1-x};
}
int main(){
    scanf("%d",&T);
    ll n,a,b;
    while(T--){
        cin>>n>>a>>b;
        pair<ll,ll> t1 = calc(n,a-1);
        pair<ll,ll> t2 = calc(n,b-1);
        ll tx = t1.first-t2.first;
        ll ty = t1.second-t2.second;
        double ans = sqrt(tx*tx+ty*ty)*10;
        printf("%.0lf\n",ans);
    }
    return 0;
}  
```                      
## AcWing99(Prefix Sum, Inclusion-Exclusion Principle)
https://www.acwing.com/problem/content/description/101/
```
#include <iostream>

using namespace std;

#define N 5002
int f[N][N];

int main() {

    int n, r;
    int max_x, max_y;
    int x = 0, y = 0, w = 0;
    cin >> n >> r;
    r = min(r, 5001);
    max_x = max_y = r;
    for (int i = 0; i < n; ++i) {
        cin >> x >> y >> w;
        f[++x][++y] += w; 
        max_x = max(x, max_x); 
        max_y = max(y, max_y);
    }
    for (int i = 1; i <= max_x; ++i) { 
        for (int j = 1; j <= max_y; ++j) {
            f[i][j] = f[i - 1][j] + f[i][j - 1] - f[i - 1][j - 1] + f[i][j];
        }
    }

    int ans = 0;
    for (int i = r; i <= max_x; ++i) {
        for (int j = r; j <= max_y; ++j) {
            ans = max(ans, f[i][j] - f[i - r][j] - f[i][j - r] + f[i - r][j - r]);
        }
    }

    cout << ans << endl;

    return 0;
}
```