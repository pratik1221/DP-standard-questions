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
                
                
                
                
                ***COUNT THE NUMBER OF SUBSTRINGS (of length greater than equal to2)**
                
int countPalindromes(string s) 
{ 
    unordered_map<string, int> m; 
    for (int i = 0; i < s.length(); i++) { 
  
        // check for odd length palindromes 
        for (int j = 0; j <= i; j++) { 
  
            if (!s[i + j]) 
                break; 
  
            if (s[i - j] == s[i + j]) { 
  
                // check for palindromes of length 
                // greater than 1 
                if ((i + j + 1) - (i - j) > 1) 
                    m[s.substr(i - j,  
                        (i + j + 1) - (i - j))]++; 
  
            } else
                break; 
        } 
  
        // check for even length palindromes 
        for (int j = 0; j <= i; j++) { 
            if (!s[i + j + 1]) 
                break; 
            if (s[i - j] == s[i + j + 1]) { 
  
                // check for palindromes of length  
                // greater than 1 
                if ((i + j + 2) - (i - j) > 1) 
                    m[s.substr(i - j,  
                         (i + j + 2) - (i - j))]++; 
  
            } else
                break; 
        } 
    } 
    return m.size(); 
}
if(of all length palindromic substring is asked  then simply add length of string)




                                                        *****Count substrings of a given string whose anagram is a palindrome****(Bit mask)
                                                        
                                                        
 Bit Masking Approach: The idea is to generate the masks of 26-bit numbers as there are 26 characters. Also, observe that if the anagram of some string is a palindrome, then the frequencies of its characters except at most one character must be even. 
Follow the steps below to solve the problem

Traverse the string and initialize a variable X = 0 at each index.
From every ithe index, traverse the string over a range of indices [i, N – 1], and for each character S[j], calculate Bitwise XOR of X and 2(S[j] – ‘a’), where 0th bit represents if the frequency of a is odd, 1st bit represents if the frequency of b is odd, and so on.
Then, check if X & (X – 1) is equal to 0 or not. If found to be true, then increment the count by 1. 

O(N^2)


// Function to print count of substrings
// whose anagrams are palindromic
void countSubstring(string s)
{
    // Stores the answer
    int res = 0;
 
    // Iterate over the string
    for (int i = 0;
         i < s.length(); i++) {
 
        int x = 0;
 
        for (int j = i;
             j < s.length(); j++) {
 
            // Set the current character
            int temp = 1 << s[j] - 'a';
 
            // Parity update
            x ^= temp;
            if ((x & (x - 1)) == 0)
                res++;
        }
    }
 
    // Print the final count
    cout << res;
}



O(N)

Efficient Approach: To optimize the above Bit Masking technique, the idea is to use a Map. Follow the steps below to solve the problem: 

Initialize a map to store the frequencies of the masks. Initialize a variable X = 0.
Traverse the string and for every ith index, calculate Bitwise XOR of X and 2(S[j] – ‘a’) and update the answer by adding the frequency of the current value of X in the Map because if any substring from 0 to j has the same mask as that of X, which is a mask for substring from 0 to i, then substring S[j + 1, i] will have even frequencies, where j < i.
Also add the frequencies of masks X xor 2k, where, 0 ≤ k < 26. After that, increment the frequency of X by 1.
Repeat the above steps for each index of the given string.
After traversing the given string, print the required answer.


// Function to get the count of substrings
// whose anagrams are palindromic
void countSubstring(string s)
{
    // Store the answer
    int answer = 0;
 
    // Map to store the freq of masks
    unordered_map<int, int> m;
 
    // Set frequency for mask
    // 00...00 to 1
    m[0] = 1;
 
    // Store mask in x from 0 to i
    int x = 0;
    for (int j = 0; j < s.length(); j++) {
        x ^= 1 << (s[j] - 'a');
 
        // Update answer
        answer += m[x];
        for (int i = 0; i < 26; ++i) {
            answer += m[x ^ (1 << i)];
        }
 
        // Update frequency
        m[x] += 1;
    }
 
    // Print the answer
    cout << answer;
}
