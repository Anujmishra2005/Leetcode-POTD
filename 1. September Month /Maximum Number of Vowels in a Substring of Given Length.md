# Maximum Number of Vowels in a Substring of Given Length

<h3>
  Given a string s and an integer k, return the maximum number of vowel letters in any substring of s with length k.

Vowel letters in English are 'a', 'e', 'i', 'o', and 'u'.

 

Example 1:

Input: s = "abciiidef", k = 3
Output: 3
Explanation: The substring "iii" contains 3 vowel letters.
Example 2:

Input: s = "aeiou", k = 2
Output: 2
Explanation: Any substring of length 2 contains 2 vowels.
Example 3:

Input: s = "leetcode", k = 3
Output: 2
Explanation: "lee", "eet" and "ode" contain 2 vowels.
 

Constraints:

1 <= s.length <= 105
s consists of lowercase English letters.
1 <= k <= s.length

</h3>

[Problem Link] :--- (https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/description/)

***Solution***

```

class Solution {
public:
    int isVowel(char ch)
    {
        return ch=='a'||ch=='e'||ch=='i'||ch=='o'||ch=='u';
    }
    int maxVowels(string s, int k) {
        vector<int>arr(26,0);
        int i=0;
        int j=0;
        int maxi=0;
        int n=s.size();
        for(i=0;i<k;i++)
        {
            arr[s[i]-'a']++;
            if(isVowel(s[i]))
             maxi++;
        }
        for(int i=k;i<n;i++,j++)
        {
            arr[s[j]-'a']--;
            arr[s[i]-'a']++;
            int c=0;
          for(int ind =0;ind<26;ind++)
          {
              if(ind==0 || ind=='e'-'a' || ind=='i'-'a' || ind=='o'-'a' || ind=='u'-'a')
                c+=arr[ind];
          }
          maxi=max(maxi,c);

        }
        return maxi;
        
    }
};

```
