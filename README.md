Download Link: https://assignmentchef.com/product/solved-nwen241-assignment-1-text-editor-2
<br>
A <strong>text editor </strong>is a systems program that facilitates the creation and modification of files that contain strings of characters.

In this assignment, you will implement several basic text editor operations such as insert, delete, replace, etc. You will implement some of the operations in pure C (Part I), and some in C++ (Part II). In Part III, you will be asked to design another subsystem of a text editor program using C++.

You only need to submit the required implementations. You do not need to write a main() function, but you would need one if you want to test your code. In any case, do not submit code with the main() function.

Full marks is 100.

<strong>Instructions and Submission Guidelines:</strong>

<ul>

 <li>You should provide appropriate comments to make your source code readable. If your code does not work and there are no comments, you may lose all the marks. See the marking criteria at the end of this document for details about the marks for commenting.</li>

 <li>You should follow a consistent coding style when writing your source code. There is a short discussion about coding style below. See the marking criteria at the end of this document for details about the marks for coding style.</li>

 <li>Submit the required files to the Assessment System (<a href="https://apps.ecs.vuw.ac.nz/submit/NWEN241/Programming_Assignment_1">https://apps. </a><a href="https://apps.ecs.vuw.ac.nz/submit/NWEN241/Programming_Assignment_1">vuw.ac.nz/submit/NWEN241/Programming_Assignment</a>_ <a href="https://apps.ecs.vuw.ac.nz/submit/NWEN241/Programming_Assignment_1">1</a><a href="https://apps.ecs.vuw.ac.nz/submit/NWEN241/Programming_Assignment_1">)</a> on or before the submission deadline.</li>

 <li>Late submissions (up to 48 hours from the submission deadline) will be accepted but will be penalized. No submissions will be accepted 48 hours after the submission deadline.</li>

</ul>

<strong>“Skeleton” Files</strong>

In this assignment, you will be given the following skeleton files which should be under the files directory in the archive that contains this file.

<ol>

 <li>h – C header file that contains macro definitions and all the required function prototypes for Part I. <em>Do not modify this file!</em></li>

 <li>hh – C++ header file that contains macro and class definitions for Part II. <em>Do not modify this file!</em></li>

 <li>hh – Empty C++ header file that you will use to define your class for Part II.</li>

 <li>c – Empty C file that you will use to implement functions for Part I. You are free to implement other functions within this file that you think are needed to fulfil the tasks.</li>

 <li>cc – Empty C++ file that implements your class for Part</li>

</ol>

II.

To get a better understanding of the tasks, you should read this document together with the provided skeleton code.

<strong>Coding Style</strong>

Coding style (also known as coding standard) refers to the use of appropriate indentation, proper placement of braces, proper formatting of control constructs, etc. Following a particular coding style consistently will make your source code more readable.

There are many coding standards available (search “C/C++ coding style”). Most of these standards are dense and will take you many days (even weeks) to read and understand. If you want to follow a <em>lightweight </em>coding style, consult the Linux kernel coding style (<a href="https://www.kernel.org/doc/html/v4.10/process/coding-style.html">https://www.kernel. </a><a href="https://www.kernel.org/doc/html/v4.10/process/coding-style.html">org/doc/html/v4.10/process/coding-style.html</a><a href="https://www.kernel.org/doc/html/v4.10/process/coding-style.html">)</a>. You only need to read sections 1–3 of this document.

Note that you do not have to follow every recommendation you can find in a coding style document. If you change, for instance the tab size from 8 to 4, that is fine. You just have to apply that style consistently.

<strong>Editing Buffer</strong>

An important component of a text editor is the <em>editing buffer </em>which is essentially a block of computer memory that contains part of the text document being edited. It can be viewed as one-dimensional array of characters from the perspective of the programmer.

<strong>Part I: Pure C Programming</strong>

You may only use the Standard C Library to perform the tasks in this part.

You should implement the functions in editor.c.

<strong>Task 1.</strong>

Basics [10 Marks]

In this task, you will implement a function with prototype

<strong>int </strong>editor_insert_char(<strong>char </strong>*editing_buffer, <strong>char </strong>to_insert, <strong>int </strong>pos)

which will insert the character to_insert at index pos of editing_buffer. The size of editing_buffer is EDITING_BUFLEN. When a character is inserted at index pos, each of the original characters at index pos until the end of buffer must be moved by one position to the right. The last character is thrown out.

The function should return 1 if the character insertion occurred, otherwise it should return 0.

To clarify, suppose that EDITING_BUFLEN is defined to be 21 and the contents of editing_buffer are

<table width="476">

 <tbody>

  <tr>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

  </tr>

 </tbody>

</table>

After invoking

<strong>int </strong>r = editor_insert_char(editing_buffer, ’s’, 9);

the contents of editing_buffer should be

<table width="476">

 <tbody>

  <tr>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

  </tr>

 </tbody>

</table>

and the value of r is 1.

<strong>Task 2.</strong>

Basics [10 Marks]

In this task, you will implement a function with prototype

<strong>int </strong>editor_delete_char(<strong>char </strong>*editing_buffer, <strong>char </strong>to_delete, <strong>int </strong>offset)

which will delete the first occurrence of the character to_delete. The search should start from index offset of editing_buffer. The size of editing_buffer is EDITING_BUFLEN. When a character is deleted at index pos, each of the original characters at index pos until the end of buffer must be moved by one position to the left. A null character is inserted at the end of the buffer.

The function should return 1 if the character deletion occurred, otherwise it should return 0.

To clarify, suppose that EDITING_BUFLEN is defined to be 21 and the contents of editing_buffer are

<table width="476">

 <tbody>

  <tr>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

  </tr>

 </tbody>

</table>

After invoking

<strong>int </strong>r = editor_delete_char(editing_buffer, ’f’, 10);

the contents of editing_buffer should be

<table width="476">

 <tbody>

  <tr>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

  </tr>

 </tbody>

</table>

and the value of r is 1.

<strong>Task 3.</strong>

Completion [10 Marks]

In this task, you will implement a function with prototype

<strong>int </strong>editor_replace_str(<strong>char </strong>*editing_buffer, <strong>const char</strong>

*str, <strong>const char </strong>*replacement, <strong>int </strong>offset)

which will replace the first occurrence of the string str with replacement. The search should start from index offset of editing_buffer. The size of editing_buffer is EDITING_BUFLEN.

The replacement should not overwrite other contents in the buffer. This means that if replacement is longer than str, there is a need move the characters after str to the right. Likewise, if replacement is shorter than str, there is a need move the characters after str to the left. When moving characters to the right, throw out characters that will not fit in the buffer. When moving characters to the left, insert null characters in the vacated positions.

If the replacement text will go beyond the limits of editing_buffer, then replacement should only occur until the end of editing_buffer.

If the string replacement occurred, the function should return the index corresponding the last letter of replacement in editing_buffer, otherwise, it should return -1. If the replacement text will go beyond the limits of editing_buffer, the function should return EDITING_BUFLEN-1.

To clarify, suppose that EDITING_BUFLEN is defined to be 21 and the contents of editing_buffer are

<table width="476">

 <tbody>

  <tr>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

  </tr>

 </tbody>

</table>

After invoking

<strong>int </strong>r = editor_replace_str(editing_buffer, “brown”,

“blue”, 0);

the contents of editing_buffer should be

<table width="476">

 <tbody>

  <tr>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

  </tr>

 </tbody>

</table>

and the value of r should be 13 (which is the index of ’e’ in “blue”).

<strong>Task 4.</strong>

Challenge [10 Marks]

In this task, you will implement a function with prototype

<strong>void </strong>editor_view(<strong>char </strong>**viewing_buffer, <strong>const char</strong>

*editing_buffer, <strong>int </strong>wrap)

which will essentially copy the contents of the editing_buffer to the viewing_buffer for display to the user. Note that the latter is a twodimensional array, with dimensions VIEWING_COLS columns and VIEWING_ROWS rows. VIEWING_COLS and VIEWING_ROWS are defined in editor.h.

Prior to the copying, the function must set every character in the viewing_buffer to the null character.

The argument wrap controls the behaviour of the copying process from editing_buffer to viewing_buffer as follows:

<ul>

 <li>Regardless of the value of wrap, whenever a newline character is encountered, subsequent text after the newline charater is copied to the next row. Note that the newline character itself is not copied to viewing_buffer.</li>

 <li>When wrap is non-zero, the text must be wrapped. This means that when the newline character is <em>not </em>encountered before the end of the current row (at column VIEWING_COLS-1 in viewing_buffer), subsequent text is copied to the next row. Note that column VIEWING_COLS-1 in viewing_buffer is never filled and will retain the null character.</li>

 <li>When wrap is 0, the text is not wrapped. This means that when the newline character is <em>not </em>encountered before the end of the current row (at column VIEWING_COLS-1), succeeding text in the editing_buffer are discarded until a newline is encountered which will cause the succeeding text to be copied to the next row. Note that column VIEWING_COLS-1 in viewing_buffer is never filled and will retain the null character.</li>

</ul>

The copying process should terminate when a null character is encountered.

To clarify, suppose that EDITING_BUFLEN is defined to be 48 and the contents of editing_buffer are

<table width="387">

 <tbody>

  <tr>

   <td width="24"></td>

   <td width="24"></td>

   <td width="24"></td>

   <td width="24"> </td>

   <td width="24"></td>

   <td width="24"></td>

   <td width="24"></td>

   <td width="24"></td>

   <td width="24"> </td>

   <td width="24"></td>

   <td width="24"></td>

   <td width="24"></td>

   <td width="24"></td>

   <td width="24"></td>

   <td width="24"></td>

   <td width="24"></td>

  </tr>

 </tbody>

</table>

Suppose that VIEWING_COLS and VIEWING_ROWS are 11 and 8, respectively. After invoking

editor_view(viewing_buffer, editing_buffer, 1);

the resulting contents of viewing_buffer should be

editor_view(viewing_buffer, editing_buffer, 0);

the resulting contents of viewing_buffer should be

<strong>Part II: C++ Programming</strong>

You may use the C++ Standard Library to perform the tasks in this part.

<strong>Task 5.</strong>

Basics [10 Marks]

In this task, you will define a class that extends the EditingBuffer class defined in editor.hh. You should declare the class in myeditor.hh and name it MyEditingBuffer. This class should be in same namespace as EditingBuffer. The access mode of the inherited members should be preserved.

You are free to declare additional member variables and functions that are necessary to perform the subsequent tasks. Provide sufficient comment, and ensure that these additional member variables and functions are <em>not </em>publicly accessible.

<strong>Task 6.</strong>

Basics [10 Marks]

In this task, you will implement the member function

<strong>bool </strong>replace(<strong>char </strong>c, <strong>char </strong>replacement, <strong>int </strong>offset)

which will replace the first occurrence of the character c with replacement in the buffer. The search should start from index offset of buffer. The length of buffer is BUFFER_LEN which is defined in editor.hh.

The function should return true if the character insertion occurred, otherwise false.

To clarify, suppose that BUFFER_LEN is defined to be 21 and the contents of buffer are

<table width="476">

 <tbody>

  <tr>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

  </tr>

 </tbody>

</table>

After invoking

MyEditingBuffer meb; … <strong>bool </strong>r = meb.replace(’b’, ’B’, 5);

the resulting contents of the buffer should be

<table width="476">

 <tbody>

  <tr>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

  </tr>

 </tbody>

</table>

and the value of r should true.

You should implement this member function in myeditor.cc.

<strong>Task 7.</strong>

Completion [10 Marks]

In this task, you will implement the member function

<strong>int </strong>replace(std::string str, std::string replacement, <strong>int </strong>offset)

which will replace the first occurrence of the string str with replacement. The search should start from index offset of buffer.

The replacement should not overwrite other contents in the buffer. This means that if replacement is longer than str, there is a need move the characters after str to the right. Likewise, if replacement is shorter than str, there is a need move the characters after str to the left. When moving characters to the right, throw out characters that will not fit in the buffer. When moving characters to the left, insert null characters in the vacated positions.

If the replacement text will go beyond the limits of buffer, then replacement should only occur until the end of buffer.

If the string replacement occurred, the function should return the index corresponding the last letter of str in editing_buffer, otherwise, it should return -1. If the replacement text will go beyond the limits of buffer, the function should return BUFFER_LEN-1.

To clarify, suppose that BUFFER_LEN is defined to be 21 and the contents of buffer are

<table width="476">

 <tbody>

  <tr>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

  </tr>

 </tbody>

</table>

After invoking

MyEditingBuffer meb; …

std::string s(“brown”); std::string t(“violet”); <strong>int </strong>r = meb.replace(s, t, 8);

the resulting contents of the buffer should be

<table width="476">

 <tbody>

  <tr>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"> </td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

   <td width="23"></td>

  </tr>

 </tbody>

</table>

and the value of r should be 15 (which is the index of ’t’ in “violet”).

You should implement this member function in myeditor.cc.

<strong>Task 8.</strong>

Challenge [15 Marks]

In this task, you will implement the member function

<strong>void </strong>justify(<strong>char </strong>**viewingBuffer, <strong>int </strong>rows, <strong>int </strong>cols)

which will justify the contents of buffer by adjusting the space in between words. The justified text should be stored in viewingBuffer, a two-dimensional array which has rows rows and cols columns.

To implement the text justification, the contents of buffer must first be copied to viewingBuffer such that the copied text is wrapped. You may reuse your implementation in Task 4 for this purpose.

After copying, the contents of viewingBuffer must be justified, i.e., <strong>the character at column </strong>cols-2 <strong>of every row must not be a whitespace if possible</strong>. This can be done by adding whitespaces in between words. When justifying, follow these guidelines:

<ol>

 <li>Do not justify empty rows (rows consisting of null characters) and single-word rows.</li>

 <li>Do not split words, <em>e.</em>, do not insert spaces in between the letters of a word.</li>

 <li>You can split a single-word row if the single word is too long to fit one row.</li>

 <li></li>

</ol>

<table>

 <tbody>

  <tr>

   <td width="167"></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Do not merge words.</li>

</ul>

<ol start="5">

 <li>If necessary, discard characters that will not fit in the buffer.</li>

</ol>

To clarify, suppose that BUFFER_LEN is defined to be 48 and the contents of buffer are

<table width="387">

 <tbody>

  <tr>

   <td width="24"></td>

   <td width="24"></td>

   <td width="24"></td>

   <td width="24"> </td>

   <td width="24"></td>

   <td width="24"></td>

   <td width="24"></td>

   <td width="24"></td>

   <td width="24"> </td>

   <td width="24"></td>

   <td width="24"></td>

   <td width="24"></td>

   <td width="24"></td>

   <td width="24"></td>

   <td width="24"></td>

   <td width="24"></td>

  </tr>

 </tbody>

</table>

After invoking

MyEditingBuffer meb; …

meb.justify(viewingBuffer, 8, 11);

the resulting contents of viewingBuffer should be

You should implement this member function in myeditor.cc.

<strong>Part III: Systems Program Design</strong>

In Parts I and II, you implemented some functionality for manipulating the contents of the editing buffer. In this part, you will <em>design </em>a C++ program for manipulating the <em>viewing buffer</em>.

<strong>Task 9.</strong>

Challenge [15 Marks]

The <em>viewing buffer </em>is a block of computer memory that contains part of the text document shown in the computer display. It can be viewed as a twodimensional array of characters, where the each row corresponds to a line of text. In practice, the number of rows and columns should be determined by the size of the display/terminal. For simplicity, fix the number of rows and columns to 25 and 80, respectively.

In designing the program, assume that a <em>main buffer </em>contains the entire text document being edited. Assume that the main buffer variable is global and is declared as char main_buffer[1000000] somewhere.

The following functionality are required to manipulate the viewing buffer:

<ul>

 <li>Load parts of text document from main buffer to the viewing buffer (from a given line/row position).</li>

 <li>Scroll up viewing buffer content by a given number of lines/rows.</li>

 <li>Scroll down viewing buffer content by a given number of lines/rows.</li>

 <li>Enable wrapping</li>

 <li>Disable wrapping</li>

 <li>Show line numbering</li>

 <li>Hide line numbering</li>

</ul>

<strong>What You Need To Do:</strong>

Create the necessary files (header and source) to define a class that would implement the above set of functionality. For every member variable and function that you specify, provide sufficient comments about their purpose.

<strong>You do not need to implement the member functions. However, you will need to write the <em>member function header </em>in the source file, followed by an empty body implementation.</strong>

Put the header and source files in a ZIP file called part3.zip.

<strong>Marking Criteria for Tasks 1, 2, 3, 4, 6, 7, and 8:</strong>

<table width="500">

 <tbody>

  <tr>

   <td width="119">Criteria</td>

   <td width="62">Weight</td>

   <td width="319">Expectations for Full Marks</td>

  </tr>

  <tr>

   <td width="119">“Compilability”</td>

   <td width="62">10%</td>

   <td width="319">Source code compiles without warnings</td>

  </tr>

  <tr>

   <td width="119">Commenting</td>

   <td width="62">10%</td>

   <td width="319">Source code contains sufficient and appropriate comments</td>

  </tr>

  <tr>

   <td width="119">Coding Style</td>

   <td width="62">10%</td>

   <td width="319">Source code is formatted, readable and uses a coding style consistently</td>

  </tr>

  <tr>

   <td width="119">Correctness</td>

   <td width="62">70%</td>

   <td width="319">Handles all possible cases correctly</td>

  </tr>

  <tr>

   <td width="119"> </td>

   <td width="62">100%</td>

   <td width="319"> </td>

  </tr>

 </tbody>

</table>

<strong>Marking Criteria for Tasks 5 and 9:</strong>

<table width="500">

 <tbody>

  <tr>

   <td width="119">Criteria</td>

   <td width="62">Weight</td>

   <td width="319">Expectations for Full Marks</td>

  </tr>

  <tr>

   <td width="119">Commenting</td>

   <td width="62">10%</td>

   <td width="319">Source code contains sufficient and appropriate comments</td>

  </tr>

  <tr>

   <td width="119">Coding Style</td>

   <td width="62">10%</td>

   <td width="319">Source code is formatted, readable and uses a coding style consistently</td>

  </tr>

  <tr>

   <td width="119">Correctness</td>

   <td width="62">40%</td>

   <td width="319">Addresses all specifications and correctly uses syntax in the declarations and/or definitions</td>

  </tr>

  <tr>

   <td width="119">Completeness</td>

   <td width="62">30%</td>

   <td width="319">Declaration and/or definition of all required member variables and functions</td>

  </tr>

  <tr>

   <td width="119"> </td>

   <td width="62">100%</td>

   <td width="319"> </td>

  </tr>

 </tbody>

</table>


