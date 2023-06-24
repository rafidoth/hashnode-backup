---
title: "Binary Exponentiation: Explanation for dummies like me"
seoTitle: "Binary Exponentiation: Explanation for dummies like me"
seoDescription: "The Binary Exponentiation is a trick to calculate  in O(logn) instead of O(n)

Let's see ,
 equals the value of 1 multiplied by a, n times. This process tak"
datePublished: Sat Jun 24 2023 01:21:17 GMT+0000 (Coordinated Universal Time)
cuid: clj9bewyf000209ma5qzj773u
slug: binary-exponentiation-explanation-for-dummies-like-me
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1687569452297/6ab99eef-88b7-48e5-9d89-30deda24c32a.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1687569586743/3bc17eea-a216-4b63-a14f-071943e14f9a.png
tags: competitive-programming, problem-solving, cpp-tutorial, binary-exponeniation

---

The Binary Exponentiation is a trick to calculate \\(a^n\\) in O(logn) instead of O(n)

Let's see \\(a^n\\),  
\\(a^n \\) equals the value of 1 multiplied by a, n times. This process takes O(n) operations we can do this quickly using binary exponentiation.

$$a^n = 1.a.a.a......(n )times$$

`Just keep following the process, it helps to understand the algorithm.`

Suppose we will calculate \\(3^{13}\\)

### prerequisite

I think we all know that \\(a^n =a^{b+c}= a^b.a^c\\) if \\(n= b+c\\)

### Main Process

We'll convert n to its binary form. Suppose the binary form of the n is something like this 10101 (21 in decimal), it's imaginary. But we bring the power to a series of power of 2s like this.

$$\displaylines{ a^{n=21}=a^{10101}= a^{1.2^4+0.2^3+1.2^2+0.2^1+1.2^0}\\ \downarrow \\ a^n = a^{1.16+0.8+1.4+0.2+1.1}\\ \downarrow \\ a^n = a^{16+0+4+0+1}\\ \downarrow \\ a^n = a^{16}. a^4 . a^1}$$

**Let's see one more time on 3^{13}**

$$\displaylines{ 3^{13}= 3^{1101}= 3^{1.2^3+1.2^2+0.2^1+1.2^0} \\ \downarrow \\ 3^{13}=3^{1.8+1.4+0.2+1.1} \\ \downarrow \\ 3^{13} = 3^8.3^4.3^{0.2}.3^1 }$$

look here we are doing fewer operations than the regular approach. Now we have to build the algorithm. Let's do fun.

Now let us try with some other numbers like:

1. Convert n to binary form \\(13 \rightarrow1101\\)
    
2. Iterate binary digits from right to left
    
    * if the iterated value is
        
        * \\(1 \rightarrow\\) `result = result * a`
            
        * \\(0 \rightarrow do-nothing\\)
            
    * calculate \\(a= a*a\\) (doing square the previous value of `a` in every step will give \\(a, a^2, a^4, a^8\\))
        

### **code**

```cpp
long long binpow(long long a, long long n) {
    long long res = 1; //initialization
    while (n > 0) { 
        if (n & 1) // checking if the last digit is 1 or not
            res = res * a;
        a = a * a; //squaring the previous term
        n >>= 1; //removing the last digit
    }
    return res;
}
```

This binary exponentiation has so many applications. We'll see them in the next articles. Happy Learning!