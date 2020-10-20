# HW2: Procedural Python

**0. Download the 20 Newsgroups dataset and unarchive/unzip the folder.**

Dataset location: http://qwone.com/~jason/20Newsgroups/20news-19997.tar.gz

**1. Create a function `check_email_validity` that takes a single argument, a text string, and returns a boolean value. Return true if a valid email, false else.**

- [ ] Correct logic for email validity using Python string methods and/or lists (regular expressions, e.g. `re`, not allowed for this assignment) [2pts].

An email is a string (a subset of ASCII characters) separated into two parts by @ symbol. Let's call the first part *personal* and the latter part *domain*, i.e., personal@domain. The length of the personal part may be up to 64 characters long and domain name may be up to 253 characters.

The personal and domain parts contains the following ASCII characters:

- Uppercase (`A-Z`) and lowercase (`a-z`) English letters.
- Digits (`0-9`).
- Character `-` (dash).
- Character `.` (period, dot or fullstop) provided that it is not the first or last character and it will not come one after the other.

Additionally, the personal part can contain:

- Characters `! # $ % & ' * + / = ? ^ _ { | } ~`

Example of valid emails:

    mysite@ourearth.com
    my.ownsite@ourearth.org
    mysite@you.me.net

Example of invalid emails:

    mysite.ourearth.com [@ is not present]
    mysite@.com.my [domain can not start with dot "."]
    @you.me.net [No character before @]
    mysite123@gmail.b [".b" is not a valid tld]
    mysite@.org.org [domain can not start with dot "."]
    .mysite@mysite.org [an email should not be start with "."]
    mysite()*@gmail.com [here the regular expression only allows character, digit, underscore, and dash]
    mysite..1234@yahoo.com [double dots are not allowed]

**2. Create a function `process_newsgroup_file` that takes two arguments, a file path string and a dictionary with words as keys and integers as values that does the following:**

The function should return a tuple with two elements:
- [ ] the validated (using function from #1) email address after the 'From:' header [1pt]
- [ ] number of lines that contain quotes (start with `>`, nested quotes still count as a single quote) [1pt]

The function should also perform the following:
- [ ] remove special characters and punctuation (anything outside of A-Z, a-z, 0-9) from non-header lines. This is a common preprocessing step for text processing. [1pt]
- [ ] increment the passed in dictionary with word counts (words as keys and integers as values) based on what's contained in the passed file [2pt]

**3. For each file in the cryptography topic, run the `process_newsgroup_file` function and pass in the growing dictionary along with filenames.**

Use the following code to get started:

    word_list = {}

    import glob
    files = glob.glob("20_newsgroups/sci.crypt/*")  # adjust filepath as needed
