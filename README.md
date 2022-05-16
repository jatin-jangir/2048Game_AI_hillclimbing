# 2048Game_AI_hillclimbing
Artificial Intelligence help us to play 2048 game. I have used hill climbing using an evaluation function. 

the 2048 game is invented by gabriele cirulli.
this game work around the concept of adding numbers to reach particular number that is 2048.
initiallly, we have 5x5 baord 
[
[0,0,0,0,0],
[0,0,0,0,0],
[0,0,0,0,0],
[0,0,0,0,0],
[0,0,0,0,0]
]
we place 2 at any random place which contains 0 after every move made by user.

moves --->
there are 4 move that is left, right, up and down.

let say we are on state
[
[0,0,0,2,0],
[0,2,0,2,0],
[0,0,4,0,0],
[0,0,8,0,4],
[0,0,0,0,0]
]

(without randomly place 2)
after left move -->

[
[2,0,0,0,0],
[4,0,0,0,0],
[4,0,0,0,0],
[8,4,0,0,0],
[0,0,0,0,0]
]

after right move -->

[
[0,0,0,0,2],
[0,0,0,0,4],
[0,0,0,0,4],
[0,0,0,4,8],
[0,0,0,0,0]
]

after up move -->

[
[0,2,4,4,4],
[0,0,8,0,0],
[0,0,0,0,0],
[0,0,0,0,0],
[0,0,0,0,0]
]

after down move -->

[
[0,0,0,0,0],
[0,0,0,0,0],
[0,0,0,0,0],
[0,0,4,0,0],
[0,2,8,4,4]
]

Evaluating Function 
 
we evaluate the state based on the product manhattan distance between 
the highest number and corresponding block to their weights.

example --

[
[0,0,0,0,0],
[0,0,0,0,0],
[0,0,0,0,256],
[0,0,512,0,0],
[0,2,1024,4,4]
]

here, position of max weight block is (4,2)
then
evaluating function = 
256*(absolute(2-4)+absolute(4-2)) + 
512*(absolute(3-4)+absolute(2-2)) +
2*(absolute(4-4)+absolute(1-2)) +
4*(absolute(4-4)+absolute(3-2)) +
4*(absolute(4-4)+absolute(4-2))
					
= 256 * 4 + 512 * 1  + 2 * 1 + 4 * 1 +4 * 2
=1550

we have to evaluate the value of evaluating function of all next state 
of the state we currently present at and suggest the best possible move 
to user whenever he/she request for help.
