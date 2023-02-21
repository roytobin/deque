## Deque Testbench

A simple stimulus pattern generator to test a scheme implementation of
what SICP[^1] calls a "deque."

>Exercise 3.23
>A deque ("double-ended queue") is a sequence in which items can be inserted
>and deleted at either the front or the rear.  Operations on deques are the construc-
>tor make-deque, the predicate empty-deque?, selectors front-deque and
>rear-deque, and mutators front-insert-deque!, rear-insert-deque!,
>front-delete-deque!, and rear-delete-deque!.  Show how to represent
>deques using pairs, and give implementations of the operations.  All operations
>should be accomplished in O(1) steps.

### Restrictions and Caveats
For the stimulus to perform correctly, the implementation under test (IUT)
must have the feature/bug that a delete from an already-empty deque is a
"no operation."  Previous queue examples in the SICP text have the logic
that an attempted delete from an empty queue is an error.  If the IUT has
this same logic, it must be temporarily modified for the stimulus to work.

### Approach
The stimulus generator creates a random pattern of deque insertions and
deletions that ebb and flow according to a sine wave to variously fill
and completely drain the deque.  To see this pattern:  `dqbench | grep the`
Randomly sprinkled within the insertions and deletions are queries to
the state of the deque.  If ever the expected response does not match the
actual response, an error message is generated.  A successful test will
have no output (i.e. no error messages to be seen).

### Verification
The testbench was verified using these scheme implementations
1. s9 Scheme 9 from Empty Space by Nils M Holm, 2018-12-05
2. mit-scheme  Release 10.1.11 || Microcode 15.3 || Runtime 15.7 
3. racket v7.9 [bc]

### See Also
http://community.schemewiki.org/?sicp-ex-3.23

[^1] *Structure and Interpretation of Computer Programs* by Harold Abelson et al. 1996

