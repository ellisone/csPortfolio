# csPortfolio

* WebPage[here](https://ellisone.github.io/testPage/dogPage/index.html)
* Lightning[here](https://ellisone.github.io/lightning2/index.html)
* Lighting JS()
* Dice[here](https://ellisone.github.io/dice3/)
* Chemotaxis[here](https://ellisone.github.io/chemotaxis4/)

```Java
class Minion   
 { 
   float x;
   float y;
   float size;
   float c;
   float xAttraction;
   float yAttraction;
   float speed;
   Minion(float a, float b, float si, float xA, float yA, float s){
     x=a;
     y=b;
     size=si;
     xAttraction=xA;
     yAttraction=yA;
     speed=s;
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
   void SetSpeed(float s){
     speed=s;
   }
   
   void move(){
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
     ellipse(x,y,size,size);
   }
 }    
```
