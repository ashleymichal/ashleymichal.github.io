---
layout: post
title: Roadblock
---

13:57 - Yesterday things got frustrating.  I shouldn't be surprised.  It's not an easy thing.  But the Caesar cipher... it's not that hard to implement, really.  I just think that the way I've done it is shitty.  I can't tell whether it is more productive to keep banging my head against the wall, or look at other solutions to identify ideas I didn't have.

I think I just answered that question....

One nice solution was to use % 26 to keep the shift point inside the alphabet.  This is clever, it works not only on numbers > 26, but also negative numbers.  I wonder if it can be implemented not only in the shift factor, but in the shifted number to loop around again?
Really just maintaining case has been the hardest part, because it feels like as soon as you do that, you're either repeating code or calling the same sub-routine again.  Which is fine, if you do the second one.
That person's solution sort of forgot that if the shift point was > 8, and the letter was lowercase, it could still accidentally get pushed into not only the wrong letter, but made uppercase.

Then there's the n.times `{ shift one }` approach, which again works, but seems not so elegant.

I like this one the best:

```ruby
def caesar_cypher(string, shiftnum = 0)    
    outstring = ''
    string.each_byte do |x|
        a = x
        if a == ' '.sum
            outstring+= a.chr
        elsif a <= 'Z'.sum
            b = ((a - 'A'.sum + shiftnum) % 26) + 'A'.sum
            outstring += b.chr
        else
            b = ((a - 'a'.sum + shiftnum) % 26) + 'a'.sum
            outstring += b.chr
        end
    end
	 return outstring
end
```

it still repeats, but it seems to be the most clever use of the underlying values, and the use of each_byte is nice and clean as opposed to #unpack and #pack

19:21 - I had to move on from Caesar Cipher to Stock Picker and Substrings.  These went way better.  Just for the record, future you, today got way better.  And then I went back with a cooler mind and re-did Caesar Cipher based on what I learned and what I had read from other people's solutions.  It seems that I could use work on strings, and that I'm not a hundred percent sure how to utilize regular expressions.  We'll get there though.