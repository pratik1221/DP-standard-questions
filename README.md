# DP-standard-questions

                          **Knapsack**
 0/1
 ll knapsack(ll wt[],ll p[],ll w,ll n)
{
    if(n==0||w==0)
    return 0;
    else if(wt[n]>w)
    return knapsack (wt,p,w,n-1);
    else
    return max(p[i-1]+knapsack(wt,p,w-wt[n],n-1),knapsack(wt,p,w,n-1));
}
ll kp(ll n,ll w)
{
    if(w<0)
    return INT_MIN;
    if(n==0)
    if(dp[w][n]!=-1)
    return dp[w][n];
    else
    return dp[n][m]=max(profit[i-1]+ks(n-1,w-wt[n-1]),ks(n-1,w));
    
}

Multiple occurences

 ll knapsack(ll wt[],ll p[],ll w,ll n)
{
    if(n==0||w==0)
    return 0;
    else if(wt[n]>w)
    return knapsack (wt,p,w,n-1);
    else
    return max(p[i-1]+knapsack(wt,p,w-wt[n],n),knapsack(wt,p,w,n-1));
}

                           
                           
                           
                           
                           
                           
                           
                           
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
                                      ***LONGEST PALINDROMIC SUBSTRING***

  
// This function prints the 
// longest palindrome substring (LPS) 
// of str[]. It also returns the 
// length of the longest palindrome 
int longestPalSubstr(char* str) 
{ 
    // The result (length of LPS) 
    int maxLength = 1; 
  
    int start = 0; 
    int len = strlen(str); 
  
    int low, high; 
  
    // One by one consider every 
    // character as center point of 
    // even and length palindromes 
    for (int i = 1; i < len; ++i) { 
        // Find the longest even length palindrome 
        // with center points as i-1 and i. 
        low = i - 1; 
        high = i; 
        while (low >= 0 && high < len 
               && str[low] == str[high]) { 
            if (high - low + 1 > maxLength) { 
                start = low; 
                maxLength = high - low + 1; 
            } 
            --low; 
            ++high; 
        } 
  
        // Find the longest odd length 
        // palindrome with center point as i 
        low = i - 1; 
        high = i + 1; 
        while (low >= 0 && high < len 
               && str[low] == str[high]) { 
            if (high - low + 1 > maxLength) { 
                start = low; 
                maxLength = high - low + 1; 
            } 
            --low; 
            ++high; 
        } 
    } 
  
    cout << "Longest palindrome substring is: "; 
    printSubStr(str, start, start + maxLength - 1); 
  
    return maxLength; 
} 
    //PRINTING THE SUBSTRING                                 
 void printSubStr(char* str, int low, int high) 
{ 
    for (int i = low; i <= high; ++i) 
        cout << str[i]; 
} 
