# Recurrent Recurrences

Give big $\Theta$ bounds for the following recurrence relations.

1.
$$ T(n) =
    \begin{cases}
        1 & n \leq 1\\
        T\left(\frac{n}{13}\right) + 5 & n > 1
    \end{cases}
$$

2.
$$ T(n) =
    \begin{cases}
        1 & n \leq 1\\
        13 T\left(\frac{n}{13}\right) + 5 & n > 1
    \end{cases}
$$

3.
$$ T(n) =
    \begin{cases}
        1 & n \leq 1\\
        13 T\left(\frac{n}{13}\right) + 2n & n > 1
    \end{cases}
$$

“I certify that I have listed all sources used to complete this exercise, including the use
of any Large Language Models. All of the work is my own, except where stated
otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is
suspected, charges may be filed against me without prior notice.”-Andrew Thomas

### Sources

n01.-https://www.youtube.com/watch?v=XjdDt2xU-tw- Got the geometric series formula from here

n02.-Solution: Chat GPT Querey  '$$ \begin{align}     & T(n)=13T(\frac{n}{13})+2n \\\\     & T(\frac{n}{13})=13T(\frac{n}{13^2})+\frac{2n}{13} \\     & \\     &=13(13T(\frac{n}{13^2})+\frac{2n}{13})+2n \\     &=13^2T(\frac{n}{13^2})+2n+2n \\     &=13^2T(\frac{n}{13^2})+4n \\     & \\     & T(\frac{n}{13^2})=13T(\frac{n}{13^3})+\frac{2n}{13^2}    \\     & \\     & =13^2(13T(\frac{n}{13^3})+\frac{2n}{13^2})+4n \\     & =13^3T(\frac{n}{13^3})+2n+4n \\     & =13^3T(\frac{n}{13^3}) +6n \\     & \text{Generalizing we obtain:} \\     & T(n)=13^iT(\frac{n}{13^i})+2ni \\     & \text{Similarly as in problems 1 and 2: }  i=log_{13}(n) \\     & =13^{log_{13}(n)}T\Big(\frac{n}{13^{log_{13}(n)}}\Big)+2n(log_{13}(n)) \\     &= n\cdot 1 +2nlog_{13}(n) \\     &=nlog_{13}(n) \\     & nlog_{13}(n) \in \Theta(nlog_{13}(n))   \end{align} $$. This wont compile in github what should i do?'

I used the querey above to get my work to show in github because I couldn't get it to compile

## The Answers
Problem 1: 
$$\textcolor{Yellow}{T(n)\in \Theta(log_{13}(n))}$$

Problem 2:
$$\textcolor{Yellow}{T(n) \in \Theta(n)}$$

Problem 3:
    $$\textcolor{Yellow}{T(n)\in \Theta(nlog_{13}(n)}$$


## The Work
### Problem 1:

$$ 
T(n)=
\begin{cases}
    1 & n \leq 1 \\
    T(\frac{n}{13})+5 & n>1
\end{cases} 
$$

Solution:

$T(n)=T(\frac{n}{13})+5$ 

Solving for $T(\frac{n}{13})$

$T(\frac{n}{13})=T(\frac{n}{13^2})+5$

---

$T(n)=T(\frac{n}{13^2})+5+5$

$=T(\frac{n}{13^2})+10$

Solving for $T(\frac{n}{13^2}):$

$T(\frac{n}{13^2})=T(\frac{n}{13^3})+5$

---
$=T(\frac{n}{13^3})+5+10$

$=T(\frac{n}{13^3})+15$

Now that we have some iterations performed we can build the following recurrance relation:

$T(n)=T(\frac{n}{13^i})+5i$

Solving for $i$ we have:

$\frac{n}{13^i}=1$ 

$i=log_{13}(n)$

Repalcing all instances of i our equation becomes:

$T(n)=T(\frac{n}{13^{log_{13}(n)}})+5(log_{13}(n))$

Then note that when  $i=log_{13}(n)$ then $T(\frac{n}{13^{log_{13}(n)}})=1$ because thats the base case. With this information in mind we then obtain:

$T(n)=1*5log_{13}(n) \in \Theta(log_{13}(n))$

$T(n) \in \Theta(log_{13}(n))$


### Problem 2:

$$
T(n)=\begin{cases}
    1 & n \leq 1 \\
    13T(\frac{n}{13})+5 & n>1
\end{cases}
$$

Solution:
$T(n)=13T(\frac{n}{13})+5$

Solving for $T(\frac{n}{13})$

$T(\frac{n}{13})=13T(\frac{n}{13^2})+5$

Plugging this in we have

$=13(13T(\frac{n}{13^2})+5)+5$

$=13^2T(\frac{n}{13^2})+13\cdot 5+5$

Solving for $T(\frac{n}{13^2})$: 

$T(\frac{n}{13^2})=13T(\frac{n}{13^3})+5$

Plugging this back in:

$13^2(13T(\frac{n}{13^3})+5)+13\cdot 5 +5$

$=13^3T(\frac{n}{13^3})+13^2\cdot 5+13\cdot 5+5$

Taking this into a general form we obatin

$$T(n)=13^iT(\frac{n}{13^i})+\sum_{j=1}^{i}5\cdot13^{j-1}$$

Solving for $i$:

$\frac{n}{13^i}=1 \\ i=log_{13}(n)$

Pluggin in $i$:

$T(n)=13^{log_{13}(n)}T\Big(\frac{n}{13^{log_{13}(n)}}\Big)+\frac{5(13^i-1)}{13-1}\text{   {-Geometric series fomula}}$

$=13^{log_{13}(n)}T\Big(\frac{n}{13^{log_{13}(n)}}\Big)+\frac{5(13^{log_{13}(n)}-1)}{13-1}$ 

$=n\cdot 1 +\frac{5(n-1)}{13-1}$

$=n+\frac{5}{13-1}\cdot n-\frac{5}{13-1}$

Dropping constants we then have:

$=2n=n \in \Theta(n)$



### Problem 3:

$$
T(n)=
\begin{cases}
    1 & n\leq 1 \\
    13T(\frac{n}{13})+2n & n>1
\end{cases}
$$

Solution:

$$ 
T(n) = 13T\left(\frac{n}{13}\right) + 2n 
$$

Expanding:

$$
T\left(\frac{n}{13}\right) = 13T\left(\frac{n}{13^2}\right) + \frac{2n}{13}
$$

$$
T(n) = 13 \left( 13T\left(\frac{n}{13^2}\right) + \frac{2n}{13} \right) + 2n
$$

$$
= 13^2 T\left(\frac{n}{13^2}\right) + 2n + 2n
$$

$$
= 13^2 T\left(\frac{n}{13^2}\right) + 4n
$$

Generalizing this pattern:

$$
T(n) = 13^i T\left(\frac{n}{13^i}\right) + 2ni
$$

Since   $$
i = log_{13}(n) 
$$ , we substitute:

$$
T(n) = 13^{\log_{13}(n)} T\left(\frac{n}{13^{\log_{13}(n)}}\right) + 2n \log_{13}(n)
$$

$$
= n \cdot 1 + 2n \log_{13}(n)
$$

$$
= n \log_{13}(n)
$$

Therefore, 

$$
T(n) \in \Theta(n \log_{13}(n))
$$
