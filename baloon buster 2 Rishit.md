var Background=createSprite(200,200,World.width,World.height);
Background.setAnimation("sunshine_showers");
var balloon1=createSprite(49,53,10,10);
balloon1.velocityX=-5;
balloon1.setAnimation("ball");
balloon1.scale=0.1;
var balloon2=createSprite(111,53,10,10);
balloon2.velocityX=-5;
balloon2.setAnimation("ball");
balloon2.scale=0.1;
var balloon3=createSprite(171,53,10,10);
balloon3.velocityX=-5;
balloon3.setAnimation("ball");
balloon3.scale=0.1;
var balloon4=createSprite(231,53,10,10);
balloon4.velocityX=-5;
balloon4.setAnimation("ball");
balloon4.scale=0.1;
var balloon5=createSprite(301,53,10,10);
balloon5.velocityX=-5;
balloon5.setAnimation("ball");
balloon5.scale=0.1;
var balloon6=createSprite(371,53,10,10);
balloon6.velocityX=-5;
balloon6.setAnimation("ball");
balloon6.scale=0.1;
var bow=createSprite(198,361,20,20);
bow.setAnimation("bow");
bow.scale=0.5;
var arrow=createSprite(230,345,2,30);
arrow.shapeColor="blue";
var lifeline=3;
var bc=0;
var gameState="start";
function draw() {
  background("white");
  drawSprites();
  bow.x=World.mouseX;
  arrow.x=bow.x;
  textSize(20);
  fill("red");
  text(lifeline,364,320);
  textSize(15);
  fill("red");
  text("Lifeline",348,290);
  text(bc,200,200);
  if(balloon1.x<0){
    balloon1.x=World.height;
  }
  if(balloon2.x<0){
    balloon2.x=World.height;
  }
  if(balloon3.x<0){
    balloon3.x=World.height;
  }
  if(balloon4.x<0){
    balloon4.x=World.height;
  }
  if(balloon5.x<0){
    balloon5.x=World.height;
  }
  if(balloon6.x<0){
    balloon6.x=World.height;
  }
  if(gameState==="start"){
    fill("yellow");
    text("Press space to shoot",130,200);
  }
  if((keyDown("space"))&&(gameState==="start")){
  hit();
  gameState="play";
  }
   if(arrow.y<0){
     arrow.x=230;
     arrow.y=345;
     arrow.velocityY=0;
      arrow.velocityX=0;
    lifeline=lifeline-1;
    playSound("sound://category_explosion/puzzle_game_break_magic_04.mp3");
    gameState="start";
  }
  if((arrow.bounce(balloon1))&&(gameState==="play")){
    arrow.x=230;
    arrow.y=345;
    arrow.velocityY=0;
    arrow.velocityX=0;
    balloon1.y=1000;
    balloon1.velocityY=0;
    playSound("sound://category_hits/vibrant_crate_break_2.mp3");
    gameState="start";
    bc=bc+1;
  }
if((arrow.bounce(balloon2))&&(gameState==="play")){
    arrow.x=230;
    arrow.y=345;
    arrow.velocityY=0;
    arrow.velocityX=0;
    balloon2.y=1000;
    balloon2.velocityY=0;
    playSound("sound://category_hits/vibrant_crate_break_2.mp3");
    gameState="start";
  }
  if((arrow.bounce(balloon3))&&(gameState==="play")){
    arrow.x=230;
    arrow.y=345;
    arrow.velocityY=0;
    arrow.velocityX=0;
    balloon3.y=1000;
    balloon3.velocityY=0;
    playSound("sound://category_hits/vibrant_crate_break_2.mp3");
    gameState="start";
  }
  if((arrow.bounce(balloon4))&&(gameState==="play")){
    arrow.x=230345;
    arrow.y=345;
    arrow.velocityY=0;
    arrow.velocityX=0;
    balloon4.y=1000;
    balloon4.velocityY=0;
    playSound("sound://category_hits/vibrant_crate_break_2.mp3");
    gameState="start";
  }
    if((arrow.bounce(balloon5))&&(gameState==="play")){
    arrow.x=230;
    arrow.y=345;
    arrow.velocityY=0;
    arrow.velocityX=0;
    balloon5.y=1000;
    balloon5.velocityY=0;
    playSound("sound://category_hits/vibrant_crate_break_2.mp3");
    gameState="start";
  }
  if((arrow.bounce(balloon6))&&(gameState==="play")){
    arrow.x=230;
    arrow.y=345;
    arrow.velocityY=0;
    arrow.velocityX=0;
    balloon6.y=1000;
    balloon6.velocityY=0;
    playSound("sound://category_hits/vibrant_crate_break_2.mp3");
    gameState="start";
  }
  if(lifeline===0){
  gameState="over";
  textSize(20);
  fill("red");
  text("You Lost",150,200);
  playSound("sound://category_bell/bells_win_low.mp3");
  }
  if((balloon1.y>400)&&(balloon2.y>400)&&(balloon3.y>400)&&(balloon4.y>400)&&(balloon5.y>400)&&(balloon6.y>400)){
  gameState="over";
  textSize(20);
  fill("yellow");
  text("You Win",150,200);
  playSound("sound://category_music/gameover.mp3");
}
if((keyDown("UP_ARROW"))&&(gameState==="over")){
gameState="start"; 
balloon1.x=49;
balloon1.y=53;
balloon1.velocityX=-5;
balloon2.x=111;
balloon2.y=53;
balloon2.velocityX=-5;
balloon3.x=171;
balloon3.y=53;
balloon3.velocityX=-5;
balloon4.x=231;
balloon4.y=53;
balloon4.velocityX=-5;
balloon5.x=301;
balloon5.y=53;
balloon5.velocityX=-5;
balloon6.x=371;
balloon6.y=53;
balloon6.velocityX=-5;
lifeline=3;
gameState="start";
}
if(gameState==="over"){
  fill("pink");
  text("Press Up arrow to restart",93,228);
}
}
function hit(){
  arrow.velocityX=0;
  arrow.velocityY=-5;
  }