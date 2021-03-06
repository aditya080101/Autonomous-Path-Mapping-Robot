<html>
<body>
    
<h1 align=center> Vision 2.0 </h1>
    
<p align=center>
    <img align=center src = "media/arena.gif" alt = "Arena" width = "250">
    <img align=center src = "media/husky.gif" alt = "Bot" width = "250"> 
</p>
    
<h3> Problem Statement</h3>

1. There are <b>2 paths</b> in our arena (<i>inner</i> and <i>outer</i> square) with <b>4 connecting paths</b> of different colours joining them. <br>
2. Bot can change from outer path to inner path or vice versa. Bot is allowed to move in <b> clockwise direction </b> only. 
3. The portion of the arena in <b> black colour </b> is restricted for the movement of the bot. <br>
4. There will be <b>3 shapes</b> (<i>square, circle</i> and <i>triangle</i>) of <b>2 different colours</b> (<i>red</i> and <i>yellow</i>), distinguishing each block in 6 different ways. <br>
5. On the outermost path there will be <b>4 black arrows</b> at the end of connecting paths pointing in clockwise direction. These arrows mark the <b> starting zone </b> where the bot will be placed initially on any one of the arrows. <br>
6. The centre of the arena is the <b>home zone</b>. The bot has to traverse the arena, complete a full round in a clockwise manner and finish at the home zone. <br>

<h3> Task To Do</h3>

1. The bot is placed on one of the <b>starting zones</b> (represented by 4 black arrows). <br>
2. An abbreviation which associate to specific colour and shape. <br>

<table align=center>
   <td align="center">
         <img src="https://i.gyazo.com/895b7ba241c10848fb4b664a480a36bf.png" width="100px;" alt=""/>
         <br />
         <sub>
             <b>TR : <em>Red Triangle</em></b>
         </sub>
      <br />
   </td>
   <td align="center">
         <img src="https://i.gyazo.com/908678469cea8f95f04549d0d02dea6e.png" width="100px;" alt=""/>
         <br />
         <sub>
             <b>SR : <em>Red Square</em></b>
         </sub>
      <br />
   </td>
   <td align="center">
         <img src="https://i.gyazo.com/e8d85fb4f53b58cd0d49655328ab909b.png" width="100px;" alt=""/>
         <br />
         <sub>
             <b>CR : <em>Red Circle</em></b>
         </sub>
      <br />
   </td>
   <td align="center">
         <img src="https://i.gyazo.com/72ab1c3524c968f7f142526dd48487e7.pngg" width="100px;" alt=""/>
         <br />
         <sub>
             <b>CY : <em>Yellow Circle</em></b>
         </sub>
      <br />
   </td>
   <td align="center">
         <img src="https://i.gyazo.com/9f9feec55eed87f775fd18e4ed92ef56.png" width="100px;" alt=""/>
         <br />
         <sub>
             <b>SY : <em>Yellow Square</em></b>
         </sub>
      <br />
   </td>
   <td align="center">
         <img src="https://i.gyazo.com/32ee8196e737e9acf97434205d7a0445.png" width="100px;" alt=""/>
         <br />
         <sub>
             <b>TY : <em>Yellow Triangle</em></b>
         </sub>
      <br />
   </td>
</table>
    
3. On start of each turn, a function returns a **random shape-color** combination from the list above.The bot must then find the closest block (with the corresponding shape) which it can reach following a clockwise path. <br>
4. As soon as the bot stops moving, bot has to ask for input using the function provided. <br>
5. This continues till the <b>bot has completed a full round around the center</b>, then it should move to home via the connecting paths that it started on. <br>
6. On reaching home the bot should signal that it has finished the task. <br>
    
<h3 align=center> Our Approach </h3>
    
1. We used <b> Computer Vision</b> for <i>image segmentation</i> i.e. extracting shapes of different colors from the arena. Used <b>Breadth First Search</b> algorithm (on a customly designed <i>directed graph</i>) to trace path from the current position of the bot to all occurences of the corresponding shape in the arena. From all the paths secured above, one with minimum length was considered. Popular physics engine <b>PyBullet</b> was utilized for simulating our bot on the arena. <b>Aruco Marker</b> was used to determine the current position of the bot at any instant. <br>
2. First, a <b>directed graph</b> is created, in which edges are added in the direction of allowed movement. <br>
3. <b>Shape</b> and <b>Color</b> in each grid of the arena is detected using several techniques such as masking, erosion, dilation and contour approximation.<br>
4. A function (<code>roll_dice</code> in our case) returns a <i>shape-color</i> combination to the bot in order to figure out the next destination to visit. <br>
5. Then, <b>BFS</b> (<i>Breadth First Search</i>) is used to determine the all possible paths from the current position to the next destination. Among the paths secured, one with minimum length is considered for traversal <br>
6. Two <b>vectors</b> are created providing the positions, along with the angles, of the bot and the destination grid. Various custom-made functions, such as <code>dist()</code>, <code>ang()</code>, <code>rotate()</code> and <code>move()</code>, are employed in order to facilitate the movement of the bot. <br>
7. After the bot crosses the first grid, the <i>graph edges are altered</i> in a way that the bot enters the home after completion of a clockwise round and doesn't retrace the previous path.The task is completed after the bot reaches the central home grid.<br>
8. Video of the run is provided in the repository <br>
 
</body>
</html>
