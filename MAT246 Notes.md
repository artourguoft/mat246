# <u>3: Set Theory</u>
A set is a collection of **unordered**, **distinct** objects called elements
- Operators on sets:
	- $|A|$, returns the size of the set
	- $x∈A$, returns True when is a **member** of set $A$
	- $x∉A$, returns True when is **not a member** of set $A$
	- $A⊆B$, returns True when every element of $A$ is an element of $B$, meaning $A$ is a **subset** of $B$
		- $A⊆A$, is always True
		- $∅⊆A$, is always True
	- $A = B$, returns True when $A⊆B$ and $B⊆A$, so $A$ and $B$ have the exact same elements which defines **set equality**
	- $A∪B$, returns the set of all elements that are in $A$, or $B$, or both; this is called the **union**
		- $\{x : x∈A∨x∈B\}$
		- Note the union is distributive over intersections, $A\cup (B\cap C)=(A\cup B)\cap(A\cup C)$, and commutative and associative with itself
	- $A∩B$, returns the set of all elements that are in $A$ and $B$, this is called the **intersection**
		- $\{x : x∈A∧x∈B\}$
		- Note the intersection is distributive over unions, $A\cap (B\cup C)=(A\cap B)\cup(A\cap C)$, and commutative and associative with itself
	- $A×B$, returns the set of all **ordered pairs** of elements in $A$ then $B$, this is the **cartesian product**
		- $\{(a,b) : a∈A∧b∈B\}$
		- $|A\times B|=|A||B|$, given that the sets are finite
			- If either or both sets are infinite, then $|A\times B|=\infty$
		- $\emptyset \times A=A\times \emptyset=\emptyset$
			- Note the product is **not commutative** otherwise; $A\times B\neq B \times A$ given $A\neq B$
		- $A\subseteq C\wedge B\subseteq D\implies A\times B\subseteq C\times D$
	- $A\backslash B$, returns the set of all elements that are in $A$ but not $B$, this is called the **set difference**
		- $\{x : x∈A∧x∉B\}$
	- $A^c$, returns the set of all elements that are in the universe of discourse but not in $A$; this called the **complement**, which is equivalent to the set difference $U\backslash A$, and thus DeMorgan's Law for sets:
		- $A^c∩B^c = (A∪B)^c$
		- $A^c∪B^c = (A∩B)^c$
		- Note, $A\backslash B=A\cap B^c$
	- $\mathcal{P}(A)$, returns the **set of all subsets** of $A$ (including $\emptyset$ and $A$), this is called the **power set**
		- $\{S : S⊆A\}$
		- $|\mathcal{P}(A)| = 2^{|A|}$
		- $A\subseteq B \iff \mathcal{P}(A)\subseteq \mathcal{P}(B)$
- **Collections of sets** can be **indexed** by other sets, ex. sets indexed by $\{ 1,2,3 \}$ would be $\{ A_{n} \}_{n=1}^{3}$
	- A collection of sets is **pairwise disjoint** if $A_{n}\cap A_{m}=\emptyset$ for all $n\neq m$
	- We also define unions and intersections over such collections of sets:
		- $\bigcup_{n\in \mathbb{N}}A_{n}:=\{ a : a\in A_{n}\text{ for some }n\in \mathbb{N}\}$
		- $\bigcap_{n\in \mathbb{N}}A_{n}:=\{ a : a\in A_{n}\text{ for all }n\in \mathbb{N}\}$
	- Distributivity applies to these larger unions and intersections as before:
		- $B\cap(\bigcup_{n\in \mathbb{N}}A_{n})=\bigcup_{n\in \mathbb{N}}(B\cap A_{n})$
		- $B\cup(\bigcap_{n\in \mathbb{N}}A_{n})=\bigcap_{n\in \mathbb{N}}(B\cup A_{n})$
	- As does DeMorgan's Law:
		- $(\bigcap_{n\in \mathbb{N}}A_{n})^c=\bigcup_{n\in \mathbb{N}}A_{n}^c$
		- $(\bigcup_{n\in \mathbb{N}}A_{n})^c=\bigcap_{n\in \mathbb{N}}A_{n}^c$
	- **Axiom of Choice:** for any arbitrary indexing set $N$ and every indexed collection of nonempty sets $\{ A_{n} \}_{n\in N}$, there exists an indexed collection of elements $\{ a_{n}\}_{n\in N}$ where $a_{n}\in A_{n}$ for each $n\in N$
		- This axiom guarantees the existence of mathematical objects that are obtained by a sequence of choices (in both finite or infinite cases)
# <u>7: Relations and Partitions</u>
For arbitrary sets $A,B$, a **relation** $R$ from $A$ to $B$ is a subset of their cartesian product; $R\subseteq A\times B$
- Note, the contents of the set are what defines a relation; the description of the relation is not!
- For $(a,b)\in R$, we say $a$ and $b$ are **related** or write shorthand $aRb$
- From the properties of cartesian products and ordered pairs, we have $aRb\centernot\implies bRA$
- Since $\emptyset \subseteq A\times A$, then we always have $\emptyset$ as the **empty relation** on $A$
- These concepts can be extended to any **arity**; in the common case of a relation where all $n$ sets are the same set $A$, we say the relation is an $n$-ary relation **on** $A$
	- However, we will almost always study **binary** relations (ie. ordered pairs between one or two sets)

For a relation $R$ on a set $A$, the relation is:
- **Reflexive**: if $\forall a\in A,aRa$ 
- **Symmetric:** if $\forall a,b\in A,aRb\implies bRa$
- **Transitive:** if $\forall a,b,c\in A,aRb\wedge bRc\implies aRc$
Note, **reflexivity is not defined** for relations between non-equal sets (and thus neither is equivalence; more on this just below)

Consider some common examples:
- $\leq$ on $\mathbb{R}$ is reflexive and transitive, but not symmetric
- $<$ on $\mathbb{R}$ is not reflexive nor symmetric, but it is transitive
- Relations about the elements having some commonality are generally symmetric
- Relations about ordering, such as ancestry, are generally transitive
- For a set $S$, the relation $\subseteq$ on $\mathcal{P}(S)$ is reflexive and transitive, but not symmetric
- Every relation on the empty set is vacuously reflexive, symmetric, and transitive

Relations that **satisfy all three properties** of reflexivity, symmetry, and transitivity are called **equivalence relations**
- For an equivalence relation $\sim$ on a set $A$ and each $a\in A$, we refer to the **set of elements related to** $a$ by $\sim$ as the **equivalence class** of $a$, shorthanded as $[a]_{\sim}$
	- $\forall a,b\in A,[a]_{\sim}=[b]_{\sim}\iff a\sim b$  
	- $\bigcup_{a\in A}[a]_{\sim}=A$
	- $\forall a,b\in A,([a]_{\sim}=[b]_{\sim})\vee ([a]_{\sim}\cap[b]_{\sim}=\emptyset)$
- The $a$ in $[a]_{\sim}$ is the **representative** of the equivalence class; from the theorems above we have that any element of an equivalence class can be used as its representative!
- The theorems above also imply that an equivalence relation $\sim$ on set $A$ breaks the entirety of $A$ up into pairwise disjoint subsets (where each subset is an equivalence class)
	- This is called a **partition**; a collection $S$ of subsets of $A$ such that:
		- $\forall X\in S,X\neq \emptyset$
		- $\forall X,Y\in S,X\neq Y\implies X\cap Y=\emptyset$
		- $\bigcup_{X\in S}X=A$
	- Ex. the relation $=$ on $\mathbb{R}$ is the most **fine-grained** partition of $\mathbb{R}$ possible (the granularity of partitions can of course vary, ex. the subsets of evens and odds is another partition of $\mathbb{R}$)
- Consider that equivalence relations and partitions are equivalent ways of viewing a given set!

For each $n\in \mathbb{N}$, define the following equivalence relation $\equiv_{n}$ on $\mathbb{Z}$:
$$\equiv_{n}:=\{(a,b)\in \mathbb{Z}^2:a-b=kn\text{ for some }k\in \mathbb{Z}\}$$
This is the **modulo congruence** relation; for $(a,b)\in\equiv_{n}$ we shorthand $a\equiv_{n}b$ meaning that $a$ is congruent to $b$ modulo $n$, meaning $n$ divides $a-b$
- We denote the equivalence class of $a$ with respect to $\equiv_{n}$ as $[a]_{n}$; this is called the **congruence class** of $a$ modulo $n$
- $\forall n\in \mathbb{N},a,b,\in \mathbb{Z},[a]_{n}=[b]_{n}\iff n|(a-b)$, ie. since $n$ divides $a-b$, both are representatives of the same congruence class, and vice versa