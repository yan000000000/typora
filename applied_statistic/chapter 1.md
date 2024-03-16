## Sets

A set is a collection of objects, which are the elements of the set

### element relation

#### in

$x \in S$: $S$ is a set and  $x$ is an element of $S$​

#### not in

$x \notin S$: $x$ is not an element of  $S$​

#### empty set

$\emptyset$: A set that has no element --> empty set

### set relation

#### subset

 $S\subseteq T$

#### equal set

 $S = T$

#### universal set

 $\Omega$ : a set that holds all the element in the sample

#### complement

 $\bar{S} = S^c = \Omega - S$

### set operation

#### union of sets

 $S \cup T$ 

#### intersection of sets

 $S \cap T \ \  \cap^{\infty}_{i = 1}S_i \ \ \ \cap_{i\in I}S_i$ 

#### De Morgan's laws

 $\bar{U_iS_i}$ =  $\cap_i\bar{S_i}$ ,  $\bar{\cap_iS_i} = \cup_i\bar{S_i}$ 

## Probabilistic models

a probabilistic model is a mathematical description of a uncertain situation

#### experiment

a underlying process involves in every probabilistic model

E.g. Flip 2 coins

#### outcomes

one out of several possible outcomes that experiment produces

E.g. head or tail for flipping coins

#### sample space

the set of all possible outcomes, usually denoted by $\Omega$ 

E.g. both head and tail are in the sample space of flipping coins

##### Attention

* different element of the sample space should be distinct and mutually exclusive
* the sample space should be collectively exhaustive, which means that it should cover all the possible outcome

#### event

a subset of the sample space

 $A \subseteq \Omega$ is a set of possible sample space

E.g.  $A = \{HH,TT\}$ , this is a event that 2 coins give the same side



### capacity of sample space

sample space may consist of finite or infinite number of possible outcome

E.g. throwing dice -- **finite**/ throwing dart(扔飞镖) -- **infinite** 

### sequential models

it is a model used to describe experiments by the mean of tree-based sequential description

E.g.  tossing a coin 3 times/observing the value of a stock on 5 successive(continuous) days

<img src=".assets/image-20240316155216603.png" alt="image-20240316155216603" style="zoom:50%;" />

### probabilistic law

the probabilistic law assigns to a set $A$ of possible outcomes a nonnegative number  $P(A)$ 

the value of $P(A)$ can be view as the likelihood of element $A$ 

#### e.g.

for tossing 2 coins

What's  $P(HH),P(HT),P(TT),P(TH)$ ?

for uniform distribution, we have

 $P(HH) = P(HT) = P(TH) = P(TT) = \frac{1}{4}$ 

for  $A = \{HH, TT\}$, we have  

$P(A) = \frac{1}{2} $ in uniform distribution

### Probability Axioms(公理)

#### non-negativity

for every event of $A$, we have  $P(A)\geq 0$

#### additivity

for any 2 disjoint events  $A$ and $B$ ，  $P(A \cup B) = P(A)+P(B)$ 

In general, if  $A_1,A_2,\cdots$ are disjoint events, we have $P(A_1 \cup A_2 \cup \cdots) = P(A_1) + P(A_2)+ \cdots$ 

#### normalization

 $P(\Omega) = 1$ ,where  $\Omega$ stands for the sample space

