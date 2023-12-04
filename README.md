<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" media="screen" href="https://cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/3.3.5/css/bootstrap.min.css">

    <title>Minimum Bootstrap HTML Skeleton</title>

    <!--  -->

    <style>
    </style>

</head>

<body>




    <div class="container">

        <div id='show'>


            <h3> NUMBA NUMBA</h3>
            <h3>Minimum wallet is R10, everytime you submit your gamble you will be charged R2. select 4 numbers between 1 and 20. If you get a match you win! One number will get you R2, Two numbers will win R4, three numbers is R16, and the jackpot of four wins you R64. You can play the same numbers as many times as you would like, or choose new numbers everytime. Once you run out of cash in your wallet you need to recharge  Good luck! </p>

            <button onClick="tikBought()">Buy Ticket</button>

            <br/>
            <p id='currentWallet'></p>


            <br/>
            <!--
<form>
   <label>Choice 1</label>
   <input type="number" id="num1" max='20' min='1'/>
    <label>Choice 2</label>
   <input type="number" id="num2" max='20' min='1'/>
    <label>Choice 3</label>
   <input type="number" id="num3" max='20' min='1'/>
    <label>Choice 4</label>
   <input type="number" id="num4" max='20' min='1'/>
</form>
<br/>
   <button onClick="startGame()"> Submit </button>
   <div id="showUserA"></div>
<br/>
            <br/>
-->
            <!--
   <p> Now that you have selected your numbers, lets gamble!  hit the play button below to test your luck!</p>
    <br/>
   <button id='' onclick='getInput()'>Play</button>
-->




        </div>

    </div>









    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/3.3.5/js/bootstrap.min.js"></script>

    <script>
        var wallet = 0;
        var numArray = [];
        var userChoiceArray = [];
        var arr = [];
        var tempArray = [];
        var matchArray = [];
        var newWallet = 0;
        var unique = false;
        function tikBought() {
            var text = '';
            text += '<div id="currentWallet"></div>';
            text += '<button onClick="buyIn()">Play</button>';
            document.getElementById('show').innerHTML = text;
            costToBuyIn(10);
        }
        function buyIn() { //play button
            var text = '';
            text += '<div id="currentWallet"></div>';
            text += '<div id="winnings"></div>';
            text += ' <form>';
            text += '<label>Choice 1</label>';
            text += '<input type="number" id="num1" max="20" min="1" required/> ';
            text += ' <label>Choice 2</label>';
            text += '<input type="number" id="num2" max="20" min="1" required/> ';
            text += ' <label>Choice 3</label>';
            text += '<input type="number" id="num3" max="20" min="1" required/> ';
            text += ' <label>Choice 4</label>';
            text += '<input type="number" id="num4" max="20" min="1" required/> ';
            text += '</form>';
            text += '<br/>';
            text += '<button onClick="startGame()"> Submit </button> ';
            document.getElementById('show').innerHTML = text;
            document.getElementById('winnings').innerHTML = "winnings: " + "R" + newWallet;
            document.getElementById('currentWallet').innerHTML = "Current Wallet: " + parseInt(wallet + newWallet);
        }
        function costToBuyIn(num) {
            wallet = wallet + num;
            document.getElementById('currentWallet').innerHTML = "You have " + "R" + wallet + " to gamble! Hit 'play' to test your luck!";
        }
        function costToPlay(num) {
            wallet = wallet - num;
            document.getElementById('currentWallet').innerHTML = "It cost R2 to gamble. Money Left: " + "R" + totalWallet();
        }
        //maybe i will use this
        function totalWallet() {
            return newWallet + wallet;
        }
        function startGame() { //submit button
            // make re runnable
            //play again button that starts it all over again  currently I am at a dead end with play button
            var choice1 = parseInt(document.getElementById('num1').value);
            if (parseInt(document.getElementById('num1').value) > 20 || parseInt(document.getElementById('num1').value) <= 0) {
                alert('please make sure all your numbers are between 1 and 20')
                return;
            }
            var choice2 = parseInt(document.getElementById('num2').value);
            if (parseInt(document.getElementById('num2').value) > 20 || parseInt(document.getElementById('num2').value) <= 0) {
                alert('please make sure all your numbers are between 1 and 20')
                return;
            }
            var choice3 = parseInt(document.getElementById('num3').value);
            if (parseInt(document.getElementById('num3').value) > 20 || parseInt(document.getElementById('num3').value) <= 0) {
                alert('please make sure all your numbers are between 1 and 20')
                return;
            }
            var choice4 = parseInt(document.getElementById('num4').value);
            if (parseInt(document.getElementById('num4').value) > 20 || parseInt(document.getElementById('num4').value) <= 0) {
                alert('please make sure all your numbers are between 1 and 20')
                return;
            }
            userChoiceArray.push(choice1);
            userChoiceArray.push(choice2);
            userChoiceArray.push(choice3);
            userChoiceArray.push(choice4);
            // esta no bueno
            var tempUserArray = [];
            tempUserArray.push(choice1, choice2, choice3, choice4);
            console.log(tempUserArray);
            for (var i = 0; i < tempUserArray.length; i++) {
                if (tempUserArray[i] == tempUserArray) {
                    prompt('NO!');
                    return;
                }
            }
            //check for matching user picks
            if (choice1 == choice2) {
                alert('Please Choose new numbers that do not match');
                userChoiceArray = [];
                buyIn();
                return;
            }
            if (choice1 == choice3) {
                alert('Please Choose new numbers that do not match');
                userChoiceArray = [];
                buyIn();
                return;;
            }
            if (choice1 == choice4) {
                alert('Please Choose new numbers that do not match');
                userChoiceArray = [];
                buyIn();
                return;;
            }
            if (choice2 == choice1) {
                alert('Please Choose new numbers that do not match');
                userChoiceArray = [];
                buyIn();
                return;;
            }
            if (choice2 == choice3) {
                alert('Please Choose new numbers that do not match');
                userChoiceArray = [];
                buyIn();
                return;;
            }
            if (choice2 == choice4) {
                alert('Please Choose new numbers that do not match');
                userChoiceArray = [];
                buyIn();
                return;;
            }
            if (choice3 == choice1) {
                alert('Please Choose new numbers that do not match');
                userChoiceArray = [];
                buyIn();
                return;;
            }
            if (choice3 == choice2) {
                alert('Please Choose new numbers that do not match');
                userChoiceArray = [];
                buyIn();
                return;;
            }
            if (choice3 == choice4) {
                alert('Please Choose new numbers that do not match');
                userChoiceArray = [];
                buyIn();
                return;;
            }
            if (choice4 == choice1) {
                alert('Please Choose new numbers that do not match');
                userChoiceArray = [];
                buyIn();
                return;;
            }
            if (choice4 == choice2) {
                alert('Please Choose new numbers that do not match');
                userChoiceArray = [];
                buyIn();
                return;;
            }
            if (choice4 == choice3) {
                alert('Please Choose new numbers that do not match');
                userChoiceArray = [];
                buyIn();
                return;
            }
            var text = '';
            text += '<div id="currentWallet"></div>';
            text += '<div id="showUserA"></div>';
            text += '<br/>';
            text += '<p> Now that you have selected your numbers,  hit the button below to test your luck!</p>';
            text += '<br/>';
            text += '<button id="" onclick="getInput()">Check Winning Numbers</button>';
            document.getElementById('show').innerHTML = text;
            costToPlay(2);
            userPicks();
        }
        //display user numbers
        function userPicks() {
            if (userChoiceArray.length = 4) {
                document.getElementById('showUserA').innerHTML = 'your choices are: ' + userChoiceArray;
            }
        }
        // randomNum generator
        function getInput() { //Check Winning Numbers Button 
            while (arr.length < 4) {
                var randomnumber = Math.ceil(Math.random() * 20)
                var found = false;
                for (var i = 0; i < arr.length; i++) {
                    if (arr[i] == randomnumber) {
                        found = true;
                        break
                    }
                }
                if (!found) arr[arr.length] = randomnumber;
            }
            console.log(arr);
            var text = '';
            text += '<div id="compChoices"></div>';
            text += '<button onClick="rePlay()">play again?</button>'; //function bottom of page
            text += '<button onClick="endGame()">No Thanks</button>'; //see above 
            document.getElementById('show').innerHTML = text;
            checkMatches();
        }
        //will check if user matched computer
        function checkMatches() {
            //set array to empty
            tempArray = [];
            for (var i = 0; i < arr.length; i++) {
                if (arr.indexOf(userChoiceArray[i]) == -1) {
                    console.log(userChoiceArray.indexOf(arr[i]));
                    tempArray.push(arr[i]);
                    //console.log(tempArray);
                    document.getElementById('compChoices').innerHTML = 'You got ' + matches1() + ' matches!';
                }
            }
            prizeMoney();
        }
        function matches1() {
            return (tempArray.length - 4) * -1; //this is causing my initial length to equal 4, but is a good bandaid for my random numbers
        }
        //calculates winning amount for matches
        function prizeMoney() {
            if (matches1() == 1) {
                newWallet = newWallet + 2;
                return wallet + 2;
            }
            if (matches1() == 2) {
                newWallet = newWallet + 4;
                return wallet + 4;
            }
            if (matches1() == 3) {
                newWallet = newWallet + 16;
                return wallet + 16;
            }
            if (matches1() == 4) {
                newWallet = newWallet + 64;
                return wallet + 64;
            }
            if (matches1() == 0) {
                return wallet;
            }
        }
        //play again button
        function rePlay() {
            userChoiceArray.length = 0;
            numArray.length = 0;
            tempArray.length = 0; //need to figure out how to reset random temp array
            arr.length = 0;
            if (totalWallet() <= 2) {
                document.getElementById('show').innerHTML = "Sorry you are out of balance please,recharge your account";
            } else {
                buyIn();
            }
        }
        //done playing button
        function endGame() {
            document.getElementById('show').innerHTML = "Thanks for playing! Your total Winnings are: " + "R" + parseInt(wallet + newWallet);
        }
        //document.getElementById('currentWallet').innerHTML = "Current Wallet: " +parseInt(wallet + newWallet);
        //generates four distinct random numbers between 1 and 10 inclusive which are shown to user
        //get the values from the form
        //validate the input
        //make sure they can afford the ticket
        //validation rules are
        //four numbers all unique display error message if user has choosen an incorrect number
        //compare user input to chosen numbers
        //store choices //decide how to store them use either variables or arraya
        //if no matches no money
        //if 1 match = R2  win
        //if 2 match = R4  win
        //if 3 match = R16 win
        //if 4 match = R64 win
        //adjust wallet only if they won since we already deducted
        //show user results
        //start again
    </script>

</body>

</html>

