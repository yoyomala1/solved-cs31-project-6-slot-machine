Download Link: https://assignmentchef.com/product/solved-cs31-project-6-slot-machine
<br>
<p id="yui_3_17_2_1_1596919763291_47" class="p1"><span id="yui_3_17_2_1_1596919763291_46" class="">Slot Machines are one of the most popular gambling methods in modern day casinos.  They typically account for approximately 70% of a US casino’s income.   Slot Machines include a currency detector which validates the money inserted to play.  Once a bet is accepted, the machine pays off when a certain combination of symbols appear on its front once the wheels stop spinning.  If you are unfamiliar with them, please spend a few moments playing one here: www.freeslots.com</span>

<p class="p1"><img decoding="async" alt="Slot Machine" width="462" height="260" data-src="./201A-COMSCI31-1_ Project 6_files/slotmachine.jpg" class="img-responsive atto_image_button_text-bottom lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

 <noscript>

  <img decoding="async" class="img-responsive atto_image_button_text-bottom" src="./201A-COMSCI31-1_ Project 6_files/slotmachine.jpg" alt="Slot Machine" width="462" height="260">

 </noscript>

<p class="p1">

<h3><b><span class="">Your Task</span></b></h3>

<p class="p1"><span class="">Based on a class-based template I will provide to you, your job will be to implement a random, three-wheel slot machine game.  Players will need to deposit funds into the machine in order to bet and play.  Once played, your slot machine will  randomly display a letter in each of three wheels.  Based on certain wheel patterns, your slot machine will pay off a multiple of what the player wagered on that round of play.</span>




<p class="p1"><span class="">Your assignment is to complete this C++ program skeleton (</span><span class=""> </span><span class=""><a href="http://www.howardstahl.com/ucla/summer20/project6/Project6SkeletonXCode.zip">XCode</a></span><span class=""> </span><span class=""> </span><span class=""> </span><span class=""><a href="http://www.howardstahl.com/ucla/summer20/project6/Project6SkeletonVS2019.zip">VS2019</a></span><span class=""> </span><span class="">) to produce a program that implements the described behavior. (We’ve indicated where you have work to do by comments containing the text </span><span class=""> </span><span class="">TODO</span><span class=""> </span><span class="">. Please remove those comments as you finish each thing you have to do.)  The program skeleton you are to flesh out defines five classes that represent the five kinds of objects this program works with: SlotMachine, Bank, PayTable, Screen and RandomNumber.  You will need to complete code for the SlotMachine, PayTable and Bank classes.  Details of the interface to all of these classes are in the program skeleton, but here are the essential responsibilities of each class:  </span>

<span class="">In order to simulate a real Slot Machine, a RandomNumber class has been provided to you.  The following UML class diagram describes the RandomNumber class. </span>

<img decoding="async" alt="RandomNumber Class Diagram" width="752" height="132" data-src="./201A-COMSCI31-1_ Project 6_files/RandomNumber.jpg" class="img-responsive atto_image_button_text-bottom lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

 <noscript>

  <img decoding="async" class="img-responsive atto_image_button_text-bottom" src="./201A-COMSCI31-1_ Project 6_files/RandomNumber.jpg" alt="RandomNumber Class Diagram" width="752" height="132">

 </noscript>

<span class="">The RandomNumber class provides a random integer value within a certain desired range of values.  When instantiated, you tell the RandomNumber constructor what the legal range of values you want.  By default, the range will potentially include the lower and upper bound value.  This behavior is configurable, so you can exclude the lower and upper bound, if you desire.  Please review the following driver code:</span>




<p class="p1"><span class="">RandomNumber die( 1, 6 );  // a six-sided die generating the random values 1-6</span><span class="">int toss = die.random( );</span><span class="">RandomNumber dayOfAugust( 0, 32, false, false );  // a day between 1-31</span><span class="">int day = dayOfAugust.random( );</span>

<p class="p1"><span class="">The RandomNumber class is fully implemented and does not require any student changes.  </span>

<p class="p1"><span class="">In order to simulate spinning wheels, a Screen class has been provided to you.  It provides the screen-related operations and is fully complete.  It gets called by the SlotMachine to display information about the current round of play back to the user.  The following UML class diagram describes the Screen class.</span>

<p class="p1"><span class=""><img decoding="async" alt="Screen Class Diagram" width="499" height="264" data-src="./201A-COMSCI31-1_ Project 6_files/Screen.png" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

  <noscript>

   <img decoding="async" src="./201A-COMSCI31-1_ Project 6_files/Screen.png" alt="Screen Class Diagram" width="499" height="264">

  </noscript></span>

<p class="p1"><span class="">In order to simulate the currency validator of a slot machine, a Bank class has been provided to you.  The Bank class will be used by the SlotMachine to hold player cash as it gets deposited, to verify that a bet can be wagered and to hold any winnings, as they occur.  As you will note, the Bank assumes whole-dollar increments and does not support fractional dollar amounts (coins).  The following UML class diagram describes the Bank class.</span>

<p class="p1"><span class=""><img decoding="async" alt="Bank Class Diagram" width="500" height="370" data-src="./201A-COMSCI31-1_ Project 6_files/RevisedBank.png" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

  <noscript>

   <img decoding="async" src="./201A-COMSCI31-1_ Project 6_files/RevisedBank.png" alt="Bank Class Diagram" width="500" height="370">

  </noscript></span>

<p class="p1">

<p class="p1"><span class="">The </span><span class="">bankAmount</span><span class=""> data member of the Bank class holds the total funds deposited by the player as well as winnings, if any.  The </span><span class="">wager</span><span class=""> data member of the Bank class holds the bet placed on the current turn of the SlotMachine.  In the beginning of time, the </span><span class="">bankAmount</span><span class=""> and </span><span class="">wager</span><span class=""> need to be set to zero.  The </span><span class="">bankAmount</span><span class=""> value gets increased when a player deposits funds into the Bank via calls to the method </span><span class="">deposit( int amount )</span><span class="">.  The </span><span class="">bankAmount</span><span class=""> value is fully returned to the player when the Bank is cashed out via calls to the method </span><span class="">cashOut( )</span><span class="">.  The Bank is used to determine whether there are sufficient funds available for a player to wager on a round of Slot Machine play.  The method </span><span class="">canWager( int amount )</span><span class=""> should return </span><span class="">true</span><span class=""> when there are sufficient funds (that is, the </span><span class="">wager</span><span class=""> being equal to or less than the available </span><span class="">bankAmount</span><span class="">); </span><span class="">false</span><span class=""> otherwise.  When a round of the Slot Machine game ends, the Bank can be told the amount that was won or lost on a round of Slot Machine play by a call to either </span><span class="">win( int amount )</span><span class=""> or </span><span class="">lose( int amount )</span><span class="">.  Please review the following driver code:</span>

<p class="p1"><span class="">Bank b;             // wager and bankAmount = 0</span><span class="">b.balance( );       // returns 0</span><span class="">b.canWager( 100 );  // returns false because there aren’t sufficient funds in this Bank</span><span class="">b.deposit( 50 );</span><span class="">b.balance( );       // returns 50</span><span class="">b.canWager( 100 );  // returns false because there aren’t sufficient funds in this Bank</span><span class="">b.deposit( 50 );  </span><span class="">b.canWager( 100 );  // returns true because there are sufficient funds</span><span class="">b.setWager( 100 );  // $100 has now been bet </span><span class="">b.getWager( );      // returns 100</span><span class="">b.balance( );       // returns 100 because the bet wager has not yet been won or lost</span><span class="">b.win( 100 );       // the wager was won</span><span class="">b.cashOut( );       // returns 200</span>

<p class="p1"><span class="">In the skeleton I have supplied, the Bank class is defined and implemented just enough to make the code compile.  CS 31 students need to read the</span><span class=""> </span><span class="">TODO </span><span class="">comments in Bank.h and Bank.cpp to complete the implementation of this class.  The Bank class must be finished first before moving on to the SlotMachine class. </span>

<p class="p1"><span class="">The class PayTable is defined to implement machine payouts and to update a player’s Bank.  The following UML diagram describes the PayTable class:</span>

<p class="p1"><img decoding="async" alt="PayTable Class Diagram" width="499" height="196" data-src="./201A-COMSCI31-1_ Project 6_files/RevisedPaytable.png" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

 <noscript>

  <img decoding="async" src="./201A-COMSCI31-1_ Project 6_files/RevisedPaytable.png" alt="PayTable Class Diagram" width="499" height="196">

 </noscript>

<p class="p1"><span class="">The SlotMachine class will provide its three wheel values to the PayTable when a PayTable object is created.  Based on those wheel values, a PayTable can determine the appropriate Multiplier for that round of play.  A Multiplier is an enumerated value representing different possible slot machine payouts.  The following UML diagram describes the enumeration Multiplier:</span>

<p class="p1"><img decoding="async" alt="Multiplier Enumeration" width="500" height="133" data-src="./201A-COMSCI31-1_ Project 6_files/MultiplierEnumeration.png" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

 <noscript>

  <img decoding="async" src="./201A-COMSCI31-1_ Project 6_files/MultiplierEnumeration.png" alt="Multiplier Enumeration" width="500" height="133">

 </noscript>

<span class="">As its name suggested, calculateMultiplier( ) returns a Multiplier based on the current wheel values in this PayTable.  By reviewing the value of the wheels, calculateMultiplier( ) should implement the following pays of winning plays: </span>




<table>

 <tbody>

  <tr>

   <th><span class="">Description              </span></th>

   <th><span class="">Winning Rate          </span></th>

   <th><span class="">createMultiplier( )</span><span class="">returns</span></th>

  </tr>

  <tr>

   <td><span class="">a single Ace  <u>as long as not a 5-to-1 straight</u></span></td>

   <td><span class="">1-to-1</span></td>

   <td><span class="">PayTable::Multiplier::ONETIME</span></td>

  </tr>

  <tr>

   <td><span class="">two Aces  </span></td>

   <td><span class="">5-to-1</span></td>

   <td><span class="">PayTable::Multiplier::FIVETIME</span></td>

  </tr>

  <tr>

   <td><span class="">any pair other than Aces </span></td>

   <td><span class="">3-to-1</span></td>

   <td><span class="">PayTable::Multiplier::THREETIME</span></td>

  </tr>

  <tr>

   <td><span class="">any pair other than Aces + Ace</span></td>

   <td><span class="">4-to-1</span></td>

   <td><span class="">PayTable::Multiplier::FOURTIME</span></td>

  </tr>

  <tr>

   <td><span class="">three Aces  </span></td>

   <td><span class="">10-to-1</span></td>

   <td><span class="">PayTable::Multiplier::TENTIME</span></td>

  </tr>

  <tr>

   <td><span class="">three of a kind other than Aces  </span></td>

   <td><span class="">7-to-1</span></td>

   <td><span class="">PayTable::Multiplier::SEVENTIME</span></td>

  </tr>

  <tr>

   <td><span class="">AKQ <del>or QKA</del>  <u>in any order (which means AKQ, KAQ, QKA, KQA, QAK, AQK)</u> </span></td>

   <td><span class="">5-to-1 </span></td>

   <td><span class="">PayTable::Multiplier::FIVETIME</span></td>

  </tr>

  <tr>

   <td><del>three of a kind other than Aces  </del></td>

   <td><del>7-to-1</del><del></del></td>

   <td><del>PayTable::Multiplier::SEVENTIME</del></td>

  </tr>

  <tr>

   <td><span class="">any other spins</span></td>

   <td><span class="">Lost Wager</span></td>

   <td><span class="">PayTable::Multiplier::ZERO</span></td>

  </tr>

 </tbody>

</table>




<span class="">As its name suggests, manageWager( Bank &amp; ) should update the Bank based on the Multiplier for the current wheel values in this PayTable by calling the Bank’s .win( int ) or .lose( int ) method.</span>

<p class="p1"><span class="">Finally. the SlotMachine class implements the gaming machine.  The SlotMachine has three data members for the wheels of the machine (</span><span class="">wheel1</span><span class="">, </span><span class="">wheel2</span><span class=""> and </span><span class="">wheel3</span><span class="">)</span><span class=""> and has a data member of type </span><span class="">string</span><span class=""> named </span><span class="">sequence</span><span class=""> which provide the letters that should be displayed as the individual wheels of the machine spin during play and also has a boolean member named display which is tracking whether play display output is desired.  One version of the .play( … ) method randomly picks the wheel values.  The other version of .play( … ) accepts the wheel values so that your code can be properly tested.  The SlotMachine constructor should be passed the sequence of letters to display for the spinning wheels feature.  When played interactively with user output, call .showDisplay( ) to print the spinning wheels as play occurs.  To test programmatically without output and pauses, call .noDisplay( ) prior to a round of play.  The following UML class diagram describes the SlotMachine class.</span>

<p class="p1"><img decoding="async" alt="SlotMachine Class Diagram" width="750" height="655" data-src="./201A-COMSCI31-1_ Project 6_files/SlotRefactored3.png" class="img-responsive atto_image_button_text-bottom lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

 <noscript>

  <img decoding="async" class="img-responsive atto_image_button_text-bottom" src="./201A-COMSCI31-1_ Project 6_files/SlotRefactored3.png" alt="SlotMachine Class Diagram" width="750" height="655">

 </noscript>

<p class="p1"><span class="">Trivial accessor methods are provided for each of the wheel values.  The internal operations spinWheels( ) and updateBankFromSpinAndDisplay( ) need to be called when the game is played. </span>

<p class="p1"><span class="">The sample main( ) I have provided in the skeleton prompts the user for commands to run using the following format:</span>

<p class="p1">

<ul>

 <li><span class="">d#</span><span class="">   (as in,   </span><span class="">d100</span><span class="">)</span><span class="">a command to deposit funds into the bank</span></li>

 <li><span class="">c </span><span class="">     </span><span class="">a command to cash out all the funds from the bank</span></li>

 <li><span class="">b#</span><span class="">   (as in,  </span><span class="">b50</span><span class="">)</span><span class="">a command to bet an amount on the next round of play.  To be accepted, the amount bet (called the wager) must not exceed the available funds in the SlotMachine’s bank.  A bet must be placed by the user before a round of play is allowed.     </span></li>

 <li><span class="">p</span><span class="">a command to spin the wheels of the machine.  If a winning round happens, the SlotMachine needs to credit its bank accordingly.  If a losing round happens, the SlotMachine needs to reduce its bank accordingly.</span></li>

 <li><span class="">q</span><span class="">a command to quit the game which will end the program</span></li>

</ul>

<span class="">The skeleton I have provided for you will compile and run but not many of these commands will not work correctly because the Bank, PayTable and certain SlotMachine operations have been left blank.  Once you complete the Bank class, your next task will be to complete PayTable and then the SlotMachine class.</span>

<p class="p1">

<p class="p1">

<span class="">You are free to create additional public and private methods and data members as you see fit.  However, the test cases will only be driving the public methods of the SlotMachine and Bank classes diagrammed here.</span>

<span class="">The source files (.h and .cpp) from all these classes will be what you turn in along with a main routine. You can have the main routine do whatever you want, because we will rename it to something harmless, never call it, and append our own main routine to your file. Our main routine will thoroughly test your functions. You’ll probably want your main routine to do the same. If you wish, you may write functions in addition to those required here. We will not directly call any such additional functions. If you wish, your implementation of a function required here may call other functions required here.</span>







<span class="">The program you turn in must build successfully, and during execution, no method may read anything from </span><code><span class="">cin</span></code><span class="">. If you want to print things out for debugging purposes, write to </span><code><span class="">cerr</span></code><span class=""> instead of </span><code><span class="">cout</span></code><span class="">. When we test your program, we will cause everything written to </span><code><span class="">cerr</span></code><span class=""> to be discarded instead — we will never see that output, so you may leave those debugging output statements in your program if you wish.</span>

<span class="">Please read the posted </span><a href="https://ccle.ucla.edu/mod/page/view.php?id=1178689"><span class="">FAQ</span></a><span class=""> </span><span class="">for further assistance.  There are also <a href="https://ccle.ucla.edu/mod/resource/view.php?id=2992874">supplemental slides</a> covering many of these ideas available for you to review.</span>

<span class="">Additionally, I have created a testing tool called CodeBoard to help you check your code.  CodeBoard enables you to be sure you are naming things correctly by running a small number of tests against your code.  Passing CodeBoard tests is not sufficient testing so please do additional testing yourself.  To access CodeBoard for Project 6, please click the link you see in this week named CodeBoard for Project 6.  The default student skeleton code has been loaded there.  Inside the files named Bank.h, Bank.cpp, PayTable.h, PayTable.cpp, SlotMachine.h and SlotMachine.cpp, copy and paste the versions you have developed.  CodeBoard uses its own main( ) to run tests against your code so you won’t get any opportunity to provide a main( ) function.  Click Compile and Run.  However please be aware that no editing changes can be saved inside CodeBoard.  In this anonymous user configuration, CodeBoard is read-only and does not allow for saving changes.</span>

<h3><b>Programming Guidelines</b></h3>

<span class="">Your program must </span><em><span class="">not</span></em><span class=""> use any function templates from the algorithms portion of the Standard C++ library or use STL &lt;list&gt; or &lt;vector&gt;.  </span><span class="">Your implementations must </span><i><span class="">not</span></i><span class=""> use any global variables (that is, variables declared outside the scope of main or a class…) whose values may get changed during execution.</span>

<span class="">Your program must build successfully under both Visual C++ and either clang++ or g++.</span>

<span class="">The correctness of your program must not depend on undefined program behavior. </span>

<span class="">What you will turn in for this assignment is a zip file named </span><span class=""><b>Project6 </b></span><span class="">containing the following 12 files and nothing more:</span>

<ol>

 <li><span class="">The text files </span><span class="">named </span><span class="">  </span><b><span class="">Bank.h </span><span class=""> </span></b><span class=""> </span><span class="">and </span><b><span class="">Bank.cpp</span><span class=""> </span></b><span class=""> </span><span class=""> that implement the </span><span class="">Bank</span><span class=""> class diagrammed above, t</span><span class="">he text files </span><span class="">named </span><span class="">  </span><b><span class="">SlotMachine.h </span><span class=""> </span></b><span class=""> </span><span class="">and </span><span class="">  </span><b><span class="">SlotMachine.cpp</span><span class=""> </span></b><span class=""> </span><span class=""> that implement the </span><span class="">SlotMachine</span><span class=""> class diagrammed above, the text files named     </span><b><span class="">RandomNumber.h </span><span class=""> </span></b><span class=""> </span><span class="">and </span><span class="">  </span><b><span class="">RandomNumber.cpp</span><span class=""> </span></b><span class="">   </span><span class="">that implement the </span><span class="">RandomNumber</span><span class=""> class diagrammed above, the text files named     <b>Screen.h  </b> and   <b>Screen.cpp </b>   that implement the Screen class diagrammed above,  the text files named     <b>PayTable.h  </b> and   <b>PayTable.cpp </b>   that implement the PayTable class diagrammed above, and the text file named </span><b><span class="">main.cpp</span><span class=""> </span></b><span class=""> </span><span class="">which will hold your main program</span><span class="">. Your source code should have helpful comments that explain any non-obvious code.</span></li>

 <li><span class="">A file named </span><b><span class="">report.doc</span></b><span class=""> or </span><b><span class="">report.docx</span><span class=""> </span></b><span class=""> </span><span class=""> (in Microsoft Word format), or </span><b><span class="">report.txt</span><span class=""> </span></b><span class=""> </span><span class=""> (an ordinary text file) that contains:</span>

  <ol>

   <li><span class="">A brief description of notable obstacles you overcame.</span></li>

   <li><span class="">A list of the test data that could be used to thoroughly test your functions, along with the reason for each test. You must note which test cases your program does not handle correctly. (This could happen if you didn’t have time to write a complete solution, or if you ran out of time while still debugging a supposedly complete solution.) Notice that most of this portion of your report can be written just after you read the requirements in this specification, before you even start designing your program.</span></li>

  </ol></li>

</ol>

<span class="">As with Project 3 and 4 and 5, a nice way to test your functions is to use the </span><code><span class="">assert</span></code><span class=""> facility from the standard library. As an example, here’s a very incomplete set of tests for Project 6.  Again, please build your solution incrementally.  So I wouldn’t run all these tests from the start because many of them will fail until you have all your code working.  But I hope this gives you some ideas….</span>

<pre>	#include &lt;iostream&gt;	#include &lt;string&gt;	#include &lt;cassert&gt;        #include "Bank.h"        #include "PayTable.h"        #include "SlotMachine.h"                   	using namespace std;	int main()	{           using namespace std;           using namespace cs31;</pre>

<pre><span class="s3">           </span><span class="s2">// test code           Bank b;           assert( b.balance() == 0 );           assert( b.getWager() == 0 );           assert( !b.canWager( 100 ) );           b.deposit( 50 );           assert( b.balance() == 50 );           assert( !b.canWager( 100 ) );           assert( b.canWager( 50 ) );           b.deposit( 50 );           PayTable p( 'A', 'A', 'A' );           PayTable::Multiplier m = p.calculateMultiplier( );  // 3 Aces is a 10-1 winner           assert( m == PayTable::Multiplier::TENTIME );</span></pre>

<p class="p1"><span class="s1">           SlotMachine s( </span><span class="s3">“AKQJ987”</span><span class="s1"> ); // cheating… b.setWager( 100 ); s.play( b, ‘A’, ‘A’, ‘A’ ); assert( b.balance( ) == 1100 ); // 3 Aces is 10-1 winner and a round of play adjusts the bank</span>

<p class="p3"><span class="s2">      </span><span class="s8">cout</span><span class="s3"> &lt;&lt; </span><span class="s2">“all tests passed!”</span><span class="s3"> &lt;&lt; </span><span class="s9">endl</span><span class="s3">; </span><span class="s2">     </span><span class="s1">return</span> <span class="s5">0</span><span class="s2">;</span>

<p class="p1"><span class="s2"> }</span>

<pre></pre>

<span class="">By August 14th, there will be links on the class webpage that will enable you to turn in your zip file electronically. Turn in the file by the due time above. Give yourself enough time to be sure you can turn something in, because we will not accept excuses like “My network connection at home was down, and I didn’t have a way to copy my files and bring them to a SEASnet machine.” There’s a lot to be said for turning in a preliminary version of your program and report early (You can always overwrite it with a later submission). That way you have something submitted in case there’s a problem later.</span>




<h3><b>G31 Build Commands </b></h3>

<span class="">g31 -c Bank.cpp</span><span class="">g31 -c PayTable.cppg31 -c RandomNumber.cppg31 -c Screen.cppg31 -c SlotMachine.cpp</span><span class="">g31 -c main.cpp</span><span class="">g31 -o runnable    main.o    Bank.o    PayTable.o.  RandomNumber.o    Screen.o.  SlotMachine.o</span><span class="">./runnable</span>