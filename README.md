# DP-standard-questions


                            **LCS**
ll LCS(char s1[],char s2[],ll m,ll n)
{
    ll dp[m+1][n+1];
    // memset(dp,-1, sizeof(dp));
    
    f(i,0,m+1)
    {
        f(j,0,n+1)
        {
            if(i==0||j==0)
            dp[i][j]=0;
            else if(s1[i-1]==s2[j-1])
            dp[i][j]=1+dp[i-1][j-1];
            else
            dp[i][j]=max(dp[i-1][j],dp[i][j-1]);
        }
    }
    return dp[m][n];
}

                      **PRINT LCS**
  string printLcs(char s1[],char s2[],ll m,ll n)
{
    ll i=m;ll j=n;
    vector<char>v;
    while(i>0&&j>0)
    {
        if(s1[i-1]==s2[j-1])
    {
         v.pb(s1[i-1]);
        i--;
        j--;
    }
    else
    {
        if(dp[i-1][j]>dp[i][j-1])
        i--;
        else
        j--;
    }
    }
    reverse(v.begin(),v.end());
    string str="";
    f(i,0,v.size())
    str+=v[i];
    return str;

   

}

                                **LONGEST_COMMON_SUBSTRING**
ll LONGEST_COMMON_SUBSTRING(char s1[],char s2[],ll m,ll n)
{
    
    // memset(dp,-1, sizeof(dp));
    ll maxi=0;
    f(i,0,m+1)
    {
        f(j,0,n+1)
        {
            if(i==0||j==0)
            dp[i][j]=0;
            else if(s1[i-1]==s2[j-1])
            {
            dp[i][j]=1+dp[i-1][j-1];
            maxi=max(maxi,dp[i][j]);
            }
             else
            dp[i][j]=0;
        }
    }
    return maxi;
}
                                **MINIMUM NUMBER OF COINS(COIN CHAANGE PART1)**
ll minimumnumberofcoins(ll c[],ll n,ll amount)
{
    ll dp[amount+1];

    dp[0]=0;

    f(i,1,amount+1)
    dp[i]=INF;

    f(i,1,amount+1)
    {
       ll ans=INF;
       f(j,0,n)
       {
            if(c[j]<=i)
            ans=min(ans,dp[i-c[j]]);
       }
        if(ans==INF)
        dp[i]=INF;
        else
        dp[i]=ans+1;
        
    }
    if(dp[amount]==INF)
    return -1;
    else
     return dp[amount];
}
                          **coin change problem (infinite coins)-number of ways**
                          
ll numberofways(ll c[],ll n,ll amount)
{
    ll dp[n+1][amount+1];

    f(i,1,n+1)
    dp[i][0]=1;

    f(j,1,amount+1)
    dp[0][j]=0;

    f(i,1,n+1)
    {
        f(j,1,amount+1)
        {
            if(j>=c[i-1])
            dp[i][j]=dp[i][j-c[i-1]]+dp[i-1][j];
            else
            dp[i][j]=dp[i-1][j];
        }
        
    }
    return dp[n][amount];
}
                
