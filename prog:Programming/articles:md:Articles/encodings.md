# Information Encoding
*A High Level Overview*

**Navaz Alani**, *Apr 16 2020*
****

This document aims to understand what file encodings are, why they are important and
how applications use them. Let's get started.

## What are Encodings?

Surely, most of us have heard that computers process ones and zeroes. And at the lowest
level, that is very true. Information is stored in binary and this is what the CPU deals
with. The reason behind this goes into physics and hardware and is pretty interesting to
learn about, but that's not the point of this document.

Keeping this fact in mind, a big question arises. How does one express a word document,
powerpoint presentation, music files, videos or virtually any information in binary for
the CPU to deal with? The answer is not a universal one which works for all files.

## Text Encoding

Let's start off simple and begin by focusing on `.txt` i.e. text files. And for even more
simplicity, let's assume we are only dealing with characters of the Englsh alphabet (a-z, 
A-Z, 0-9, punctuations and symbols). How would one go about unambiguously expressing such
a text file into binary?

Well, a simple way would be to list out the characters we have to deal with and assign a
binary value to each of them. Then, when encoding the file into binary, we use the assigned
binary value in place of the character. This works but it's 90% of the answer.

Say we just want to encode the first 10 lowercase English characters.
When counting from 1 to 10 in binary, the length of the binary representation changes...
1 is just `1` and 10 is `1010`. So if we assigned `a` (1st letter) to `1` and `j` (10th
letter) to `1010`, the string `aj` would be encoded as `11010`. This is problematic! Where
does one break this binary representation to get back the origial text? If I break it up as
`110` and `10` (`6` and `2`), this would translate to `fb` (f->6th letter and b->2nd 
letter) which is far from the original text `aj`. 

So, to solve this, we can use blocks of a certain length (4 is adequate for this case).
Therefore, we write 1 as `0001` instead of `1`. After this modification, `aj` is now
encoded as `00011010`. To get the text representation back, we break this binary
representation into blocks of length 4 and convert them back to their respective characters.
So `00011010` breaks up to be `0001` and `1010` which gives us back `aj`! Great, we have
come up a very simple encoding which works for the first 10 lowercase characters of the
English alphabet.

## Standardizing Encodings

But wait, there's another issue. If you had to do the same thing at home, the chances are
that you would come up with a different encoding from someone else doing the same activity.
If you decide that `a` is `0001` but someone else decides to encode the characters in
reverse order, `a` for them could be `1010`! So if you encode and send that person a
message, it will probably be jibberish for them.

Turns out, this is the same problem faced in the early days of computing in the US.
Different encodings are a pain to deal with so a committee decided to standardize an
encoding for the set of characters which were being used back then. The encoding that
they came up was called ASCII (American Standard Code for Information Interchange)
and it is still being used today (to some extent).

ASCII works for a total 128 characters, so the minimum required block width is 7
(`2^7=128`). But computers deal in binary, so powers of two. The closest power of two to 7
is 8. So ASCII uses blocks of length 8. You can see below that the first number in each
binary block is `0`.

Therefore, using ASCII, we the string `hello world` is encoded as:
`0110100001100101011011000110110001101111001000000111011101101111011100100110110001100100`.
But this looks ugly, so we break it up into blocks of 8:
`01101000 01100101 01101100 01101100 01101111 00100000 01110111 01101111 01110010 01101100
01100100`,
from which it is clearly visible that:

```rb
01101000 => 'h'
01100101 => 'e'
01101100 => 'l'
01101100 => 'l'
01101111 => '0'
00100000 => ' '
01110111 => 'w'
01101111 => 'o'
01110010 => 'r'
01101100 => 'l'
01100100 => 'd'
```

This can also be seen if the string `hello world` were saved to a text file. The final
sequence `00001010` (10) is the newline character, equivalent to pressing 'Return' or 
'Enter'.

```bash
# save string into file.txt
$ echo "hello world" > file.txt
# view the binary data stored in file.txt
$ xxd -b file.txt
01101000 01100101 01101100 01101100 01101111 00100000  hello 
01110111 01101111 01110010 01101100 01100100 00001010  world.
```

So now you know about basic text encoding! But what about characters in other languages,
emojis and all of that fun stuff? Well with the rise of the internet, this did become a
problem because different countries would have their own encodings and as we have
seen, this leads to jibberish. So the Unicode Consortium was formed and they came up with
the UTF-8 encoding. This encoding is international and handles each character in most modern
languages (oh, and emojis too). Check out the 
[Unicode Consortium](https://home.unicode.org/) 
for more details on UTF-8 and their great work!

## Application/File Specific Encodings

So we have covered how to encode plain text but the problem is that not all information is
plain text. A word document is not plain text - it includes information on how the
document is formatted, images and much more. Music files (`.mp3` and so on) encode audio by
describing sound through mathematics.

As you can see, different formats require different encodings. Microsoft Word understands
how to interpret binary information describing a word document. A music player is suited to
interpret binary data describing sound. If you try to open a word document or a music file
using a text editor (like Notepad or Sublime Text), all you see is jibberish. The editor
attempts to interpret the binary data as text but it isn't.
