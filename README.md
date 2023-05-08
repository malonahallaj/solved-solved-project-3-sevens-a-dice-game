Download Link: https://assignmentchef.com/product/solved-solved-project-3-sevens-a-dice-game
<br>






Before Starting the Project

·         Read chapter 5 and sections 6.1 – 6.4      Read this entire project description before starting




Learning Objectives

After completing this project you should be able to:

·         Read and write source code for a Graphical User Interface (GUI)

·         write methods to meet specific requirements

·         write conditional statements with boolean expressions

·         describe the difference between public and private methods

Game Rules

Sevens is played by two people using six standard dice. A player’s turn includes 1 – 3 rolls of the dice. The first player to earn 77 points loses!

Aim of the game: You win if the other player gets at least 77 points before you.

How to play: A player rolls all six dice.  After each roll the player may set aside a single pair of dice that sum to 7.  The player now has the option to roll the remaining dice or pass to the next player.  The player must pass if there is no pair that sums to 7.  Player points for the turn are the total value of all “left over” dice.  Play goes back and forth between players until one loses by getting at least 77 points.

Example 1: You initially roll 2 4 3 3 1 5 and set aside a 4 and 3.  You roll the remaining dice and get 5 6 6 2.  Set aside the 5 and 2.  You will probably choose to roll the last two dice and hope for a seven but roll 4 6.  You score 10 points for this turn and pass the dice.

Example 2: You initially roll 2 4 6 6 2 2.  You have no pairs that add to 7 and must pass the dice.  You score 22 points for this turn.

Example 3: You initially roll 2 4 5 6 2 2 and set aside a 2 and 5.  You roll the remaining dice and get 1 1 1 1.  This is a relatively low score and you might choose to pass the dice now.  You score 4 points for this turn.

Step 1: Create a New BlueJ Project

Step 2: Class Definition: GVdie

Rather than writing your own Die class, we are providing a completed class for you.  Create a new class in BlueJ called GVdie and delete all of the provided code.  Cut and paste the provided code from (GVdie.java) into the newly created class.  It should compile with no errors.  Do not make any changes to this code.  You only need to use the following methods but you are encouraged to read through the source code to see how it works.

GVdie d1 = new GVdie();      // create object

d1.roll();                  // roll the die

int val = d1.getValue();     // check current value

d1.setBlank();              // set face to blank

if(d1.isHeld())             // check if die is selected

d1.setHeld(boolean b);       // hold or unhold die

d1.setFrozen(boolean b);     // freeze or unfreeze

Step 3: Class Definition: Sevens

Create a new class called Sevens.  Implement each of the following methods.  It is generally best to write the methods in the following order but you may occasionally have to skip ahead and write other methods first.

All feedback is provided to the player through a graphical user interface (GUI).  Nothing is printed to the screen.  Your source code should have no System.out.print() statements with the exception of showDice().

Instance Variables

A class should contain several instance variables (section 3.1). Sometimes instance members are not expected to change after given an initial value.  It is good practice to define these as final and use ALL CAPS for the names (section 7.1).  Provide appropriate names and data types for each of the private instance variables:

·         GVdie objects for six dice

·         integers for both player scores

·         integer for number of rolls in current round

·         boolean value if it is player1 turn or not

Constructors (5 pts)

A constructor is a special method with the same name as the class and generally initializes the fields to appropriate starting values.  Refer to sections 3.7 and 3.8.

·         public Sevens ( ) – a constructor that instantiates six dice and initializes all instance variables to appropriate values.  Set the dice faces to blank.  Player 1 goes first.

Accessor Methods (15 pts)

An accessor method does not modify class fields.  The names for these methods, which simply return the current value of a field, often begin with the prefix ‘get’. Refer to section 3.6.

·         public int getScore1 ( ) – returns score of first player.

·         public int getScore2 ( ) – returns score of second player.

·         public boolean isPlayer1turn ( ) – returns true if it is first player’s turn.  Otherwise, return false.

·         public boolean turnOver ( ) – returns true if the number of rolls is three or greater.

·         public boolean gameOver ( ) – returns true if either player score is at least 77.

·         public GVdie getDie (int num) – return the requested die. Legal values for the parameter are 1 – 6.   This method is used for the GUI.  For example,

if (num == 1){

return d1;

}

Private Helper Methods (20 pts)

Designated as private, a helper method is designed to be used by other methods within the class.  Good practice is to make methods private unless they need to be public.  Refer to section 3.6.

·         private void resetDice ( ) – Set all dice to unselected, unfrozen and blank.  Note, this requires eighteen statements.

·         private int getDiceTotal( ) – returns total value of all dice NOT HELD.

·         private int getNumHeld( ) – return the number of dice that are HELD.  Note, this returns how many dice are currently held and not the value of their faces.

·         private void freezeDice ( ) –  Freeze all of the dice.

d1.setFreeze(true);

·         private void showDice () – Use System.out.print to display current values of the dice on one line.  Use an asterisk to indicate the die is held.  Note, this method is used mainly for testing.  For example:

2  3  *  2  *  6

Mutator Methods  (15 pts)

A mutator method performs tasks that may modify class fields. Refer to section 3.6.

·         public void rollDice ( ) – If the number of current rolls is less than three, roll all dice that are NOT HELD.  Increment the number of rolls.

·         public void passDice ( ) –  Update score of current player (first or second) by adding the new total.  Invoke the helper method getDiceTotal().   Change the boolean variable to switch players.  Reset the number of rolls to zero and invoke resetDice().

·         public void resetGame () – reset for a fresh game.  Set scores and number of rolls to zero.  Reset all dice by invoking resetDice().

Coding Style (10 pts)

Good programming practice includes writing elegant source code for the human reader.  Follow the GVSU Java Style Guide.

So Far So Good!

You now have a functional game and can complete steps 4 5 and 6 in any order

Step 4: Preventing Player Errors (10 pts)

The game is now functional but the player can make errors or try to cheat!  Make the following improvements to prevent common errors and cheating.  We do not want players to select dice that do not create pairs of sevens.  Players should be prevented from rolling dice if their hand is not legal.

·         private void checkValidOptions( ) – confirm there is at least one pair of dice not already held that add to seven.  If there are no remaining options then set the number of rolls to 3 and invoke freezeDice().  This will effectively end the player’s turn. Note, this will be a cumbersome solution with fifteen if statements.  Be patient and carefully check all options.

·         private boolean isValidHand( ) – return true if the dice represent a valid hand.  There are only three options: 1) number of rolls = 0 and no dice are held, 2) number of rolls = 1, two dice are held and their values sum to seven, 3) number of rolls = 2, four dice are held and their values sum to fourteen.  Invoke getNumHeld().

·         Update the existing rollDice().  Only roll the dice if the hand is valid, invoke isValidHand().  At the end of the method, invoke checkValidOptions() to end the turn if no valid options remain.

·         Note, these methods will help avoid most cheating but not all!

Step 5: Software Testing (10 pts)

Games and other applications that generate random results are difficult to test.  You will use a different approach for this project by writing methods to automate a game.  You can then review the results for errors.

·         private void autoHold( ) – look for a pair of dice not already held that add to seven.  If you find a pair then hold both dice by invoking d.setHeld(true).  If there are no valid options then set the number of rolls to 3 ending the player’s turn. Note, this will be a cumbersome solution with fifteen if statements.

·         private void autoTurn( ) – simulate one player’s turn and pass the dice afterwards.

while(!turnOver()){

rollDice();

showDice();

autoHold();

}

passDice();

·         public void autoGame( ) – simulate a complete game by alternating back and forth between players until someone wins.  Print the player’s current score each turn.  Use a while loop to continue as long as the game is not over.  For each loop: invoke autoTurn().  After the loop, print a message indicating which player won.  Strive to duplicate the following output (with different numbers of course).

Shows last few turns of the game:

Player 2: 59

1 6 1 6 1 6

* * 1 2 1 6

* * * 2 1 *

Player 1: 54

6 6 2 4 2 2

Player 2: 62

3 2 3 2 4 4

* 3 2 4 * 2

* * 2 * * 2

Player 1: 76

2 6 5 4 5 2

* 3 * 3 2 2

Game Over

Player 1: 86

Player 2: 66

Player 2 wins

Step 6: Modify a GUI class (15 pts)

Now that you have the basic game working within its own class it is time to create a more interesting graphical user interface for the player to use.

Rather than writing your own GUI class, we are providing a partially complete class to get you started.  Create a new class in BlueJ called SevensGUI and delete all of the provided code.  Cut and paste the provided code from (SevensGUI.java) into the newly created class.  It should compile with no errors.  If it doesn’t compile then it probably means you used different method names in your Sevens class than what was specified.

We modeled our design on examples from the book in Section 6.3.  Read the code and comments carefully to understand how it works.  Your final GUI should look similar to Figure 1.  Start the program by invoking the GUI’s main method.

Figure 1. GUI screen shot.

1) Personalize Your Solution

·         Change the JFrame title to include your name

2) Create and place buttons and score label for Player 2

·         Define new instance variables for two JButton and a JLabel

·         Within the constructor, find the FIX ME comment and add code to instantiate and place the buttons / label.  Read the code for player 1 for guidance.

3) Finish the disableAllButtons() method

Add two lines of code to disable the buttons for player 2

4) Finish the newGame() method

Add code to: 1) disable all buttons by invoking disableAllButtons(), 2) enable player 1 roll button and 3) display the score for both players.

5) Finish the actionPerformed() method

This method will contain several if statements for each of the possible player actions and game status. Study the existing code and add new code at the FIX ME comments.

·         add an if statement for the New Game menu item.

if (e.getSource() == newGameItem){

newGame();

}

·         add if statement for player clicking on either pass button. Invoke the game method to pass the dice. Read the if statement for “rollButton” for guidance.

·         When the game is over, display a pop up message indicating who won.  For example,

JOptionPane.showMessageDialog(this, “Player 1 wins”);

·         Challenge Activity (5 pts of the GUI grade). Add statements to enable and disable buttons as necessary to prevent players from making mistakes. Enforce each of the following conditions: 1) both roll/pass buttons are disabled if it is not the player’s turn, 2) only Roll is enabled at the start of a turn, 3) only Pass is enabled if the turn is over.  Otherwise, both roll/pass buttons are enabled for the current player.  Do not make any changes to the Sevens class.

Strive to keep your logic simple and minimize the number of additional statements.  Hint, our solution requires 12 additional statements but maybe you can do better?

Grading Criteria

There is a 50% penalty on programming projects if your solution does not compile.

•     Stapled cover page with your name and signed pledge. (-5 pts if missing)

•     Project requirements as specified above. (90 pts)

Late Policy

Projects are due at the START of the class period. However, you are encouraged to complete a project even if you must turn it in late.

•     The first 24 hours (-20 pts)

•     Each subsequent weekday is an additional -10 pts

•     Weekends and university holidays are free days.

Turn In

A professional document is stapled with an attractive cover page.  Do not expect the lab to have a working stapler!

•     Cover page – Provide a cover page that includes your name, a title, and an appropriate picture or clip art for the project

•     Time Card – The cover page must also include a brief statement of how much time you spent on the project.  For example, “I spent 7 hours on this project from January 22-27 reading the book, designing a solution, writing code, fixing errors and putting together the printed document.”

•     Sample Output – a printout of the Terminal window after running the main method that shows a variety of the printed messages. You can copy and paste into the Word document that contains your cover page.

•     Source code – a printout of your elegant source code for the Sevens and SevensGUI classes.

•     Source code – upload to Blackboard the Sevens.java and SevensGUI.java files.