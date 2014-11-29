Java-Evil-HangMan
=================

The program makes use of the HashMap and Set classes to simulate the Hangman game.

In the ordinary game of Hangman, the opponent (computer) chooses a word and te
lls you
how many letters it contains. Then you guess a letter. If the letter is in the word, the
opponent shows you where. If not, you pay a penalty, i.e. your "hangman" has an
additional body part drawn. If you guess the word before your hangman is co
mplete, you
win. Otherwise, you lose. (For a simplified interface, the hangman drawing can be
replaced by a simple counter of wrong guesses.)
Here is an example, using the word "goal" and assuming that if you guess 5 wrong letters,
you lose.
The word i
s: _ _ _ _
Guess a letter: e
Sorry, there is no e. You have 4 wrong guesses left.
The word is _ _ _ _
You have guessed: e
Guess a letter: o
Yes, there is 1 o.
The word is _ o _ _
You have guessed: e o
Guess a letter
(and so on)
Your task is to bui
ld a computer player that cheats! While in the usual game of
Hangman, the word remains the same throughout the game, in Evil Hangman, the
computer does not have a chosen word at all, but always gives the response that leaves
the most possible words.
For
example, suppose the dictionary is
act, bat,
baa, bet,
bit, bun, but, cat, can, mat, man, men, tin
The computer's word starts at _ _ _
The player guesses
the letter "a"
The computer needs to consider several options:
•
Words with no "a": bet, bit
, bun, but, men, tin (6)
•
Words with a _ _ : act
•
Words with _ a _ : bat, cat, can, mat, man (5)
•
Words with _ a a : baa (1) <
-
note that both a's are revealed at once, so this word
is not in _ a _ or _ _ a.

Since the largest set of words goes with _ _ _
, the computer answers _ _ _ and game play
continues. Only words without a's can be considered now.
The player guesses the letter "t"
Options are:
•
No "t": bun, men (2)
•
t _ _ : tin (1)
•
_ _ t: bet, bit, but (3)
So the computer responds _ _ t
Now, yo
u guess e
Options are:
•
No e: bit, but (2)
•
_ e
_ : bet (1)
So the computer responds _ _ t again, and the game continues
Essentially, the program starts with a set of available words of the appropriate length.
When a letter is guessed, the set must be broken into non
-
overlapping subsets, one for
each possible pattern of where the letter can be found and one for words that do not
contain the letter. Whichever set is largest is chosen. That is the new set of available
words, and the proper pattern of dashes and letter
s so far is returned to the user. Keeping
the set of possible words as large as possible makes it difficult for the other player