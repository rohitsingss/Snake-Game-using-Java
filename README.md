# Snake-Game-using-Java

void setup() // for defining initial properties
{ size(300,300); background(0);
}
How can we create our Snake
ArrayList<Integer> x_pos = new ArrayList<Integer>(); ArrayList<Integer> y_pos = new ArrayList<Integer>(); int height=24,width=24; // window int block = 15; void setup(){
x_pos.add(4); // initial position y_pos.add(15);
} 
void draw(){
fill(255); for(int i=0;i<x_pos.size();i++) rect(x_pos.get(i)*block, y_pos.get(i)*block , block,block);
}
How can we move our Snake?
int dir=2; //0-down , 1-up, 2-left, 3-right int []x_dir={0,0,1,-1}; // up down left right int []y_dir={1,-1,0,0}; if(frameCount%8==0){ // only one element is present x_pos.add(0,x_pos.get(0)+x_dir[dir]); y_pos.add(0,y_pos.get(0)+y_dir[dir]); x_pos.remove(x_pos.size()-1); y_pos.remove(y_pos.size()-1);
}
How can we control our Snake?
int dir=2; //0-down , 1-up, 2-right, 3-left
int []x_dir={0,0,1,-1}; // up down left right int []y_dir={1,-1,0,0}; void keyPressed(){ int new_dir = keyCode; if(keyCode==DOWN) new_dir=0; else if(keyCode==UP) new_dir=1; else if(keyCode==LEFT) new_dir=3; else if(keyCode==RIGHT) new_dir=2; else new_dir =-1; if(new_dir!=-1) dir=new_dir; 
}
How does our Snake Eat Food?
1. Creating the Food int f_x_pos=15;
int f_y_pos=15; boolean gamestatus =false; if (!gamestatus)
{ fill(255); rect(f_x_pos*block,f_y_pos*block,block,block);
}
How does our Snake Eat Food 2. Now making our snake eat food and creating random positions for next?
if(x_pos.get(0)==f_x_pos && y_pos.get(0)==f_y_pos){ f_x_pos=(int)random(0,width); f_y_pos=(int)random(0,height);
}
How to display Score Positioning our scoreboard: textAlign(LEFT); //alignment textSize(25); // position fill(255); text("Score:" + x_pos.size(),0,20);
                                           
 How can we increase our Snake’s Speed int speed =10;
Just after our snake eats food:
if(x_pos.size()%2==0 && speed>=2 ) speed=speed-1;
When does our Snake die?
1. When our snake touches the border:
if(x_pos.get(0)<0 || y_pos.get(0)<0 || x_pos.get(0)>wdt|| y_pos.get(0)> hgt)
{
gamestatus=true;
}
1. When our touches itself: for(int i=1;i<x_pos.size();i++)
{ if(x_pos.get(0)==x_pos.get(i) && y_pos.get(0)==y_pos.get(i)) gamestatus=true;
}
Display the score
fill(222, 9, 12);
textAlign(CENTER); textSize(30);
text("Game Over \n Score: " + x_pos.size() + "\n Press Enter", 
500/2,500/2); if(keyCode ==ENTER)
{ x_pos.clear(); y_pos.clear(); x_pos.add(4); y_pos.add(15); dir =2; speed=10; gamestatus = false;
}
This code is written by Rohit Raj(10800117048) CSE Final Year(2017-2021)
