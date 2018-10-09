# csPortfolio

* WebPage[here](https://ellisone.github.io/testPage/dogPage/index.html)
* Lightning[here](https://ellisone.github.io/lightning2/index.html)
* Lighting JS()
* Dice[here](https://ellisone.github.io/dice3/)

```Java
void show()
  {
    noStroke();
    fill(0);
    int CD=(int)((Math.random()*3)+1);
    if(CD==1){
      fill(255,0,0);
    }else if(CD==2){
      fill(0,255,0);
    }else{
      fill(0,0,255);
    }
    rect(x,y,50,50,7);
    roll();
    if(CD==1){
      fill(0,255,0);
    }else if(CD==2){
      fill(0,0,255);
    }else{
      fill(255,0,0);
    }
    if(num==1||num==3||num==5){
      ellipse(x+25,y+25,10,10);
    }
    if(num==2||num==3||num==4||num==5){
      ellipse(x+12,y+12,10,10);
      ellipse(x+38,y+38,10,10);
    }
    if(num==4||num==5){
      ellipse(x+12,y+38,10,10);
      ellipse(x+38,y+12,10,10);
    }
    if(num==6){
      ellipse(x+15,y+10,10,10);
      ellipse(x+15,y+25,10,10);
      ellipse(x+15,y+40,10,10);
      ellipse(x+35,y+10,10,10);
      ellipse(x+35,y+25,10,10);
      ellipse(x+35,y+40,10,10);
    }
  }
    

```
