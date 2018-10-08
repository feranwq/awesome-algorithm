# 3. Longest Substring Without Repeating Characters

**<font color=red>�Ѷ�:Medium</font>**

## ˢ������

> ԭ������

*https://leetcode.com/problems/longest-substring-without-repeating-characters/description/
> ��������

```
��һ���ַ�����������ַ����в��ظ������ַ���
�������"abcabcbb"����Ϊ3
```

## ���ⷽ��

> ˼·1


�� map���� keyΪ�ַ���value Ϊ����ַ���λ�ã����ǿ���ά��һ�����ַ���(���ظ��ַ�)����¼������ʼλ�ã����� string s ���޷���map���ҵ��ַ�����С�����ַ�������ʼλ�ã�����û��������ַ����г��֣���֮���ַ��ظ������� map����Ϊ O(lgn)������ܵ�ʱ�临�Ӷ�ΪO(NlgN)
```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
   map<int,int> m;
    int beg = 0,length = s.length(),ll = 0,ans = 0;
    for(int i = 0;i < length;++i)
    {
        if(m.find(s[i]) == m.end() || m[s[i]] < beg)
            ll++;
        else
        {
            int pos = m[s[i]];
            ans = max(ll,ans);
            ll = ll - (pos - beg);
            beg = pos + 1;
        }
        m[s[i]] = i;
    }
    ans = max(ans,ll);
    return ans;
    }
};
```
> ˼·2

���˼·�������࣬�õ���һ��С���ţ���Ϊ��������ַ���charΪ8λ������ܴ���������Ϊ256������ʱ�临�ӶȾ�ΪO(N)
```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
         int m[256];
    for(int i = 0;i < 256;++i)
        m[i] = -1;
    int beg = 0,length = s.length(),ll = 0,ans = 0;
    for(int i = 0;i < length;++i)
    {
        if(m[s[i]] < beg)
            ll++;
        else
        {
            int pos = m[s[i]];
            ans = max(ll,ans);
            ll = ll - (pos - beg);
            beg = pos + 1;
        }
        m[s[i]] = i;
    }
    ans = max(ans,ll);
    return ans;
    }
};
```