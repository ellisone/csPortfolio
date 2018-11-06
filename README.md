# csPortfolio

* WebPage[here](https://ellisone.github.io/testPage/dogPage/index.html)
* Lightning[here](https://ellisone.github.io/lightning2/index.html)
* Lighting JS()
* Dice[here](https://ellisone.github.io/dice3/)
* Chemotaxis[here](https://ellisone.github.io/chemotaxis4/)
* Starfield[here](https://ellisone.github.io/starfield5/)

```Java
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
```
