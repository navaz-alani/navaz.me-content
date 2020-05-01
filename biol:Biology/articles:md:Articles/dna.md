# DNA
*Notes on DNA [Structure](#structure), [Replication](#replication), [Transcription](#transcription) and [Translation](#translation)*

**Navaz Alani**, *1 May 2020*
****

## Introduction

As a programmer, I tend to be fascinated by the incredible encoding that is the DNA. It is basically
a recipe for creating the materials and systems needed for a living organism to function. The DNA
encodes these instructions using a basic instruction set containing 4 basic instructions. Of course,
this is all represented, parsed and executed chemically.

It's impressive how there is an abstraction that can be drawn between how the body reads and
executes the instructions encoded within DNA and how computer programs are parsed and executed by
the CPU. While learning about the DNA, I learnt by connecting these molecular processes to the
abstraction of source code compilation and execution that I was already aware of and I believe that
this made it easier for me to understand these processes __*at a high level*__. If you would like
to get a high level overview of compilation, check out my work on
["The Essence of Programming Languages".](
/content/prog/articles/programmingLanguagesConcept?ttl=The%20Essence%20of%20Programming%20Languages)

This document attempts at a high level overview of the structure of DNA, how it is replicated so that
cells can duplicate, parsing and transcompiling of mini-recipes contained within the DNA molecule
(transcription) and finally execution of these transcompiled versions to create proteins (translation).

In general, I have found it to be helpful to think of proteins as molecular machines which serve a
particular purpose. In programming terms, they are tiny programs which perform a certain function.
Using this abstraction, the high level process seems to follow the Unix philosophy of software design
as well, specifically *"Write programs that do one thing and do it well. Write programs to work together. Write programs to handle text streams, because that is a universal interface."*

* Programs that do one thing, and do it well -> analogous to proteins
* Programs that work together -> analous to many processes e.g. how RNA polymerase works hand in hand
with DNA polymerase during replication
* Write programs to handle text streams -> analogous to the the stream of nitrogenous bases encoded
in DNA

The Unix philosophy, probably developed without any knowledge of biological systems, seems to have
converged to the way that biological systems actually work, in an abstract sense.

Finally, before starting, I will assume basic knowledge of chemical bonding- which can be considered
as the glue at the molecular level (yet another abstraction).

DNA stands for "deoxyribonucleic acid". It lies in one of the 4 major categories of biological
molecules:

* Proteins
* Lipids
* Carbohydrates
* Nucleic acids `<- this is where DNA lies`

## <a name="structure"/>Structure

1. In humans, there are 46 chromosomes, each containing 1 DNA molecule
2. Structurally, DNA is a polymer (made up of many smaller repeating molecular units)
	* In the case of DNA, these molecular units are called __nucleotides__
	* Nucleotides linked together are called __polynucleotides__
3. A nucleotide has 3 main components:
	1. A 5-Carbon sugar molecule (called deoxyribose- this is where the `deoxyribo-` part in DNA
	comes from)
	2. A Phosphate group
	3. One of 4 nitrigenous bases
		* Adenine (A)
		* Thymine (T)
		* Guanine (G)
		* Cytosine (C)
4. In living organisms, DNA doesn't exist as a single polynucleotide molecule/strand, but rather as
a pair of strands held together in the famous __double helix__ fashion by hydrogen bonds between the
bases.
5. The backbone of each polynucleotide strand is formed from the sugar molecules and phosphate groups
	* These sugar-phosphate bonds run down each side of the double helix- chemically, in opposite
	directions.
	* One strand begins at the top, with the first phosphate connected to the sugar molecule's 5th
	carbon and runs down the strand. It ends where the next phosphate would go, with a free end at
	the sugar's 3rd carbon. This is known as the 5' (5 prime) to 3' (3 prime) pattern (`[5'-->3']`
	direction).
	* The other strand runs, chemically, in the opposite `[3'-->5']` direction
6. The two strands are linked together via the nitrogenous bases
	1. The nitrogenous bases have their respecitve counterparts
		* Adenine's counterpart is Thymine (and vice versa) -> `AT` (or `TA`) pairing
		* Guanine's counterpart is Cytosine (and vice versa) -> `GC` (or `CG`) pairing
	2. Bonded nitrogenous bases are called __base pairs__
	3. The `GC` pairing is slightly stronger than the `AT` pairing because they are respecively
	bonded by 3 and 2 hydrogen bonds
	4. If given a polynucleotide strand sequence, the complementary strand sequence should now be
	obvious. Given `5'-AGGTCCG-3'`, the complementary sequence will be `3'-TCCAGGC-5'`.

### RNA vs DNA

RNA stands for ribonucleic acid. It is similar to DNA, except for the three main differences:

1. RNA is single stranded
2. The sugar in RNA is ribose, which has one more oxygen (hence the `ribo-` in RNA)
3. In RNA, thymine is replaced with uracil (U)

## <a name="replication"/>Replication

### Programming Abstraction

Thinking of this programatically, the program to implement performs DNA Replication. Keeping in
mind that proteins are basically the tiny programs that do one thing, and do it well (from the Unix
philosophy), we can understand replication by first thinking of how one would program it based on
the structure of DNA above.

* Since there are 2 polynucleotide strands and one is complementary to the other, this means that
2 copies of the DNA can be created, using each of these strands as "templates".
* In order to use the two strands as templates, one has to first split the DNA molecule. One can
envision a small program (protein) which performs this, and only this.
* Then, once the two template strands are split, it is pretty easy to assemble a complementary
polynucleotide strand for this because each nucleic acid has only one counterpart and the backbone
must be in the opposite direction to the template strand. One can also envision a small program
to perform this "template completion" (in the actual replication process, this is achieved by two
smaller programs (proteins) working hand in hand).
* Finally, some cleanup needs to be done. This is like garbage collection or freeing memory in a
program.

### Biological Process

At a _very_ high level the process is as follows:

1. An enzyme (a specialized protein) called __helicase__ unzips the DNA molecule into the
two polynucleotide strands which can be used as template strands. The strand which runs in the
`[5'-->3']` direction is called the __leading strand__ and complementarily, the strand which runs
in the `[3'-->5']` direction is called the __lagging strand__ (for reasons which will soon become
apparent).
2. What remains is creating two complementary polynucleotide strands from the template strands.
This is where the process forks because the templates run in opposite directions, chemically. The
issue is that the enzyme which adds nucleotides onto the template strand, called DNA polymerase 3,
can only work in the `[5'-->3']` direction because it _latches_ onto the `3'` end. This brings in
another issue: DNA polymerase 3 needs to latch onto the `3'` end in order to work, but there is no
such site available on any of the template strands- so it needs to be created.

This is where we see two enzymes working together in order to create the complementary strands.
Firstly, an enzyme called RNA primase (important! we'll come back to this point) primes the
strand by adding a short length of RNA onto by base pairing with the the template strand. This
makes it possible for the DNA polymerase to latch onto the `3'` end of the primer provided by RNA
primase and continue down the molecule.

* The leading strand is easy to deal with- RNA primase has to prime the strand only once at the
beginning and DNA polymerase can keep adding nucleotides in the `[5'-->3']` direction until the
end of the strand.
* The lagging strand requires more work- since it runs in opposite the direction in which DNA
polymerase works, it has to be copied in segments (called __Okazaki fragments__). For each segment,
RNA primase primes the beginning of the segment and DNA polymerase works the segment in the opposite
direction.

The process isn't done yet. At this point, we have two strands which are just a few steps away
from being valid DNA. Some cleanup is required! The enzyme RNA primase is also called DNA primase in
some cases, but I chose to call it RNA primase because it's closer to what it actually does. It
primes the strand by adding RNA to it, not DNA. So, if you remember, RNA actually has a different
sugar in its structure compare to DNA and Thymine is replaced with Uracil. This needs to be
rectified.

Another enzyme called DNA polymerase 1 replaces the RNA primer with DNA. However, this process
leaves a little nick in the region that was replaced. It needs to be bonded with the surrounding
nucleotides and this is done by another enzyme called DNA ligase which completes the sugar-phosphate
bonds in the strand (the nicks that were left). After these two enzymes have cleaned up, the DNA
replication is finally complete!

This cleanup process has to happen only once for the leading strand (because RNA primase provided
a primer once at the beginning of the strand) and multiple times (depending on the number of Okazaki
fragments) on the lagging strand. This is why the lagging strand is called so- it lags behind in the
replication process.

## <a name="transcription"/>Transcription

	todo

## <a name="translation"/>Translation

	todo
