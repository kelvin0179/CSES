### Sum of Divisors

```cpp
ll d,x,y;
void extendedEuclid(ll A, ll B) {
    if(B == 0) {
        d = A;
        x = 1;
        y = 0;
    }
    else {
        extendedEuclid(B, A%B);
        ll temp = x;
        x = y;
        y = temp - (A/B)*y;
    }
}

ll modInverse(ll A, ll M)
{
    extendedEuclid(A,M);
    return (x%M+M)%M;
}
ll mul(ll a,ll b)
{
    ll k=((a%MOD)*(b%MOD))%MOD;
    return k;
}
ll add(ll a,ll b)
{
    ll k=((a%MOD)+(b%MOD))%MOD;
    return k;
}
ll diff(ll a,ll b)
{
    ll k=(((a%MOD)-(b%MOD))+MOD)%MOD;
    return k;
}
ll divi(ll a,ll b)
{
    ll k=((a%MOD)*(modInverse(b,MOD)))%MOD;
    return k;
}
void solve()
{
    ll n;
    read(n);
    ll i=1,ans=0,rght,lft=i;
    while(i<=n)
    {
        ll times=n/i;
        ll tempAns=0;
        rght=(n/times);
        tempAns=add(tempAns,(divi(mul(rght,add(rght,1)),2)));
        tempAns=diff(tempAns,(divi(mul(lft,diff(lft,1)),2)));
        tempAns=mul(tempAns,times);
        ans=add(ans,tempAns);
        i=lft=rght+1;
    }
    write(ans);
}
```
![image](https://user-images.githubusercontent.com/56430190/125108596-dc2ab200-e0ff-11eb-86c7-336450b7b5cc.png)
