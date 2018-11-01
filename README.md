# csPortfolio

* WebPage[here](https://ellisone.github.io/testPage/dogPage/index.html)
* Lightning[here](https://ellisone.github.io/lightning2/index.html)
* Lighting JS()
* Dice[here](https://ellisone.github.io/dice3/)
* Chemotaxis[here](https://ellisone.github.io/chemotaxis4/)
* Starfield[here](https://ellisone.github.io/starfield5/)

```Java
int R1=255,G1=0,B1=0,R2=0,G2=255,B2=0,R3=0,G3=0,B3=255;
boolean ReverseOddball1;
Particle[] Particles=new Particle[3168];
ColorChange RGB1=new ColorChange(R1,G1,B1);
ColorChange RGB2=new ColorChange(R2,G2,B2);
ColorChange RGB3=new ColorChange(R3,G3,B3);
void setup(){
  size(900,900);
  //fullScreen();
  for(int i=0; i<10; i++){
    Particles[i]=new NormalParticle(10,.2,i*((Math.PI*2)/10));
  }
  for(int i=10; i<60; i++){
    Particles[i]=new NormalParticle(10,.1,i*((Math.PI*2)/50));
  }
  for(int i=60; i<160; i++){
    Particles[i]=new NormalParticle(5,-.02,i*((Math.PI*2)/100));
  }
  for(int i=160; i<3160; i++){
    Particles[i]=new OddballParticle(6);
  }
  for(int i=3160; i<3168; i++){
    Particles[i]=new JumboParticle(6,i);
  }
}

void draw(){
  RGB1.setR(R1);
  RGB1.setG(G1);
  RGB1.setB(B1);
  RGB1.ChangeColor();
  R1=RGB1.getR();
  G1=RGB1.getG();
  B1=RGB1.getB();
  
  RGB2.setR(R2);
  RGB2.setG(G2);
  RGB2.setB(B2);
  RGB2.ChangeColor();
  R2=RGB2.getR();
  G2=RGB2.getG();
  B2=RGB2.getB();
  
  RGB3.setR(R3);
  RGB3.setG(G3);
  RGB3.setB(B3);
  RGB3.ChangeColor();
  R3=RGB3.getR();
  G3=RGB3.getG();
  B3=RGB3.getB();
  
  
  fill(0,0,0,5);
  rect(0,0,width,height);
  noStroke();
  for(int i=0; i<Particles.length; i++){
    if(i<160){
      fill(R1,G1,B1);
    }if(i>=160&&i<3160){
      fill(R2,G2,B2,15);
    }if(i>=3160&&i<3168){
      fill(R3,G3,B3,35);
    }
    Particles[i].move();
    Particles[i].show();
  }
}


class ColorChange{
  int R,G,B;
  ColorChange(int r,int g,int b){
    R=r;
    G=g;
    B=b;
  }
  
  void ChangeColor(){
    if(R==255&&G<255&&B==0){
      G++;
    }
    if(R>0&&G==255&&B==0){
      R--;
    }
    if(R==0&&G==255&&B<255){
      B++;
    }
    if(R==0&&G>0&&B==255){
      G--;
    }
    if(R<255&&G==0&&B==255){
      R++;
    }
    if(R==255&&G==0&&B>0){
      B--;
    }
  }
  
  int getR(){
    return R;
  }
  
  int getG(){
    return G;
  }
  
  int getB(){
    return B;
  }
  
  void setR(int r){
    R=r;
  }
  
  void setG(int g){
    G=g;
  }
  
  void setB(int b){
    B=b;
  }
}


class JumboParticle extends OddballParticle{
  int side;
  JumboParticle(double s,int si){
    super(s);
    side=si%4;
    x=0;
    y=0;
    if(side==0){
      y=25;
      x=Math.random()*width-25;
    }
    if(side==1){
      y=height-25;
      x=Math.random()*width-25;
    }
    if(side==2){
      y=Math.random()*height-25;
      x=width-25;
    }
    if(side==3){
      y=Math.random()*height-25;
      x=25;
    }
  }
  void move(){
     x+=xSpeed;
     y+=ySpeed;
     if(x<15||x>width-15){
       xSpeed*=-1;
     }
     if(y<15||y>height-15){
       ySpeed*=-1;
     }
  }
  
  void show(){
    ellipse((float)x,(float)y,30,30);
  }
  
}


class NormalParticle implements Particle{
  double x,y,speed,angle,angleChange;
  NormalParticle(double s, double ac, double a){
    x=width/2;
    y=height/2;
    speed=s;
    angleChange=ac;
    angle=a;
  }
  public void move(){
    x+=Math.cos(angle)*speed;
    y+=Math.sin(angle)*speed;
    angle+=angleChange;
  }
  public void show(){
    ellipse((float)x,(float)y,10,10);
  }
}


class OddballParticle implements Particle{
  double x,y,XAttraction,YAttraction,speed,xSpeed,ySpeed;
  int XorY;
  boolean Reverse;
  OddballParticle(double s){
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
    if(x>(width/2)){
      xSpeed*=-1;
    }
    if(y>(height/2)){
      ySpeed*=-1;
    }
  }
  
  double getX(){
    return x;
  }
  double getY(){
    return y;
  }
  
  void Reverse(){
    xSpeed*=-1;
    ySpeed*=-1;
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


interface Particle{
  public void show();
  public void move();
}
```
