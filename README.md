## Function:

  Remove duplicated words  
  Sort words  
  Export normalized case words to output file, one word per line 

## Parameters:

	the name of an input file
	format specifier (T for text and B for binary)
	the name of an output file 

## Requirements:

	for the T variant:
    a text file with keywords
    the list is in random order
    there can be duplicates (and keywords that differ only in letter case are considered duplicate)
    each line is a comma-separated list of keywords
    there can be up to tens of thousands of keywords in the file

    for the B variant, the input is:
    4 bytes big-endian: number of keywords N
    N entries of 2 bytes each: big-endian length of each keyword in bytes
    Keywords, UTF-8 encoded, without any terminating byte, lengths specified in the preceding table
    25 bytes in total
    writes into the output file a sorted list of the keywords, , 
    with duplicates eliminated and 
    indicates success or failure so that an automated batch process can react to it

## Expected input:

	(case Binary) if there are 3 keyword (apple, pear, orange), 
  the input file will look like this:
  00 00 00 03 00 05 00 04 00 06 a p p l e p e a r o r a n g e

	(case Text)the input file will look like this:
	orange, pear, apple, pear
    red, green, blue,  green, orange,
    Samsung,,Apple,LG

## Expected output:
	apple
	blue
	green
	lg
	orange
	pear
	red
	samsung
