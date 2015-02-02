# Processing-JS-intro

Ojo o1, o2, o3, o4, o5;
OjoV ov1, ov2, ov3, ov4, ov5;

PImage OvejaNegra;
PImage OvejaBlanca;
String s = "Presiona las teclas 'B' o 'N' para empezar";

void setup() 

{

  size(800, 600);

  smooth();

  noStroke();

  o1 = new Ojo( 700, 36, 120);

  o2 = new Ojo( 544, 385, 100);  

  o3 = new Ojo( 90, 200, 120);

  o4 = new Ojo(150, 440, 80); 

  o5 = new Ojo(375, 120, 140);

  ov1 = new OjoV( 700, 36, 120);

  ov2 = new OjoV( 544, 385, 100);  

  ov3 = new OjoV( 90, 200, 120);

  ov4 = new OjoV(150, 440, 80); 

  ov5 = new OjoV(375, 120, 140);

  OvejaNegra = loadImage("ON.png");
  OvejaBlanca = loadImage("OB.png");
}


void draw() 

{

  background(102);

  fill(50);
  text(s, 10, 550, 600, 80);

  if (key =='n') {
    image(OvejaNegra, mouseX, mouseY);
    image(OvejaBlanca, 0, 0);

    o1.update(mouseX, mouseY);

    o2.update(mouseX, mouseY);

    o3.update(mouseX, mouseY);

    o4.update(mouseX, mouseY);

    o5.update(mouseX, mouseY);

    o1.display();

    o2.display();

    o3.display();

    o4.display();

    o5.display();
  } else if (key =='b') {
    image(OvejaBlanca, mouseX, mouseY);
    image(OvejaNegra, 0, 0);

    ov1.update(mouseX, mouseY);

    ov2.update(mouseX, mouseY);

    ov3.update(mouseX, mouseY);

    ov4.update(mouseX, mouseY);

    ov5.update(mouseX, mouseY);

    ov1.display();

    ov2.display();

    ov3.display();

    ov4.display();

    ov5.display();
  }
}


class Ojo 

{

  int ox, oy;

  int tamanio;

  float angulo = 0.0;



  Ojo(int x, int y, int s) {

    ox = x;

    oy = y;

    tamanio = s;
  }



  void update(int mx, int my) {

    angulo = atan2(my-oy, mx-ox);
  }



  void display() {

    pushMatrix();

    translate(ox, oy);

    fill(255);

    ellipse(0, 0, tamanio, tamanio);

    rotate(angulo);

    fill(153);

    ellipse(tamanio/4, 0, tamanio/2, tamanio/2);

    popMatrix();
  }
}

class OjoV

{

  int ovx, ovy;

  int tamaniov;

  float angulov = 0.0;



  OjoV(int xv, int yv, int sv) {

    ovx = xv;

    ovy = yv;

    tamaniov = sv;
  }



  void update(int vmx, int vmy) {

    angulov = atan2(ovy-vmy, ovx-vmx);
  }



  void display() {

   pushMatrix();

    translate(ovx, ovy);

    fill(255);

    ellipse(0, 0, tamaniov, tamaniov);

    rotate(angulov);

    fill(153);

    ellipse(tamaniov/4, 0, tamaniov/2, tamaniov/2);

   popMatrix();
  }
}
