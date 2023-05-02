Download Link: https://assignmentchef.com/product/solved-comp1044-uo-programming-fundamentals-assignment-part-two
<br>
Assignment

Mastermind Board Game Development

<h1>Assignment Learning Outcomes</h1>

<ul>

 <li>Design a UML class diagram using UMLet</li>

 <li>Apply object-oriented principles (encapsulation, reuse, etc.) including inheritance and composition relationships to the software design</li>

 <li>Implement the software design in Python using class inheritance and polymorphism features</li>

 <li>Write init functions for Python classes</li>

 <li>Use stream I/O and manipulators for formatted input and output</li>

 <li>Write code adhering to coding standards, guidelines and good programming practices</li>

</ul>

<h1>Instructions</h1>

The assignment will require you to design, implement, test, and debug a text-based Mastermind board game using object-oriented methods and the application of appropriate relationships between classes (inheritance, composition, association). In addition, the assignment will require you to use version control to keep track of your implementation as you progress through the assignment and to document your classes appropriately.

The assignment is split into two parts: UML Design (due: Week 5), and Implementation (due: Week 9). <strong>Part 1 of this assignment (UML Design) is to be performed individually </strong>and will be <strong>submitted via LearnOnline</strong>.<strong> Part 2 of this assignment (Implementation in Python) is to be performed individually</strong> and will be<strong> submitted via LearnOnline</strong>.







<h1>Part 2: Implementation</h1>




<h2>1. Introduction</h2>

The second part of this assignment will develop your skills by allowing you to put into practice what has been taught in classes so far on object-oriented programming in Python.

<h2>2. Task Description</h2>

Mastermind is a code-breaking game for two to four players

<a href="https://en.wikipedia.org/wiki/Mastermind_(board_game)">(</a><a href="https://en.wikipedia.org/wiki/Mastermind_(board_game)">https://en.wikipedia.org/wiki/Mastermind_(board_game)</a><a href="https://en.wikipedia.org/wiki/Mastermind_(board_game)">)</a>. The goal of the game is to discover a hidden code that consists of 4-5 code pegs.

<strong>2.1 The Board Game “Original Mastermind” </strong>




The <u>board game</u> is played using:

<ul>

 <li><strong>a decoding board</strong>, with a shield at one end covering a row of four large holes, and twelve (or ten, or eight, or six) additional rows containing four large holes next to a set of four small holes;</li>

 <li><strong>code pegs</strong> of six different colours (Red, Green, Blue, Cyan, Magenta, Yellow), with round heads, which will be placed in the large holes on the board; and</li>

 <li><strong>key pegs</strong>, some coloured black, some white, which are flat-headed and smaller than the code pegs; they will be placed in the small holes on the board.</li>

</ul>

The two players decide in advance how many games they will play, which must be an even number. One player becomes the <em>codemaker</em>, the other the <em>codebreaker</em>. The codemaker chooses a pattern of four code pegs. Duplicates and blanks are allowed depending on player choice, so the player could even choose four code pegs of the same colour or four blanks. In the instance that blanks are not elected to be a part of the game, the codebreaker may not use blanks in order to establish the final code. The chosen pattern is placed in the four holes covered by the shield, visible to the codemaker but not to the codebreaker.

The codebreaker tries to guess the pattern, in both order and colour, within eight to twelve turns. Each guess is made by placing a row of code pegs on the decoding board. Once placed, the codemaker provides feedback by placing from zero to four <em>key pegs</em> in the small holes of the row with the guess. A black key peg is placed for each code peg from the guess which is correct in both colour and position. A white key peg indicates the existence of a correct colour code peg placed in the wrong position.

If there are duplicate colours in the guess, they cannot all be awarded a key peg unless they correspond to the same number of duplicate colours in the hidden code. For example, if the hidden code is red-red-blue-blue and the player guesses red-red-red-blue, the codemaker will award two black key pegs for the two correct reds, nothing for the third red as there is not a third red in the code, and a black key peg for the blue. No indication is given of the fact that the code also includes a second blue.

Once feedback is provided, another guess is made; guesses and feedback continue to alternate until either the codebreaker guesses correctly, or twelve (or ten, or eight) incorrect guesses are made.

If the code is not guessed correctly within 12 attempts, then the code is revealed.

<strong>2.2 The Board Game “Mastermind44” </strong>




Mastermind44 is a variation of the original Mastermind for 4 players: <a href="https://boardgamegeek.com/boardgame/12467/mastermind44">https://boardgamegeek.com/boardgame/12467/mastermind44</a>

The difference between the two versions of the game are in the length of the code, how the code is created, how feedback is provided, and the number of attempts for each player:

<ul>

 <li>The code consists of 5 coloured pegs.</li>

 <li>There are five black code counters that contain the numbers 1 to 5. They indicate the position of the code.</li>

 <li>There are white code counters that contain a colour. There are 5 white code counters for each colour. They will be used to select the colour of a position in the code.</li>

 <li>The code counters are placed upside down on the table so the number and the colours cannot be seen.</li>

 <li>The code is created by the four players: Each player picks a black (with a number) and a white (with a colour) code counter and secretly places them with the colour and number facing to them. One black code counter will remain on the table. This indicates a blank on the position in the code as indicated by that counter.</li>

 <li>One player makes a guess and then that player and the other players provide feedback with a black or white key peg (or nothing) depending on their secret black and white code counter. (Note, the player who makes a guess may put the correct coloured code peg in the correct position according to his/her secret black and white code counter. He must indicate this by a key peg in the feedback).</li>

 <li>Then the next player clockwise makes a guess and receives feedback from everyone else.</li>

 <li>Each player has 5 attempts.</li>

 <li>The first player who receives four black key pegs wins.</li>

 <li>If each player guesses 5 times and no player wins then the code is revealed.</li>

</ul>

<strong>2.3 Adaptation for Implementation: </strong>

For the implementation we will make some adaptations:

<ul>

 <li>Both versions, the Original and Mastermind44 must be supported by the implementation.</li>

 <li>No blanks are allowed for the Original Mastermind and there will be only one blank in the code for Mastermind44.</li>

 <li>The Original version will use a code consisting of 4 pegs.</li>

 <li>The Mastermind44 version will use a code consisting of 5 pegs.</li>

 <li>The Original Mastermind version will allow 12 attempts for the code breaker and the Mastermind44 version will allow 5 attempts for each player.</li>

 <li>The computer will always provide feedback for each guess automatically on the screen. No human input is required.</li>

 <li>The Original Mastermind version will allow two modes: (1) With or (2) without <em>computer support</em>. <em>Computer support</em> means that the secret code is generated automatically at the start of a game.

  <ul>

   <li>Original Mastermind without computer support: There are two players, the code maker, and the code breaker. The code maker and code breaker will be selected at random by the computer. The code maker specifies manually the code and the code breaker tries to find it.</li>

   <li>Original Mastermind with computer support: There is only one player, the code breaker. The computer will generate the code.</li>

  </ul></li>

 <li>The secret code for Mastermind44 is generated by the computer. The computer will reveal a unique position and colour to each player individually.</li>

</ul>




In this assignment, you will design and implement a text-based Mastermind game that fulfils the specification above. Text-based does not mean ASCII art but instead will be driven by a text-based menu interface.

The aim of the assignment is to allow you to practise creating an object-oriented design and implementing it in Python using features such as <em>class inheritance</em>, <em>polymorphism</em>, and <em>composition</em>. The focus of the assignment is on identifying classes and applying appropriate relationships between the classes. The game should be designed in such a way that code is reused and can be extended easily, for example, with yet another version of Mastermind.

In the second part of the assignment you will need to <strong><em>implement the classes and methods based on your UML class diagrams.</em></strong>

A brief example of how the game will be played is provided below. The remainder of the section describes the requirements of the game in more detail.

Note: the following conventions will be used when illustrating the example output below:

<ul>

 <li>A <strong>bold purple text</strong> indicates input entered by the user</li>

 <li>User input surrounded by square brackets ‘[…]’ indicates a specific key press</li>

</ul>

Inside Visual Studio Code:

my_game = Mastermind() my_game.play()







Welcome to Mastermind!

This game has been developed by Masud Karim

For the course UO Programming Fundamentals SP1 2021







*********************************************************

Select which game you want to play?

<ul>

 <li>Original Mastermind for 2 players</li>

 <li>Original Mastermind for 1 player with Computer Support</li>

 <li>Mastermind44 for 4 players</li>

 <li>Mastermind44 for 4 players with Computer Support</li>

 <li>Exit</li>

</ul>




*********************************************************

*Enter your choice [Press A, B, C, D, or E]*

<h3>A [ENTER]</h3>




Player 1: What is your name? <strong>Matthew</strong> <strong>[ENTER]</strong> Player 2: What is your name? <strong>Daniel [ENTER]</strong>




*********************************************************

Welcome Matthew

You are the codemaker for this game.

You need to make a Code that consists of four pegs.

Each peg can be of the colour (R)ed, (B)lue, (G)reen, (Y)ellow, (M)agenta, or (C)yan.

Make the Code by specifying four characters where each character indicates a colour as above.

For example, BYRG represents the code Blue Yellow Red Green.

You need to enter the Code twice. Asterisk character (*) is shown on the screen for each character.




[Matthew] Enter the Code to make:

****

[Matthew] Enter the Code again to make:

****

[Matthew] The Code is stored.




*********************************************************

Welcome Daniel

You are the codebreaker for this game. Matthew has made a Code for you.

You need to break the Code that consists of four pegs.

Each peg can be of the colour (R)ed, (B)lue, (G)reen, (Y)ellow, (M)agenta, or (C)yan.

Break the Code by specifying four characters where each character indicates a colour as above.

For example, BYRG represents the code Blue Yellow Red Green.

Feedback will be provided on your attempted Code.

Black peg means there is a peg in your Code with correct colour and correct order.

White peg means there is a peg in your Code with correct colour but incorrect order.

Blank space in the feedback denotes a peg in your Code with incorrect colour and incorrect order.

You will get 12 attempts to break the code.

Good luck!




[Daniel] Enter the Code to break:

<h3>GGGG</h3>

Attempt #1:

GREEN GREEN GREEN GREEN Feedback #1:







[Daniel] Enter the Code to break:

<h3>RRRR</h3>

Attempt #2:

RED RED RED RED

Feedback #2:

BLACK BLACK




[Daniel] Enter the Code to break:

<h3>BBBB</h3>

Attempt #3:

BLUE BLUE BLUE BLUE

Feedback #3:

BLACK BLACK




[Daniel] Enter the Code to break:

<h3>RRBB</h3>

Attempt #4:

RED RED BLUE BLUE

Feedback #4:

BLACK BLACK WHITE WHITE




[Daniel] Enter the Code to break:

<h3>BBRR</h3>

Attempt #5:

BLUE BLUE RED RED

Feedback #5:

BLACK BLACK WHITE WHITE




[Daniel] Enter the Code to break:

<h3>BRBR</h3>

Attempt #6:

BLUE RED BLUE RED

Feedback #6:

WHITE WHITE WHITE WHITE




[Daniel] Enter the Code to break:

<h3>RBRB</h3>

Attempt #7:

RED BLUE RED BLUE

Feedback #7:

BLACK BLACK BLACK BLACK

Congratulations Daniel! You have broken the Code in 7 attempts.

Daniel has won this original matermind game!

Better luck next time Matthew!




*********************************************************

Select which game you want to play?

<ul>

 <li>Original Mastermind for 2 players</li>

 <li>Original Mastermind for 1 player with Computer Support</li>

 <li>Mastermind44 for 4 players</li>

 <li>Mastermind44 for 4 players with Computer Support</li>

 <li>Exit</li>

</ul>




*********************************************************

*Enter your choice [Press A, B, C, D, or E]* <strong>E</strong>

Goodbye!




<h2>3. Documentation</h2>

Your code must be documented appropriately using docstrings comments.

Document as you go, not all at the end. One strategy is to write a brief comment about what the  “1 thing” the function is supposed to do when you declare it, then refer to that comment while implementing it: this helps maintain focus when implementing the function and helps stop yourself from making it do more than the ‘1’ thing it is supposed to do.

Each class and each method should have at least one docstring which can be brief. The responsibilities that you have specified in the UML diagram can be used as a starting point for the class docstring.




<h2>4. Python Code Style Guide</h2>

There are many style guides available online. Follow the Python guide available here:

<a href="https://www.python.org/dev/peps/pep-0008/">https://www.python.org/dev/peps/pep</a><a href="https://www.python.org/dev/peps/pep-0008/">–</a><a href="https://www.python.org/dev/peps/pep-0008/">0008/</a>




<h2>5. Version Control</h2>

You must use version control to keep track of your progress during implementation, using git. You should perform regular commits as you implement features and fix errors. Your commit comments should reflect the context of the changes that were made in each commit—a fellow developer can always diff the contents to see exactly what changed but that does not provide the context. You should try to ensure each commit comment contains a short subject line.

Your submission will comprise your entire version control repository, so it should be specific to the assignment. For example, if you use git, you must create the git repository in the root directory for your assignment. Do not commit your assignment to a repository created in a parent folder or any other location. Your repository must contain all source files required to run your program. You can use the ‘.gitignore’ file to specify files and folders you do not want to include in the repository, such as the generated documentation files/folders.

You do not have to use an online version control repository such as GitHub. If you do use an online repository, ensure that the assignment is private, i.e., cannot be seen by people other than yourself.




<h2>6. Implementation Rules and Hints</h2>

Implement your code into a single Python file.

It is recommended that you test individual methods as you go, rather than trying to test the whole application through the menu-driven interface. Writing code to test specific elements will speed up development as you will not need to constantly enter data through the menu interface.

Update the UML diagram as you implement the program and you realise that attributes or methods are missing in the design. You will need to submit an updated UML diagram with your submission.




<h2>7. Work Plan</h2>

To complete the implementation, you will need to perform the following steps:

<ol>

 <li>Read the assignment specification carefully.</li>

 <li>Start to implement the basic classes for the Original Mastermind with single player mode.</li>

 <li>Always include docstrings for documentation as you go. If you do this later, you may forget something, and it is more effort to insert documentation at a later stage.</li>

 <li>Create basic functionality before you start to implement the interaction with a player, for example, generating code, checking an attempt from the player, and providing feedback.</li>

 <li>Create interaction with the player.</li>

 <li>Update the UML diagram to reflect your implementation.</li>

 <li>Start testing the game: (1) Write tests for methods. (2) Play the game and try out different things.</li>

 <li>Include exception handling where necessary based on test results.</li>

 <li>Implement the “two players” mode for Original Mastermind.</li>

 <li>Implement Mastermind44: First basic classes, then the interaction with players.</li>

 <li>Update the UML diagram to reflect your implementation.</li>

 <li>Start testing the Mastermind44 game: (1) Write tests for methods. (2) Play the game and try out different things.</li>

 <li>Submit your assignment</li>

</ol>

<h2>4. Submission Details</h2>

You MUST submit a zip archive which contains the following files:

<ul>

 <li>Updated UML Class Diagram as a single PNG imported into <strong>Word</strong> or <strong>PDF</strong> The file MUST be generated from the UMLet modelling tool: a photo of a hand-drawn diagram will NOT be accepted.</li>

 <li>A Python file that contains the implementation of the game.</li>

 <li>A Word document that explains how to start and interact with the game.</li>

 <li>Version control directory (‘.git’ folder)</li>

</ul>








