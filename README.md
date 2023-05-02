Download Link: https://assignmentchef.com/product/solved-cop3252-project-4
<br>
This assignment should give you practice with accessing the file system using the Java File class as well as the basics of using input/output streams. It will also give you more practice with command line arguments and some practice formatting dates.

<h1>Task</h1>

Write a file viewer that allows you to view file information, view directory structure, read text files, and copy files. Your main program should be run from the file:

<ul>

 <li>FileViewer.java</li>

</ul>

You should not <strong>need </strong>any other files or classes, but you may create them if you wish.

<strong>Each file should have a comment including your name at the top of the file. Each file should also have appropriate comments throughout.</strong>

<h1>Requirements</h1>

<ol>

 <li><strong>Command Line Options: </strong>Your program should accept the following command line options:

  <ul>

   <li>“-i” (for (i)nformation) with an optional file or directory as a 2nd parameter. If no 2nd parameter is passed, default to the current directory “.”</li>

   <li>“-v” (for (v)iew) with a file to view as the 2nd parameter</li>

   <li>“-c” (for (c)opy) with a sourcefile as the 2nd parameter and a destination file as the 3rd parameter</li>

   <li>If no parameters are passed, then the program should default to displaying information on the current directory (as if the user had passed “-i .”)</li>

  </ul></li>

</ol>

If the command is invalid usage (illegal options), print a usage message, as below, then exit the program:

Usage : java −jar hw4. jar [−i [<em>&lt;</em>file <em>&gt;</em>|<em>&lt;</em>directory <em>&gt;</em>]|−v <em>&lt;</em>file <em>&gt;</em>|−c <em>&lt;</em>sourceFile<em>&gt;&lt;</em>destFile <em>&gt;</em>]

Since that text has to be small to fit on the line, I’ll break it up into multiple lines here (make sure you print it all on one line in your code):

Usage: java -jar hw4.jar

[-i [&lt;file&gt;|&lt;directory&gt;]|-v &lt;file&gt;|-c &lt;sourceFile&gt; &lt;destFile&gt;]

<ol start="2">

 <li><strong>Information: </strong>When the user requests information using the “-i” option, they may pass a 2nd parameter indicating the file or directory they wish information on. This is handled in different ways, depending on whether it is a file or directory. If it is a file:

  <ul>

   <li>Print the absolute path to the file</li>

   <li>Indicate whether the file can be executed</li>

   <li>Print out the file size in bytes</li>

   <li>Print out the last modified date of the file</li>

   <li>Your output should match mine exactly (see the example output for the exact format)</li>

  </ul></li>

</ol>

However, if it is a directory:

<ul>

 <li>Print a heading indicating that you are printing size followed by filename</li>

 <li>Print each file/directory contained in the directory being viewed</li>

 <li>For each file that you are printing, print the size, followed by the filename</li>

 <li>For directories, print the size as *</li>

 <li>Sort the files by filesize (lowest to highest)</li>

 <li>See example output for details</li>

</ul>

If the 2nd parameter is not a regular file or directory, print the error message:

”Error: Invalid File”

<ol start="3">

 <li><strong>View: </strong>If the user requests to view a file, the 2nd parameter should be a regular file. If the file is not found, print an appropriate error message. You should then print the contents of the file, as text, to the screen. Remember to handle all exceptions you encounter.</li>

 <li><strong>Copy: </strong>If the user requests to copy a file, the 2nd parameter should be the name of a regular file (the source file) and the 3rd parameter should be the name of the file to copy to (the destination file). If the destination file already exists, do not make the copy and print an appropriate error message. If the source file is not valid, print an appropriate error message. Then you should copy the information from the source file to the destination file, handling any exceptions encountered appropriately. After this, print a message to the user stating that the copy was successful. Please note that you should be able to copy binary files with this method, not just text files.</li>

 <li><strong>Other Requirements:</strong>

  <ul>

   <li>Make sure you handle all exceptions that could be thrown when dealing with the file I/O</li>

   <li>When printing error messages to the user, you do not have to match my format exactly (although it is preferred)</li>

   <li>For all other output, match my format and text exactly</li>

  </ul></li>

 <li><strong>Extra Credit: </strong>You may earn extra credit on this assignment by allowing the user to specify an additional command-line option: ”-d” for compare (d)ifferences in files. This option should take 2 more parameters, both of which should be files. It should compare the two files and print a message indicating whether they are the same. As in the other options, handle exceptions. Please note that this changes the usage message. The new usage message is as follows (Please note this is on multiple lines, but your actual message should all print on the same line)</li>

</ol>

Usage: java -jar hw4.jar [-i [&lt;file&gt;|&lt;directory&gt;]| -v &lt;file&gt;|-c &lt;sourceFile&gt; &lt;destFile&gt;|-d &lt;file1&gt; &lt;file2&gt;]

<ol start="7">

 <li><strong>Hints:</strong>

  <ul>

   <li>Remember that file sizes are returned via the length() function and are of type long (which can be converted to type Long using a class method of class Long – This can be very useful when attempting to sort)</li>

   <li>You can print the last modified date using the Java Date class along with a SimpleDateFormat class (<a href="https://docs.oracle.com/javase/tutorial/i18n/format/simpleDateFormat.html">this is a good place to start</a><a href="https://docs.oracle.com/javase/tutorial/i18n/format/simpleDateFormat.html">)</a></li>

   <li>You could also print the last modified date using printf. Look at the Formatter class for a detailed listing of the date/time flags. Remember to use the ”<em>&lt;</em>” flag as well to keep using the same parameter (so you don’t have to pass the date in multiple times). As an example:</li>

  </ul></li>

</ol>

System.out.printf(“%b %&lt;d %&lt;Y”, date)

would print out

Jan 31 2016

if the variable date was a long integer representing the date Jan 31, 2016.

<ul>

 <li>The display option only has to handle text files, all other options should handle binary files as well (so use the appropriate streams).</li>

 <li>You may use exit(0) to exit the program at any time</li>

 <li>Make sure you handle all invalid commands (including too many command-line parameters)</li>

</ul>

<strong>Some Helpful Classes/Methods</strong>

<ul>

 <li>equals(Object)</li>

 <li>charAt(int)</li>

 <li>File class</li>

 <li>sort(T[], Comparator)</li>

 <li>Comparator Interface</li>

 <li>Date(long)</li>

 <li>format(Date)</li>

 <li>valueOf(long)</li>

</ul>

<h1>Sample Output</h1>

(This example has the extra credit implemented)

(commands are underlined)

(these commands were all issued in order in the same directory)

<u>java -jar hw4.jar </u>Size Filename

26                manifest.mf

767                 FileViewer$1.class

1018 aTextFile

1018 aCopyOfATextFile

*                sol

6261 FileViewer.class

6683 hw4.jar 7140 FileViewer.java

<u>java -jar hw4.jar -i ˜/cop3252/</u>

Size Filename

<ul>

 <li>another</li>

 <li>classExamples</li>

 <li>hw</li>

 <li>exams</li>

 <li>lec</li>

 <li>cpdj</li>

</ul>

<u>java -jar hw4.jar -i aTextFile</u>

File Path: /home/grads/thrasher/cop3252/hw/hw4/aTextFile

Is executable? false

Size: 1018 bytes

Last Modified Date: Wed Nov 23 15:36:21

<u>java -jar hw4.jar -v aTextFile </u>“Jabberwocky”

’Twas brillig, and the slithy toves

Did gyre and gimble in the wabe;

All mimsy were the borogoves, And the mome raths outgrabe.

“Beware the Jabberwock, my son!

The jaws that bite, the claws that catch!

Beware the Jubjub bird, and shun The frumious Bandersnatch!”

He took his vorpal sword in hand:

Long time the manxome foe he sought

So rested he by the Tumtum tree, And stood awhile in thought.

And as in uffish thought he stood,

The Jabberwock, with eyes of flame, Came whiffling through the tulgey wood, And burbled as it came!

One, two! One, two! and through and through The vorpal blade went snicker-snack!

He left it dead, and with its head He went galumphing back.

“And hast thou slain the Jabberwock?

Come to my arms, my beamish boy! O frabjous day! Callooh! Callay!” He chortled in his joy.

’Twas brillig, and the slithy toves

Did gyre and gimble in the wabe;

All mimsy were the borogoves, And the mome raths outgrabe. — from Through the Looking-Glass, and What Alice Found There (1871)

<u>java -jar hw4.jar -c aTextFile aCopyOfATextFile </u>File aCopyOfATextFile already exists. <u>rm aCopyOfATextFile</u>

<u>java -jar hw4.jar -c aTextFile aCopyOfATextFile</u>

File aTextFile was copied to file aCopyOfATextFile successfully.

<u>java -jar hw4.jar -d aTextFile aCopyOfATextFile</u>

The two files aTextFile and aCopyOfATextFile are the same.

<u>java -jar hw4.jar -d aTextFile FileViewer.class</u>

The two files aTextFile and FileViewer.class are not the same.

<u>java -jar hw4.jar -q</u>

Usage: java -jar hw4.jar [-i [&lt;file&gt;|&lt;directory&gt;]|-v &lt;file&gt;|-c &lt;sourceFile&gt; &lt;dest