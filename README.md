# csPortfolio
* WebPage[here](https://ellisone.github.io/testPage/dogPage/index.html)
* Lightning[here](https://ellisone.github.io/lightning2/index.html)
* Dice[here](https://ellisone.github.io/dice3/)
* Chemotaxis[here](https://ellisone.github.io/chemotaxis4/)
* Starfield[here](https://ellisone.github.io/starfield5/)
```Java
1. I had a lot of fun developing these projects and I feel like I did pretty well on them. Although, my webpage isn't quite the way I wanted it and I'm not doing the best with HTML.
2. Two sources of pride would be my Starfield and chemotaxis projects.

3.
a. I absolutely love my starfield and I am very happy with how it turned out even though I don't understand how some parts of it work. I mostly just put code down and saw what it did, then added more from there. My OddballParticle class was the most fun and experimental as I played along with the code.

class OddballParticle implements Particle{
  double x,y,XAttraction,YAttraction,speed,xSpeed,ySpeed;
  int XorY;
  Boolean V2;
  OddballParticle(double s, boolean v2){
    V2=v2;
    XorY=(int)(Math.random()*4);
    if(XorY==0){
      y=0;
      x=Math.random()*width;
    }
    if(XorY==1){
      y=height;
      x=Math.random()*width;
    }
    if(XorY==2){
      y=Math.random()*height;
      x=width;
    }
    if(XorY==3){
      y=Math.random()*height;
      x=0;
    }
    XAttraction=width/2;
    YAttraction=height/2;
    speed=s;
    xSpeed=(Math.abs(XAttraction-x)/(Math.abs(XAttraction-x)+(Math.abs(YAttraction-y)))*speed);
    ySpeed=(Math.abs(YAttraction-y)/(Math.abs(XAttraction-x)+(Math.abs(YAttraction-y)))*speed);
    if(V2==true){
      if(x>(width/2)){
        xSpeed*=-1;
      }
      if(y>(height/2)){
        ySpeed*=-1;
      }
    }
    
  }
 
  double getX(){
    return x;
  }
  double getY(){
    return y;
  }
 
  public void move(){
     x+=xSpeed;
     y+=ySpeed;
     if(x<0||y<0||x>width||y>height){
       xSpeed*=-1;
       ySpeed*=-1;
     }
   }
  public void show(){
    ellipse((float)x,(float)y,10,10);
  }
 
}
b. I also really like how chemotaxis turned out, it ended up working exactly as I pictured it when I first came up with the idea of what I wanted to do with it. I had a lot of problems getting the mother and minnions to follow the mouse and I had to do a lot of problem solving to figure out how to make them go strait, but after a lot of troubleshooting I managed to fix all of the bugs. I learned a lot about how to get things to follow certain points on the screen.
class Mother{
   Minion[] minions=new Minion[10];
   float x;
   float y;
   float c;
   float xAttraction;
   float yAttraction;
   float speed;
   double distance;
   boolean gameOver=false;
   int timer=0;
   Mother(){
     x=(float)(Math.random()*950);
     y=(float)(Math.random()*950);
     xAttraction=mouseX;
     yAttraction=mouseY;
     for(int i=0; i<minions.length; i++){
       minions[i]=new Minion(x,y, 10, ((float)mouseX), ((float)mouseY), (float)((Math.random()*10)+10));
     }
   }
  
   float GetX(){
     return x;
   }
   float GetY(){
     return y;
   }
   void SetxAttraction(float mx){
     xAttraction=mx;
   }
   void SetyAttraction(float my){
     yAttraction=my;
   }
   void reset(){
     x=(float)(Math.random()*950);
     y=(float)(Math.random()*950);
     timer=0;
     for(int i=0; i<minions.length; i++){
       minions[i].minionReset(x,y);
     }
   }
  
   void move(){
     speed=((float)((Math.random()*3)+1));
     float xSpeed;
     float ySpeed;
     
     xSpeed=(Math.abs(xAttraction-x)/(Math.abs(xAttraction-x)+(Math.abs(yAttraction-y)))*speed);
     ySpeed=(Math.abs(yAttraction-y)/(Math.abs(xAttraction-x)+(Math.abs(yAttraction-y)))*speed);
     
     if(ySpeed>0){
       if(xAttraction>x){
         x+=xSpeed;
       }if(xAttraction<x){
         x-=xSpeed;
       }
       if(yAttraction>y){
         y+=ySpeed;
       }if(yAttraction<y){
         y-=ySpeed;
       }
     }
   }
  
   void show(){
     if(timer<3500){
       timer++;
       distance=((double)(timer/10))+50;
     }
     for(int i=0; i<minions.length; i++){
       fill(255);
       
       if(Math.abs(x-mouseX)<distance&&Math.abs(y-mouseY)<distance){
         minions[i].SetxAttraction(mouseX);
         minions[i].SetyAttraction(mouseY);
       }else{
         minions[i].SetxAttraction(x);
         minions[i].SetyAttraction(y);
       }
       minions[i].SetSpeed((float)((Math.random()*10)+10));
       minions[i].move();
       minions[i].show();
     }
     fill(255,0,0);
     ellipse(x,y,30,30);
     
     for(int i=0; i<minions.length; i++){
       if(minions[i].GetX()+10>mouseX&&minions[i].GetX()-10<mouseX&&minions[i].GetY()+10>mouseY&&minions[i].GetY()-10<mouseY){
         gameOver=true;
       }
     }
   }
   void setGameOver(boolean GO){
     gameOver=GO;
   }
   boolean checkGameOver(){
     return gameOver;
   }
 }    
4. The most significant hurdle the I had to get over this tri would be getting my chemotaxis to work correctly. I kept trying out different strategies to get my code to work, but kept running into a wall. Eventually I figured out why I was having so many problems and everything started to work the way I was painstakingly trying to get it to from the very beginning.
```
