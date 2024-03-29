public:: true

- by *Alissa Tung <alissa-tung@outlook.com>*
- 🚧 This project is WORK IN PROGRESS. There are many TODOs to be done. Any report on typo, errors, and suggestions are welcome!
- Please refer to https://github.com/alissa-tung/hack-lean-in-lean-code for code example and exercises and exercises solutions.
- This material is initially purposed for a seminar about The Tactics in Lean4 hosted at BICMR, Peking University. The scoped of this little book is hopefully some gentle introduction to functional programming using dependent typed programming languages, and meta programming with interactive theorem provers. The technologies we mentioned here may or may not be applicable to other provers, but they should have many things in common.
- As one of the most attracting part of functional programming, the monad, is not a mystery concept. When talking about monads, people can refer to the famous quote "A monad in $X$ is just a monoid in the category of endofunctors of $X$, with product $\times$ replaced by composition of endofunctors and unit set by the identity endofunctor." (from *Categories for the Working Mathematician* by Saunders Mac Lane), but to understand the purity and grace behind monads in functional programming, "No knowledge of category theory is assumed." (from ((652a3071-e1c9-40db-a7fc-9ed8c2d9c3aa)) by Philip Wadler) in the beginning.
- Learning functional programming is essential for understanding how we can hacking Lean in Lean. Manipulating states, handling errors, write functions which traverse or do recursions on expressions, and other more operations are daily works when doing meta programming in Lean. Besides, the meta programming APIs of Lean are *monadic*, so it would be better to understanding how monadic programming works first.
- It is worth to mention that meta programming in Lean is not only useful and capable for generate Lean code, but also powerful enough to improve the experiences of interactive theorem proving. There already exists some libraries had done such works, from the simple one just providing more friendly error messages, to the complex one that let user to specify what interactive options to choose next, edit the code dynamically and so on. Other experiments shows that we can also fully exploit the power of the meta programming APIs for Lean, to translate different kind of visual graphs to Lean code (dynamically), and back. What's more, auto theorem proving is also a famous result of tactics, the APIs provide a way to visualize the method of solving problems step by step with generated figures and descriptions. We hope to see such work appear and stable in the future. Another successful application is using the APIs to build different kind of DSLs, from the one improving the process of programming to the one simplify the steps of stating and proving theorems.
- Other references textbooks:
	- [*Programming Language Foundations in Agda*](https://plfa.github.io)
	- [*Functional Programming in Lean*](https://lean-lang.org/functional_programming_in_lean/title.html)
	- [*Metaprogramming in Lean4*](https://github.com/leanprover-community/lean4-metaprogramming-book)
- Other reference papers:
	- [*Functional programming with bananas, lenses, envelopes and barbed wire*](https://maartenfokkinga.github.io/utwente/mmf91m.pdf)
	  id:: 652a2f6a-50d6-44c6-bfe6-38a043e4ab4e
	- [*Comprehending monads*](https://homepages.inf.ed.ac.uk/wadler/topics/monads.html)
	  id:: 652a3071-e1c9-40db-a7fc-9ed8c2d9c3aa
	- [*Data types à la carte*](https://www.cambridge.org/core/journals/journal-of-functional-programming/article/data-types-a-la-carte/14416CB20C4637164EA9F77097909409)
	- [*Design patterns for parser combinators*](https://dl.acm.org/doi/10.1145/3471874.3472984)
	- [*Use and abuse of instance parameters in the Lean mathematical library*](https://arxiv.org/abs/2202.01629)
- Other reference web resources:
	- [*Every foldl is a foldr.*](https://stackoverflow.com/a/26036320)
	- [*The inverse of a bijection.*](https://xenaproject.wordpress.com/2019/06/11/the-inverse-of-a-bijection/)
	- [*The great crusade against TCM*](https://github.com/agda/agda/pull/3589)
	- [*Lean verbose: Very controlled natural language tactics for Lean*](https://github.com/PatrickMassot/lean-verbose)
- All exercises:
	- [[Please finish the exercises in the referred code above.]]
	  id:: 652ada79-8e66-4c41-a778-6fcf21c3d9b2
- ## Functional Programming in Lean
	- [[Transformations between Terms and Tactics, and More on The Syntax of Lean]]
	- [[Playing with Nat, List and Error Types]]
	- [[Binding the Monadic Computations]]
	- [[Joining the Monadic Comprehensions]]
	- [[More Monads and Monad Transformers]]
- ## Meta Programming in Lean
	- [[Monadic Meta Programming APIs]]
	- [[Expr]]
	- [[Syntax]]
- ## More Notes on Lean
	- [[Design Patterns for Typeclasses]]
	- [[Hierarchy of Universes]]
	- [[Proof Irrelevance and Subsingleton Elimination]]
	- [[Non-compute Axioms and Tactics]]
	- [[Quotient, Subtypes and More on Typeclasses]]
