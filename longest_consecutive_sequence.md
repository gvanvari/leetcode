# Longest Substring Without Repeating Characters and DNA sequencing

## Problem
Given a string s, find the length of the longest substring without repeating characters.

### Example 1:
    Input: s = "pwwkew"
    Output: 3
    Explanation: The answer is "wke", with the length of 3.
    Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.

## Code
```
    def lengthOfLongestSubstring(self, s: str) -> int:

        charSet = set()

        longest = 0
        
        leftPtr = 0

        for index,value in enumerate(s):

            while value in charSet:
                charSet.remove(s[leftPtr])
                leftPtr +=1

            charSet.add(value)

            longest = max(longest, index - leftPtr + 1)

        return longest
```

## DNA sequencing
[Here](https://www.ncbi.nlm.nih.gov/nuccore/PQ156960.1)'s an example of a sequence of DNA that codes for a type of protein in human white blood cells. The code is at the bottom of the page.  

```
Input: s=      
aggagaagagggatcaggacgaagtcccaggtcccgggcggggctctcagggtctcaggc
tccaagggccgtgtctgcactggggaggcgccgcgttgaggattctccactcccctgagt
ttcacttcttctcccaacctgcgtcgggtccttcttcctgaatactcatgacgcgtcccc
aattcccactcccattgggtgtcgggttctagagaagccaatcagcgtctccgcagtccc
ggttctaaagtccccagtcacccacccggactcggattctccccagacgccgagatgcgg
gtcatggcgccccgaaccctcatcctgctgctctcgggagccctggccctgaccgagacc
tgggcctgtgagtgcggggttgggagggaaacggcctctgcggagaggagcgaggggccc
gcccggcgagggcgcaggacccggggagccgcgcagggaggagggtcgggcgggtctcag
cccctcctcgcccccaggctcccactccatgaggtatttctacaccgccgtgtcccggcc
cggccgcggagagccccgcttcatcgcagtgggctacgtggacgacacgcagttcgtgcg
gttcgacagcgacgccgcgagtccaagaggggagccgcgggcgccgtgggtggagcagga
ggggccggagtattgggaccgggagacacagaagtacaagcgccaggcacaggctgaccg
agtgagcctgcggaacctgcgcggctactacaaccagagcgaggccggtgagtgaccccg
gcccggggcgcaggtcacgacccctccccatcccccacggacggcccgggtcgccccgag
tctcccggtctgagatccaccccgaggctgcggaacccgcccagaccctcgaccggagag
agccccagtcacctttacccggtttcattttcagtttaggccaaaatccccgcgggttgg
tcggggctggggcggggctcgggggacggggctgaccacgggggcggggccagggtctca
caccctccagaggatgtatggctgcgacgtggggcccgacgggcgcctcctccgcgggta
tgaccagtccgcctacgacggcaaggattacatcgccctgaacgaggacctgcgctcctg
gaccgctgcggacacggcggctcagatcacccagcgcaagtgggaggcggcccgtgaggc
ggagcagtggagagcctacctggagggcacgtgcgtggagtggctccgcagatacctgga
gaacgggaaggagacgctgcagcgcgcgggtaccaggggcagtggggagccttccccatc
tcctgtagatctcccgggatggcctcccacgaggaggggaggaaaatgggatcagcgcta
gaatatcgccctcccttgaatggagaatgggatgagttttcctgagtttcctctgagggc
cccctctgctctctaggacaattaagggatgaagtccttgaggaaatggaggggaagaca
gtccctggaatactgatcaggggtcccctttgaccactttgaccactgcagcagctgtgg
tcaggctgctgacctttctctcaggccttgttctctgcctcacgctcaatgtgtttaaag
gtttgattccagcttttctgagtccttcggcctccactcaggtcaggaccagaagtcgct
gttcctccctcagagactagaactttccaatgaataggagattatcccaggtgcctgtgt
ccaggctggcgtctgggttctgtgcccccttccccaccccaggtgtcctgtccattctca
ggatggtcacatgggcgctgttggagtgtcgcaagagagatacaaagtgtctgaattttc
tgactcttcccgtcagaacacccaaagacacacgtgacccaccatcccgtctctgaccat
gaggccaccctgaggtgctgggccctgggcttctaccctgcggagatcacactgacctgg
cagcgggatggcgaggaccaaactcaggacaccgagcttgtggagaccaggccagcagga
gatggaaccttccagaagtgggcagctgtggtggtgccttctggagaagagcagagatac
acgtgccatgtgcagcacgaggggctgcc
```
```
Output = 4
Explanation = {'g', 'a', 't', 'c'}
```
A DNA sequence cannot occur without all the 4 nucleotides. This code will help determine if there are all the nucleotides in the given sequence atleast once. So this code can be used to verify if the dna sequence is valid. If the sequence is invalid - may be a serious genetic disease ?