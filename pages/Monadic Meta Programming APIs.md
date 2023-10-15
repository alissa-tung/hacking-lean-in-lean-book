public:: true

- ## How Does `exact` work, Exactly?
	- The tactic `exact x` closes the main goal if its target type matches that of `x`.
	  id:: 652aa946-5d4d-41a0-a5de-971c75c41b17
	- Consider the code example in `HackingLeanInLeanSrc/PartII/Exact.lean`:
		- the code `syntax (name := exact') "exact' " term : tactic`
			- Defines a parser named `exact'`
			- The parser will parse string of the form, a literal name `exact'`, than one or more spaces, than one any term (although we have not explain what `term` is yet)
			- `: tactic` states that the parser we define will produce a value of the syntax category `tactic` once the parser succeed
		- the attribute `@[tactic exact']`
			- States that we have a function with the type signature `Tactic` implements a tactic named `exact'`
			- The type `Tactic` is an abbreviation of the function type `Syntax → TacticM Unit`, hence we can say a tactic is essentially a function that consume a `Syntax` object, and do something. And the concrete things they are expected to do and what they can do will be introduced latter.
	- The concrete and complete define of a tactic is not very scary! Apart from the syntax parser definition and the tactic implementation attribute is a normal function that consume a `Syntax` object and do something. Let's look closer to the function `def evalExact'`
		- Recall that the type `Tactic` is an abbreviation of the function type `Syntax → TacticM Unit`, so we can use lambda to define a function. The `stx` been matched is a value of the type `Syntax`.
		- It would be quite annoying to write the original `Syntax` constructor structure out in the match arm, since `Syntax` is a very complex inductive type and not easy to use. We use the "syntax pattern" ```(tactic| exact' $e)`` here to reduce the complexity. More details on constructing syntax objects will be covered in the [[Syntax]] chapter.
		- Recalls that ((652aa946-5d4d-41a0-a5de-971c75c41b17)), so the main job is done by the function `closeMainGoalUsing`. The name `using` and the type of this function suggests that the function mainly takes a argument of the type `Expr → TacticM Expr`, that is, the function created their by a lambda `fun type => do ...`.
		- We can ignore some details for now, since implementation details is not the main topic here. Consider the function `fun type => do ...`
			- in the match arm, the syntax pattern ```(tactic| exact' $e)`` binds a variable `e`, like any normal pattern matching, but with a prefix `$`
				- the `e` here is a typed syntax object, that is, ``e : TSyntax `term``, as we stated in the parser, and binds out in the match arm
				- (formally, but not need to understand now) the `elabTermEnsuringType e type` "elaborate" `e` in the current `MVarContext`. If given, the expected type will be used to help elaboration and then a `TypeMismatchError` will be thrown if the elaborated type doesn't match.
		- So we can say simply, the function `evalExact'` first states it only consider the case when calling the tactic `exact'`, otherwise throw an error. Then ensure the term we want to use in `exact'` is exactly of the type "unified" with the current main goal, otherwise throw some errors.
		- But what is elaborate, what is unify, what is `MVarContext`, what is elaboration here? And why a tactic is essentially a function from `Syntax` to `TacticM Unit` (plus its parser)? To answer these questions, we are going to say a little about some of the primary steps involved in the Lean type checking process, and introduce the Monadic Meta Programming APIs of Lean.
		- [[Please finish the exercises in the referred code above.]]
- ## About the Lean Internal
- ## The Monads and APIs