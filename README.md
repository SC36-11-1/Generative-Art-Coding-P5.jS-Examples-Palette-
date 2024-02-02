# P5.JS-Samples
Generative Art Coding Pallet Examples🎨✨

# [P5.jS Examples](https://p5js.org/examples/) Pallet 👨🏿‍🎨🎨✨

## Examples
## Structure

### Functions

<img width="706" alt="Screen Shot 2023-08-18 at 7 43 47 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/fac4d732-2151-4d9e-bdb3-3b329b8de769">

*The drawTarget() function makes it easy to draw many distinct *targets. Each call to drawTarget() specifies the position, size, and number of *rings for each target.*

    function setup() {
     createCanvas(720, 400);
     background(51);
     noStroke();
     noLoop();
    }

    function draw() {
     drawTarget(width * 0.25, height * 0.4, 200, 4);
     drawTarget(width * 0.5, height * 0.5, 300, 10);
     drawTarget(width * 0.75, height * 0.3, 120, 6);
    }

    function drawTarget(xloc, yloc, size, num) {
     const grayvalues = 255 / num;
     const steps = size / num;
    for (let i = 0; i < num; i++) {
     fill(i * grayvalues);
     ellipse(xloc, yloc, size - i * steps, size - i * steps);
     }
    }


### CreateGraphics

<img width="699" alt="Screen Shot 2023-08-18 at 7 49 57 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/51b779d1-f974-4738-a532-46f6e37384b7">

**Creates and returns a new p5.Renderer object. Use this class if you need to draw into an off-screen graphics buffer. The two parameters define the width and height in pixels.
**

      let pg;
        function setup() {
        createCanvas(710, 400);
      pg = createGraphics(400, 250);
    }

    function draw() {
      fill(0, 12);
      rect(0, 0, width, height);
      fill(255);
      noStroke();
      ellipse(mouseX, mouseY, 60, 60);

      pg.background(51);
      pg.noFill();
      pg.stroke(255);
      pg.ellipse(mouseX - 150, mouseY - 75, 60, 60);

      //Draw the offscreen buffer to the screen with image()
      image(pg, 150, 75);
    }


### Recurrsion

<img width="703" alt="Screen Shot 2023-08-18 at 8 03 01 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/54867d97-3c7f-4d56-aa23-9913d7143ce8">

**A demonstration of recursion, which means functions call themselves. A recursive function must have a terminating condition, without which it will go into an infinite loop. Notice how the drawCircle() function calls itself at the end of its block. It continues to do this until the variable "level" is equal to 1.
**

    function setup() {
      createCanvas(720, 560);
      noStroke();
      noLoop();
    }

    function draw() {
        drawCircle(width / 2, 280, 6);
    }

    function drawCircle(x, radius, level) {
 
// 'level' is the variable that terminates the recursion once it reaches 
// a certain value (here, 1). If a terminating condition is not 
// specified, a recursive function keeps calling itself again and again
// until it runs out of stack space - not a favourable outcome! 
  
      const tt = (126 * level) / 4.0;
      fill(tt);
      ellipse(x, height / 2, radius * 2, radius * 2);
      if (level > 1) {  

 // 'level' decreases by 1 at every step and thus makes the terminating condition
 // attainable
  
    level = level - 1;  
    drawCircle(x - radius / 2, radius / 2, level);
    drawCircle(x + radius / 2, radius / 2, level);
      }
    }


## Form
### Shape Primitives

<img width="639" alt="Screen Shot 2023-08-18 at 8 46 47 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/b6e9b668-533d-43eb-b031-2222f2128cb0">

**The basic shape primitive functions are triangle(), rect(), quad(), ellipse(), and arc(). Squares are made with rect() and circles are made with ellipse(). Each of these functions requires a number of parameters to determine the shape's position and size.
**

    function setup() {
 
// Sets the screen to be 720 pixels wide and 400 pixels high
 
      createCanvas(720, 400);
      background(0);
      noStroke();

      fill(204);
      triangle(18, 18, 18, 360, 81, 360);

      fill(102);
      rect(81, 81, 63, 63);

      fill(204);
      quad(189, 18, 216, 18, 216, 360, 144, 360);

      fill(255);
      ellipse(252, 144, 72, 72);

      fill(204);
      triangle(288, 18, 351, 360, 288, 360);

      fill(255);
      arc(479, 300, 280, 280, PI, TWO_PI);
    }


### Regular Polygon

<img width="711" alt="Screen Shot 2023-08-18 at 9 34 57 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/1ed223df-8e54-4f39-87b3-cabd6ebefd34">

**What is your favorite? Pentagon? Hexagon? Heptagon? No? What about the icosagon? The polygon() function created for this example is capable of drawing any regular polygon. Try placing different numbers into the polygon() function calls within draw() to explore.
**

    function setup() {
     createCanvas(720, 400);
    }

    function draw() {
     background(102);

    push();
    translate(width * 0.2, height * 0.5);
    rotate(frameCount / 200.0);
    polygon(0, 0, 82, 3);
    pop();

    push();
    translate(width * 0.5, height * 0.5);
    rotate(frameCount / 50.0);
    polygon(0, 0, 80, 20);
    pop();

    push();
    translate(width * 0.8, height * 0.5);
    rotate(frameCount / -100.0);
    polygon(0, 0, 70, 7);
    pop();
    }

    function polygon(x, y, radius, npoints) {
     let angle = TWO_PI / npoints;
    beginShape();
    for (let a = 0; a < TWO_PI; a += angle) {
     let sx = x + cos(a) * radius;
     let sy = y + sin(a) * radius;
    vertex(sx, sy);
     }
    endShape(CLOSE);
    }


### Star
<img width="712" alt="Screen Shot 2023-08-18 at 10 12 16 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/0862619a-71cc-4fed-951e-ef8d680710c6">

**The star() function created for this example is capable of drawing a wide range of different forms. Try placing different numbers into the star() function calls within draw() to explore.
**

     function setup() {
      createCanvas(720, 400);
    }

     function draw() {
      background(102);

      push();
      translate(width * 0.2, height * 0.5);
      rotate(frameCount / 200.0);
      star(0, 0, 5, 70, 3);
      pop();

      push();
      translate(width * 0.5, height * 0.5);
      rotate(frameCount / 50.0);
      star(0, 0, 80, 100, 40);
      pop();

      push();
      translate(width * 0.8, height * 0.5);
      rotate(frameCount / -100.0);
      star(0, 0, 30, 70, 5);
      pop();
    }

    function star(x, y, radius1, radius2, npoints) {
      let angle = TWO_PI / npoints;
      let halfAngle = angle / 2.0;
      beginShape();
      for (let a = 0; a < TWO_PI; a += angle) {
        let sx = x + cos(a) * radius2;
        let sy = y + sin(a) * radius2;
        vertex(sx, sy);
        sx = x + cos(a + halfAngle) * radius1;
        sy = y + sin(a + halfAngle) * radius1;
        vertex(sx, sy);
      }
      endShape(CLOSE);
    }

### Bezier

<img width="711" alt="Screen Shot 2023-08-18 at 10 50 56 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/c7448548-f581-416b-bfe7-8b170866a8d7">

**The first two parameters for the bezier() function specify the first point in the curve and the last two parameters specify the last point. The middle parameters set the control points that define the shape of the curve.
**

    function setup() {
      createCanvas(720, 400);
      stroke(255);
      noFill();
    }

    function draw() {
      background(0);
      for (let i = 0; i < 200; i += 20) {
        bezier(
          mouseX - i / 2.0,
          40 + i,
          410,
          20,
          440,
          300,
          240 - i / 16.0,
          300 + i / 8.0
        );
      }
    }

### 3D Primitives

<img width="702" alt="Screen Shot 2023-08-18 at 10 56 19 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/6f21e6dc-b94e-4815-9922-a3840018f2a4">

**Placing mathematically 3D objects in synthetic space. The box() and sphere() functions take at least one parameter to specify their size. These shapes are positioned using the translate() function.
**

    function setup() {
      createCanvas(710, 400, WEBGL);
    }

    function draw() {
      background(100);

      noStroke();
      fill(50);
      push();
      translate(-275, 175);
      rotateY(1.25);
      rotateX(-0.9);
      box(100);
      pop();

      noFill();
      stroke(255);
      push();
      translate(500, height * 0.35, -200);
      sphere(300);
      pop();
    }

### Trig Wheels and Pie Chart   

<img width="312" alt="Screen Shot 2023-08-18 at 10 59 53 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/7c1ad24f-adf3-48ce-a2d2-81c4d9feb8db">

**contributed by Prof WM Harris, How to create a trig color wheel and a visualization of a population age data as a pie chart.
Functions are created for the canvas setup, trig color wheel, drawslice, and pie chart. The size of the slices are determined as well as their color range. The pie chart is separated by definitive color per value whereas the trig color wheel has a fixed slice amount with a range color fill.
**

    function setup() {
      createCanvas(400, 400);
      colorMode(HSB);
      angleMode(DEGREES);

  //vars for color wheel center point

      let x = width / 2;
      let y = height / 2 + 100;
      colorWheel(x, y, 100); //slide 11

      noStroke();
      pieChartPop(200, 100); //slide 12
    }

//**** slide 12 pie chart trig demo 

    function pieChartPop(x, y) {
      let [total, child, young, adult, senior, elder] = [577, 103, 69,
    122, 170, 113
      ];
      let startValue = 0;
      let range = 0;
  //child slice
  
      range = child / total;
      drawSlice("blue", x, y, 200, startValue, startValue + range);
      startValue += range;
  //young slice
 
      range = young / total;
      drawSlice("orange", x, y, 200, startValue, startValue + range);
      startValue += range;
  //adult slice
 
      range = adult / total;
      drawSlice("green", x, y, 200, startValue, startValue + range);
      startValue += range;
  //senior slice

      range = senior / total;
      drawSlice("tan", x, y, 200, startValue, startValue + range);
      startValue += range;
  //elder slice
  
      range = elder / total;
      drawSlice("pink", x, y, 200, startValue, startValue + range);
      startValue += range;
        }
    /**
     * drawSlice - draw colored arc based on angle percentages. slide 13
     * Adjust angles so that 0% starts at top (actually -90).
     * @param {color} fColor - fill color
     * @param {number} x - center x
     * @param {number} y - center y
     * @param {number} d - diameter
     * @param {float} percent1 - starting percentage
     * @param {float} percent2 - ending percentage
     */
       function drawSlice(fColor, x, y, d, percent1, percent2) {
           fill(fColor);
           arc(x, y, d, d, -90 + percent1 * 360, -90 + percent2 * 360);
          }
//**** slide 11 trig demo 
    
    function colorWheel(x, y, rad) {
      strokeWeight(10);
      strokeCap(SQUARE);
//Iterate 360 degrees of lines, +10deg per turn

      for (let a = 0; a < 360; a += 10) {
        stroke(a, 150, 200); //hue based on a
//radius is 100, angle is a degrees

    line(x, y, x + rad * cos(a),
      y + rad * sin(a));
      }
    }

## DATA
### Variables

<img width="713" alt="Screen Shot 2023-08-21 at 8 00 37 AM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/2d442c12-51be-456b-b6c1-52972d3bf115">

**Variables are used for storing values. In this example, change the values of variables to affect the composition.**

    function setup() {
      createCanvas(720, 400);
      background(0);
      stroke(153);
      strokeWeight(4);
      strokeCap(SQUARE);

      let a = 50;
      let b = 120;
      let c = 180;

      line(a, b, a + c, b);
      line(a, b + 10, a + c, b + 10);
      line(a, b + 20, a + c, b + 20);
      line(a, b + 30, a + c, b + 30);

      a = a + c;
      b = height - b;

      line(a, b, a + c, b);
      line(a, b + 10, a + c, b + 10);
      line(a, b + 20, a + c, b + 20);
      line(a, b + 30, a + c, b + 30);

      a = a + c;
      b = height - b;

      line(a, b, a + c, b);
      line(a, b + 10, a + c, b + 10);
      line(a, b + 20, a + c, b + 20);
      line(a, b + 30, a + c, b + 30);
    }

### True and False

<img width="716" alt="Screen Shot 2023-08-21 at 8 04 33 AM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/e48ff12a-65c8-44ce-9a2d-1d3971045f97">

**A Boolean variable has only two possible values: true or false. It is common to use Booleans with control statements to determine the flow of a program. In this example, when the boolean value "b" is true, vertical lines are drawn and when the boolean value "b" is false, horizontal lines are drawn.
**

    function setup() {
      createCanvas(720, 400);
      background(0);
      stroke(255);

      let b = false;
      let d = 20;
      let middle = width / 2;

      for (let i = d; i <= width; i += d) {
        b = i < middle;

        if (b === true) {
// Vertical line

          line(i, d, i, height - d);
        }

        if (b === false) {
 // Horizontal line

          line(middle, i - middle + d, width - d, i - middle + d);
        }
      }
    }

### Variable Scope

<img width="712" alt="Screen Shot 2023-08-21 at 8 10 23 AM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/846e6c16-951f-450f-9576-fe3d39d11513">

**Variables have a global or function "scope". For example, variables declared within either the setup() or draw() functions may be only used in these functions. Global variables, variables declared outside of setup() and draw(), may be used anywhere within the program. If a function variable is declared with the same name as a global variable, the program will use the function variable to make its calculations within the current scope.
**

    let a = 80; // Create a global variable "a"

    function setup() {
      createCanvas(720, 400);
      background(0);
      stroke(255);
      noLoop();
    }

    function draw() {
  // Draw a line using the global variable "a"
     
      line(a, 0, a, height);

  // Use a local variable a in for loop
      
      for (let a = 120; a < 200; a += 3) {
        line(a, 0, a, height);
      }

  // Make a call to the custom function drawAnotherLine()
     
      drawAnotherLine();

  // Make a call to the custom function drawYetAnotherLine()
      
      drawYetAnotherLine();
    }

    function drawAnotherLine() {
  // Create a new variable "a" local to this function

      let a = 320;
  // Draw a line using the local variable "a"

      line(a, 0, a, height);
    }

    function drawYetAnotherLine() {
  // Because no new local variable "a" is set,
  // this line draws using the original global
  // variable "a" which is set to the value 20.
    
      line(a + 3, 0, a + 3, height);
    }

### Numbers

**Numbers can be written with or without decimals. An integer (more commonly called an int) is a number without a decimal point. A float is a floating-point number, which means it is a number that has a decimal place.
**

    let a = 0; // Create a global variable "a" of type Number
    let b = 0; // Create a global variable "b" of type Number

    function setup() {
      createCanvas(720, 400);
      stroke(255);
    }

    function draw() {
      background(0);

      a = a + 1; // Increment a with an integer
      b = b + 0.2; //Increment b with a float
      line(a, 0, a, height / 2);
      line(b, height / 2, b, height);

      if (a > width) {
    a = 0;
      }
      if (b > width) {
    b = 0;
      }
    }

## Arrays
### Arrays

<img width="726" alt="Screen Shot 2023-08-21 at 8 38 25 AM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/ebc7c69b-df62-4afd-9140-5dafcfac58fc">

**An array is a list of data. Each piece of data in an array is identified by an index number representing its position in the array. Arrays are zero based, which means that the first element in the array is [0], the second element is [1], and so on. In this example, an array named "coswave" is created and filled with the cosine values. This data is displayed three separate ways on the screen.
**

    let coswave = [];

    function setup() {
      createCanvas(720, 360);
      for (let i = 0; i < width; i++) {
        let amount = map(i, 0, width, 0, PI);
        coswave[i] = abs(cos(amount));
      }
      background(255);
      noLoop();
    }

    function draw() {
      let y1 = 0;
      let y2 = height / 3;
      for (let i = 0; i < width; i += 3) {
        stroke(coswave[i] * 255);
        line(i, y1, i, y2);
      }

      y1 = y2;
      y2 = y1 + y1;
      for (let i = 0; i < width; i += 3) {
        stroke((coswave[i] * 255) / 4);
        line(i, y1, i, y2);
      }

      y1 = y2;
      y2 = height;
      for (let i = 0; i < width; i += 3) {
        stroke(255 - coswave[i] * 255);
        line(i, y1, i, y2);
      }
    }

### Array 2D

<img width="715" alt="Screen Shot 2023-08-21 at 2 10 18 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/0df9bf53-07ff-4096-8950-c624a2a28b70">

**Demonstrates the syntax for creating a two-dimensional (2D) array. Values in a 2D array are accessed through two index values. 2D arrays are useful for storing images. In this example, each dot is colored in relation to its distance from the center of the image.
**

    let distances = [];
    let maxDistance;
    let spacer;

    function setup() {
      createCanvas(720, 360);
      maxDistance = dist(width / 2, height / 2, width, height);
      for (let x = 0; x < width; x++) {
        distances[x] = []; // create nested array
        for (let y = 0; y < height; y++) {
          let distance = dist(width / 2, height / 2, x, y);
          distances[x][y] = (distance / maxDistance) * 255;
        }
      }
      spacer = 10;
      noLoop(); // Run once and stop
    }

    function draw() {
      background(0);
  // This embedded loop skips over values in the arrays based on
  // the spacer variable, so there are more values in the array
  // than are drawn here. Change the value of the spacer variable
  // to change the density of the points

      for (let x = 0; x < width; x += spacer) {
        for (let y = 0; y < height; y += spacer) {
          stroke(distances[x][y]);
          point(x + spacer / 2, y + spacer / 2);
        }
      }
    }

### Array Objects

<img width="714" alt="Screen Shot 2023-08-21 at 2 15 24 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/7a54fe6e-746e-4a7e-b5af-b501987bf918">

**Demonstrates the syntax for creating an array of custom objects.
**

    class Module {
      constructor(xOff, yOff, x, y, speed, unit) {
        this.xOff = xOff;
        this.yOff = yOff;
        this.x = x;
        this.y = y;
        this.speed = speed;
        this.unit = unit;
        this.xDir = 1;
        this.yDir = 1;
      }

  // Custom method for updating the variables

      update() {
        this.x = this.x + this.speed * this.xDir;
        if (this.x >= this.unit || this.x <= 0) {
          this.xDir *= -1;
          this.x = this.x + 1 * this.xDir;
          this.y = this.y + 1 * this.yDir;
        }
        if (this.y >= this.unit || this.y <= 0) {
          this.yDir *= -1;
          this.y = this.y + 1 * this.yDir;
        }
      }

  // Custom method for drawing the object

      draw() {
        fill(255);
        ellipse(this.xOff + this.x, this.yOff + this.y, 6, 6);
      }
    }

    let unit = 40;
    let count;
    let mods = [];

    function setup() {
      createCanvas(720, 360);
      noStroke();
      let wideCount = width / unit;
      let highCount = height / unit;
      count = wideCount * highCount;

      let index = 0;
      for (let y = 0; y < highCount; y++) {
        for (let x = 0; x < wideCount; x++) {
          mods[index++] = new Module(
            x * unit,
            y * unit,
            unit / 2,
            unit / 2,
            random(0.05, 0.8),
            unit
          );
        }
      }
    }

    function draw() {
      background(0);
      for (let i = 0; i < count; i++) {
        mods[i].update();
        mods[i].draw();
      }
    }

## Control

### Iteration

<img width="713" alt="Screen Shot 2023-08-21 at 3 43 20 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/a4dd90fc-8ea3-4a88-b57a-7f3584a32719">

**Iteration with a "for" structure to construct repetitive forms.
**

    let y;
    let num = 14;

    function setup() {
      createCanvas(720, 360);
      background(102);
      noStroke();
  // Draw white bars

      fill(255);
      y = 60;
      for (let i = 0; i < num / 3; i++) {
        rect(50, y, 475, 10);
        y += 20;
      }
  // Gray bars

      fill(51);
      y = 40;
      for (let i = 0; i < num; i++) {
        rect(405, y, 30, 10);
        y += 20;
      }
      y = 50;
      for (let i = 0; i < num; i++) {
        rect(425, y, 30, 10);
        y += 20;
      }
  // Thin lines

      y = 45;
      fill(0);
      for (let i = 0; i < num - 1; i++) {
        rect(120, y, 40, 1);
        y += 20;
      }
    }

### Embedded Iteration

<img width="712" alt="Screen Shot 2023-08-21 at 3 47 49 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/875cd26b-0b1a-498f-b29d-2388917efb9a">

**Embedding "for" structures allows repetition in two dimensions.
**

    function setup() {
      createCanvas(720, 360);
      background(0);
      noStroke();

      let gridSize = 35;

      for (let x = gridSize; x <= width - gridSize; x += gridSize) {
        for (let y = gridSize; y <= height - gridSize; y += gridSize) {
          noStroke();
          fill(255);
          rect(x - 1, y - 1, 3, 3);
          stroke(255, 50);
          line(x, y, width / 2, height / 2);
        }
      }
    }

### Conditionals 1

<img width="711" alt="Screen Shot 2023-08-21 at 3 51 50 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/6c802779-b147-4f34-8bca-bdfb270d0d2e">

**Conditions are like questions. They allow a program to decide to take one action if the answer to a question is true or to do another action if the answer to the question is false. The questions asked within a program are always logical or relational statements. For example, if the variable 'i' is equal to zero then draw a line.
**


    function setup() {
      createCanvas(720, 360);
      background(0);

      for (let i = 10; i < width; i += 10) {  
// If 'i' divides by 20 with no remainder draw the first line
// else draw the second line

        if (i % 20 === 0) {
          stroke(255);
          line(i, 80, i, height / 2);
        } else {
          stroke(153);
          line(i, 20, i, 180);
        }
      }
    }

### Conditionals 2

<img width="712" alt="Screen Shot 2023-08-21 at 3 54 30 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/feff7b0c-d7cc-4219-b016-ffeddd8f1d0c">

**We extend the language of conditionals from the previous example by adding the keyword "else". This allows conditionals to ask two or more sequential questions, each with a different action.
**

    function setup() {
      createCanvas(720, 360);
      background(0);

      for (let i = 2; i < width - 2; i += 4) {  
// If 'i' divides by 20 with no remainder
  
        if (i % 20 === 0) {
          stroke(255);
          line(i, 80, i, height / 2);
  // If 'i' divides by 10 with no remainder
 
        } else if (i % 10 === 0) {
          stroke(153);
          line(i, 20, i, 180);
      // If neither of the above two conditions are met
      // then draw this line
 
        } else {
          stroke(102);
          line(i, height / 2, i, height - 20);
        }
      }
    }

### Logical Operators

<img width="713" alt="Screen Shot 2023-08-21 at 3 58 59 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/b06074a8-be76-4274-bb52-1a474635b733">

**The logical operators for AND (&&) and OR (||) are used to combine simple relational statements into more complex expressions. The NOT (!) operator is used to negate a boolean statement.
**

    let test = false;

    function setup() {
      createCanvas(720, 360);
      background(126);

      for (let i = 5; i <= height; i += 5) {
// Logical AND
 
        stroke(0);
        if (i > 35 && i < 100) {
          line(width / 4, i, width / 2, i);
          test = false;
        }
// Logical OR
  
        stroke(76);
        if (i <= 35 || i >= 100) {
          line(width / 2, i, width, i);
          test = true;
        }
// Testing if a boolean value is "true"
// The expression "if(test)" is equivalent to "if(test == true)"

        if (test) {
          stroke(0);
          point(width / 3, i);
        }
// Testing if a boolean value is "false"
// The expression "if(!test)" is equivalent to "if(test == false)"
   
        if (!test) {
          stroke(255);
          point(width / 4, i);
        }
      }
    }

### Logical Operators 2

<img width="396" alt="Screen Shot 2023-08-21 at 4 12 16 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/77276197-acfa-4ec8-a342-12ef6f80db30">

**contributed by Prof WM Harris, How to create Xboxes with one global variable and create conditions with boolean variables and boolean expressions by utilizing Boolean operators ||, &&, and ! to do boundary checking.
Functions are created for both the canvas set up as well as the creation of the boxes. Background color is dependent on the location of the boxes in the canvas space. When mouse button and key are pressed simultaneously, the “where” text and box color changes to cyan, but if the mouse button is clicked alone then the animation will start. When q or Q are pressed the text “Did you type q or Q?” will change to blue, else it will be purple. If the mouse is placed within the orange box containing the text, “withinRect” then the shape will turn pink.
**

//1 coordinate for everything :)

    let where = 0; //control boxes' positions
    function setup() {
      createCanvas(400, 400);
    }
    function draw() {
  //similar to slide 4 use of OR, ||
  //to set bg color of canvas

      if ((where < 0) || (where > height)) {
        background("beige");
      } else {
        background("chocolate");
      }
  //similar to slide 4 use of AND, &&
  //to set fill color of box & text
  
      if (mouseIsPressed && keyIsPressed) {
        fill("cyan");
      } else {
        fill(255);
      }
  //boxL
 
      rect(where, where, 40);
  //boxR, pad x coordinate for size of box
 
      rect(width - where - 40, where, 40);
 //Move the boxes

      where = where + 1;
  //Show the value of where the boxes are
 
      text("where is " + where, 150, 30);
  //testing not, ! and or, || operators
 
      if (!(key === "q" || key === "Q")) {
        fill("purple");
      } else {
        fill("dodgerBlue");
      }
  //Show the current key value
 
      text("Did you type a q or Q? " + key, 150, 70);
  //*** Boundary checking ***
  //Is the mouse within rect boundary?
  //left, right, top, bottom
 
      let withinRect = (mouseX >= 150) &&
        (mouseX <= 150 + 100) &&
        (mouseY >= 300) &&
        (mouseY <= 300 + 40);
  //fill color based on value of withinRect
    
        if (withinRect) {
        fill("pink");
      } else {
        fill("orange");
      }
  //draw the rect
  
      rect(150, 300, 100, 40);
  //show withinRect value as label on rect
 
      fill(0);
      text("withinRect " + withinRect, 160, 320);
    }
//boxes restart

    function mousePressed() {
  //Reset boxes back up and above the canvas

      where = -50;
    }

### Conditional Shapes

<img width="698" alt="Screen Shot 2023-08-21 at 4 18 27 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/f24bc43a-ccec-44c1-82d6-736d88140b9b">

**contributed by Prof WM Harris, How to draw different shapes mid canvas depending on the mouse position.
Functions are created for the main canvas set up with the markers on the left and right hand sides. One is also created for the location of the mouse regarding the canvas and the markers. If the mouse is within the outer left hand beige rectangle, then the shape of circle is drawn down the center of the canvas. If the mouse is within the outer right hand beige rectangle, then the shape of square is drawn down the center of the canvas.
**

    function setup() {
        createCanvas(400, 400);
        strokeWeight(3);
//center squares to match circles
      
        rectMode(CENTER);
//draw rects to mark far sides
      
        noStroke();
        fill("beige");
        rect(5, height / 2, 10, height);
        rect(width - 5, height / 2, 10, height);
        fill("orange");
        stroke("brown");
      }
      function draw() {
        point(mouseX, mouseY);
  
//if (test) {doThis; }
//test: mouseX on far left of canvas
//doThis: draw a circle at mouseY
   
        if (mouseX < 10) {
          circle(width / 2, mouseY, 20);
        }
//test: mouseX on far right of canvas
//doThis: draw a square at mouseY
    
        if (mouseX > width - 10) {
          square(width / 2, mouseY, 20);
        }
      }

## Image

### Load and Display Image

**To run this example locally, you will need an image file, and a running local server.
**

<img width="715" alt="Screen Shot 2023-08-21 at 4 24 43 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/da7314cb-c48b-49de-a4aa-9f5feea0afa4">

**Images can be loaded and displayed to the screen at their actual size or any other size.
To run this example locally, you will need an image file, and a running local server.**

    let img; // Declare variable 'img'.
    function setup() {
      createCanvas(720, 400);
      img = loadImage('assets/moonwalk.jpg'); // Load the image
    }
    function draw() {
// Displays the image at its actual size at point (0,0)

      image(img, 0, 0);
// Displays the image at point (0, height/2) at half size
  
      image(img, 0, height / 2, img.width / 2, img.height / 2);
    }

### Background Image

**To run this example locally, you will need an image file, and a running local server.
**

<img width="709" alt="Screen Shot 2023-08-21 at 5 42 52 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/ea4c6cfa-df67-4ace-8908-000410adc4b6">

**This example presents the fastest way to load a background image. To load an image as the background, it must be the same width and height as the program.
**

    let bg;
    let y = 0;

    function setup() {
  // The background image must be the same size as the parameters
  // into the createCanvas() method. In this program, the size of
  // the image is 720x400 pixels.

      bg = loadImage('assets/moonwalk.jpg');
      createCanvas(720, 400);
    }

    function draw() {
      background(bg);

      stroke(226, 204, 0);
      line(0, y, width, y);

      y++;
      if (y > height) {
        y = 0;
      }
    }

### Transparency

**To run this example locally, you will need an image file, and a running local server.
**

<img width="717" alt="Screen Shot 2023-08-21 at 5 50 06 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/45c1f875-266e-41e1-8466-f4da717237df">

**
Move the pointer left and right across the image to change its position. This program overlays one image over another by modifying the alpha value of the image with the tint() function.
**

    let img;
    let offset = 0;
    let easing = 0.05;

    function setup() {
      createCanvas(720, 400);
      img = loadImage('assets/moonwalk.jpg'); // Load an image into the program
    }

    function draw() {
      image(img, 0, 0); // Display at full opacity
      let dx = mouseX - img.width / 2 - offset;
      offset += dx * easing;
      tint(255, 127); // Display at half opacity
      image(img, offset, 0);
    }

### Alpha Mask

**To run this example locally, you will need two image files, and a running local server.
**

<img width="718" alt="Screen Shot 2023-08-21 at 5 57 37 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/cabf3348-7932-4aee-90b7-24f58fa3bd04">

**Loads a "mask" for an image to specify the transparency in different parts of the image. The two images are blended together using the mask() method of p5.Image.
**

    let img;
    let imgMask;

    function preload() {
      img = loadImage('assets/moonwalk.jpg');
      imgMask = loadImage('assets/mask.png');
    }

    function setup() {
      createCanvas(720, 400);
      img.mask(imgMask);
      imageMode(CENTER);
    }

    function draw() {
      background(0, 102, 153);
      image(img, width / 2, height / 2);
      image(img, mouseX, mouseY);
    }

### Create Image

<img width="713" alt="Screen Shot 2023-08-21 at 6 02 36 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/1db644ff-e435-4d7f-bc10-ccd88856fd5f">

**The createImage() function provides a fresh buffer of pixels to play with. This example creates an image gradient.
**

    let img; // Declare variable 'img'.

    function setup() {
      createCanvas(720, 400);
      img = createImage(230, 230);
      img.loadPixels();
      for (let x = 0; x < img.width; x++) {
        for (let y = 0; y < img.height; y++) {
          let a = map(y, 0, img.height, 255, 0);
          img.set(x, y, [0, 153, 204, a]);
        }
      }
      img.updatePixels();
    }

    function draw() {
      background(0);
      image(img, 90, 80);
      image(img, mouseX - img.width / 2, mouseY - img.height / 2);
    }

### Pointillism

**To run this example locally, you will need an image file, and a running local server.
**

<img width="723" alt="Screen Shot 2023-08-21 at 6 05 33 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/da16f0fe-8009-4da2-a8b6-cc03092fdb06">

**By Dan Shiffman. Mouse horizontal location controls size of dots. Creates a simple pointillist effect using ellipses colored according to pixels in an image.
**

    let img;
    let smallPoint, largePoint;

    function preload() {
      img = loadImage('assets/moonwalk.jpg');
    }

    function setup() {
      createCanvas(720, 400);
      smallPoint = 4;
      largePoint = 40;
      imageMode(CENTER);
      noStroke();
      background(255);
      img.loadPixels();
    }

    function draw() {
      let pointillize = map(mouseX, 0, width, smallPoint, largePoint);
      let x = floor(random(img.width));
      let y = floor(random(img.height));
      let pix = img.get(x, y);
      fill(pix, 128);
      ellipse(x, y, pointillize, pointillize);
    }

### Blur

**This example is ported from the Blur example on the Processing website
**

<img width="640" alt="Screen Shot 2023-08-21 at 6 46 54 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/eac923f8-fd65-41f0-bc2e-f9c1ee135725">

**A low-pass filter that blurs an image. This program analyzes every pixel in an image and blends it with all the neighboring pixels to blur the image. 
**

  // to consider all neighboring pixels we use a 3x3 array
  // and normalize these values
  // v is the normalized value

    let v = 1.0 / 9.0;
  // kernel is the 3x3 matrix of normalized values

    let kernel = [
      [v, v, v],
      [v, v, v],
      [v, v, v]
    ];

   // preload() runs once, before setup()
   // loadImage() needs to occur here instead of setup()
   // if loadImage() is called in setup(), the image won't appear
   // since noLoop() restricts draw() to execute only once
   // (one execution of draw() is not enough time for the image to load),
   // preload() makes sure image is loaded before anything else occurs

    function preload() {
   // load the original image

      img = loadImage('assets/rover.png');
    }
   // setup() runs once after preload

    function setup() {
   // create canvas
    
        createCanvas(710, 400);
   // noLoop() makes draw() run only once, not in a loop

      noLoop();
    }
   // draw() runs after setup(), normally on a loop
   // in this case it runs only once, because of noDraw()

    function draw() {
   // place the original image on the upper left corner
 
      image(img, 0, 0);
   // create a new image, same dimensions as img

      edgeImg = createImage(img.width, img.height);
   // load its pixels
  
      edgeImg.loadPixels();
   // two for() loops, to iterate in x axis and y axis
   // since the kernel assumes that the pixel
   // has pixels above, under, left, and right
   // we need to skip the first and last column and row
   // x then goes from 1 to width - 1
   // y then goes from 1 to height - 1
     
      for (let x = 1; x < img.width; x++) {
        for (let y = 1; y < img.height; y++) {
   // kernel sum for the current pixel starts as 0
      
      let sum = 0;
   // kx, ky variables for iterating over the kernel
   // kx, ky have three different values: -1, 0, 1
    
      for (kx = -1; kx <= 1; kx++) {
        for (ky = -1; ky <= 1; ky++) {
          let xpos = x + kx;
          let ypos = y + ky;
   // since our image is grayscale,
   // RGB values are identical
   // we retrieve the red value for this example
   // (green and blue work as well)
         
          let val = red(img.get(xpos, ypos));
   // accumulate the  kernel sum
   // kernel is a 3x3 matrix
   // kx and ky have values -1, 0, 1
   // if we add 1 to kx and ky, we get 0, 1, 2
   // with that we can use it to iterate over kernel
   // and calculate the accumulated sum
        
          sum += kernel[kx + 1][ky + 1] * val;
        }
      }
   // set the value of the edgeImg pixel to the kernel sum
     
          edgeImg.set(x, y, color(sum));
        }
      }
   // updatePixels() to write the changes on edgeImg

      edgeImg.updatePixels();
   // draw edgeImg at the right of the original image
 
      image(edgeImg, img.width, 0);
    }

## Color 

### Hue

<img width="717" alt="Screen Shot 2023-08-21 at 7 03 54 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/6959c82b-6fbe-44b7-b5b9-90ef9f5da4ff">

**Hue is the color reflected from or transmitted through an object and is typically referred to as the name of the color (red, blue, yellow, etc.) Move the cursor vertically over each bar to alter its hue.
**

    const barWidth = 20;
    let lastBar = -1;

    function setup() {
      createCanvas(720, 400);
      colorMode(HSB, height, height, height);
      noStroke();
      background(0);
    }

    function draw() {
      let whichBar = mouseX / barWidth;
      if (whichBar !== lastBar) {
        let barX = whichBar * barWidth;
        fill(mouseY, height, height);
        rect(barX, 0, barWidth, height);
        lastBar = whichBar;
      }
    }

### Saturation

<img width="718" alt="Screen Shot 2023-08-21 at 7 06 47 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/a11c3ac4-e5c0-467d-9e34-5ad8c4fc4e10">

**Saturation is the strength or purity of the color and represents the amount of gray in proportion to the hue. A "saturated" color is pure and an "unsaturated" color has a large percentage of gray. Move the cursor vertically over each bar to alter its saturation.
**

    const barWidth = 20;
    let lastBar = -1;

    function setup() {
      createCanvas(720, 400);
      colorMode(HSB, width, height, 100);
      noStroke();
    }
    function draw() {
      let whichBar = mouseX / barWidth;
      if (whichBar !== lastBar) {
        let barX = whichBar * barWidth;
        fill(barX, mouseY, 66);
        rect(barX, 0, barWidth, height);
        lastBar = whichBar;
      }
    }

### Color Variables

<img width="709" alt="Screen Shot 2023-08-21 at 7 11 11 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/47bf522e-6df9-42a0-a641-c9ffee75215c">

**(Homage to Albers.) This example creates variables for colors that may be referred to in the program by a name, rather than a number.
**

    function setup() {
      createCanvas(710, 400);
      noStroke();
      background(51, 0, 0);

      let inside = color(204, 102, 0);
      let middle = color(204, 153, 0);
      let outside = color(153, 51, 0);

  // These statements are equivalent to the statements above.
  // Programmers may use the format they prefer.
  //let inside = color('#CC6600');
  //let middle = color('#CC9900');
  //let outside = color('#993300');

      push();
      translate(80, 80);
      fill(outside);
      rect(0, 0, 200, 200);
      fill(middle);
      rect(40, 60, 120, 120);
      fill(inside);
      rect(60, 90, 80, 80);
      pop();

      push();
      translate(360, 80);
      fill(inside);
      rect(0, 0, 200, 200);
      fill(outside);
      rect(40, 60, 120, 120);
      fill(middle);
      rect(60, 90, 80, 80);
      pop();
    }

### Relativity

<img width="708" alt="Screen Shot 2023-08-21 at 7 14 13 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/b03bd139-b98f-4b9d-be6a-3e7c82046a49">

**Each color is perceived in relation to other colors. The top and bottom bars each contain the same component colors, but a different display order causes individual colors to appear differently.
**

    let a, b, c, d, e;

    function setup() {
      createCanvas(710, 400);
      noStroke();
      a = color(165, 167, 20);
      b = color(77, 86, 59);
      c = color(42, 106, 105);
      d = color(165, 89, 20);
      e = color(146, 150, 127);
      noLoop(); // Draw only one time
    }
    function draw() {
      drawBand(a, b, c, d, e, 0, width / 128);
      drawBand(c, a, d, b, e, height / 2, width / 128);
    }
    function drawBand(v, w, x, y, z, ypos, barWidth) {
      let num = 5;
      let colorOrder = [v, w, x, y, z];
      for (let i = 0; i < width; i += barWidth * num) {
        for (let j = 0; j < num; j++) {
          fill(colorOrder[j]);
          rect(i + j * barWidth, ypos, barWidth, height / 2);
        }
      }
    }

### Linear Gradient

<img width="705" alt="Screen Shot 2023-08-21 at 7 17 19 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/1a824a23-1efb-48f6-8cf7-071daefc99a2">

**The lerpColor() function is useful for interpolating between two colors.
**

// Constants

    const Y_AXIS = 1;
    const X_AXIS = 2;
    let b1, b2, c1, c2;
    function setup() {
      createCanvas(710, 400);
  // Define colors
  
      b1 = color(255);
      b2 = color(0);
      c1 = color(204, 102, 0);
      c2 = color(0, 102, 153);
      noLoop();
    }
    function draw() {
  // Background
 
      setGradient(0, 0, width / 2, height, b1, b2, X_AXIS);
      setGradient(width / 2, 0, width / 2, height, b2, b1, X_AXIS);
  // Foreground

      setGradient(50, 90, 540, 80, c1, c2, Y_AXIS);
      setGradient(50, 190, 540, 80, c2, c1, X_AXIS);
    }
    function setGradient(x, y, w, h, c1, c2, axis) {
      noFill();
      if (axis === Y_AXIS) {
  // Top to bottom gradient
    
    for (let i = y; i <= y + h; i++) {
      let inter = map(i, y, y + h, 0, 1);
      let c = lerpColor(c1, c2, inter);
      stroke(c);
      line(x, i, x + w, i);
    }
      } else if (axis === X_AXIS) {
  // Left to right gradient
       
        for (let i = x; i <= x + w; i++) {
          let inter = map(i, x, x + w, 0, 1);
          let c = lerpColor(c1, c2, inter);
          stroke(c);
          line(i, y, i, y + h);
        }
      }
    }

### Radial Gradient

<img width="710" alt="Screen Shot 2023-08-21 at 7 25 49 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/3265744e-ad11-4933-8ae0-9f882ac2404d">

**Draws a series of concentric circles to create a gradient from one color to another.
**

    let dim;

    function setup() {
      createCanvas(710, 400);
      dim = width / 2;
      background(0);
      colorMode(HSB, 360, 100, 100);
      noStroke();
      ellipseMode(RADIUS);
      frameRate(1);
    }
    function draw() {
      background(0);
      for (let x = 0; x <= width; x += dim) {
        drawGradient(x, height / 2);
      }
    }
    function drawGradient(x, y) {
      let radius = dim / 2;
      let h = random(0, 360);
      for (let r = radius; r > 0; --r) {
        fill(h, 90, 90);
        ellipse(x, y, r, r);
        h = (h + 1) % 360;
      }
    }

### Lerp Color

<img width="723" alt="Screen Shot 2023-08-21 at 7 32 36 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/68f1171f-bbbd-4ee1-9dc3-e0938816cb93">

**Loop random shapes, lerp color from red to blue.
**

    function setup() {
      createCanvas(720, 400);
      background(255);
      noStroke();
    }
    function draw() {
      background(255);
      from = color(255, 0, 0, 0.2 * 255);
      to = color(0, 0, 255, 0.2 * 255);
      c1 = lerpColor(from, to, 0.33);
      c2 = lerpColor(from, to, 0.66);
      for (let i = 0; i < 15; i++) {
        fill(from);
        quad(
          random(-40, 220), random(height),
          random(-40, 220), random(height),
          random(-40, 220), random(height),
          random(-40, 220), random(height)
        );
        fill(c1);
        quad(
          random(140, 380), random(height),
          random(140, 380), random(height),
          random(140, 380), random(height),
          random(140, 380), random(height)
        );
        fill(c2);
        quad(
          random(320, 580), random(height),
          random(320, 580), random(height),
          random(320, 580), random(height),
          random(320, 580), random(height)
        );
        fill(to);
        quad(
          random(500, 760), random(height),
          random(500, 760), random(height),
          random(500, 760), random(height),
          random(500, 760), random(height)
        );
      }
      frameRate(5);
    }

## Math
### Increment Decrement

<img width="709" alt="Screen Shot 2023-08-21 at 7 36 20 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/950ef926-e66b-4873-b987-c47a2fe602c0">

**Writing "a++" is equivalent to "a = a + 1". Writing "a--" is equivalent to "a = a - 1".
**

    let a;
    let b;
    let direction;

    function setup() {
      createCanvas(710, 400);
      colorMode(RGB, width);
      a = 0;
      b = width;
      direction = true;
      frameRate(30);
    }
    function draw() {
      a++;
      if (a > width) {
        a = 0;
        direction = !direction;
      }
      if (direction === true) {
        stroke(a);
      } else {
        stroke(width - a);
      }
      line(a, 0, a, height / 2);
      b--;
      if (b < 0) {
        b = width;
      }
      if (direction == true) {
        stroke(width - b);
      } else {
        stroke(b);
      }
      line(b, height / 2 + 1, b, height);
    }


### Operator Precedence

<img width="709" alt="Screen Shot 2023-08-21 at 7 43 14 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/23e3b90a-e098-4fca-8f70-60a378c09c46">

**Move the mouse left and right to control the speed and direction of the moving shapes.
**

// The highest precedence is at the top of the list and
// the lowest is at the bottom.
// Multiplicative: * / %
// Additive: + -
// Relational: < > <= >=
// Equality: == !=
// Logical AND: &&
// Logical OR: ||
// Assignment: = += -= *= /= %=

    function setup() {
      createCanvas(710, 400);
      background(51);
      noFill();
      stroke(51);
      stroke(204);
      for (let i = 0; i < width - 20; i += 4) {
// The 30 is added to 70 and then evaluated
// if it is greater than the current value of "i"
// For clarity, write as "if (i > (30 + 70)) {"
    
       if (i > 30 + 70) {
          line(i, 0, i, 50);
        }
      }
      stroke(255);
// The 2 is multiplied by the 8 and the result is added to the 4
// For clarity, write as "rect(5 + (2 * 8), 0, 90, 20);"
 
      rect(4 + 2 * 8, 52, 290, 48);
      rect((4 + 2) * 8, 100, 290, 49);

      stroke(153);
      for (let i = 0; i < width; i += 2) {

// The relational statements are evaluated
// first, and then the logical AND statements and
// finally the logical OR. For clarity, write as:
// "if(((i > 20) && (i < 50)) || ((i > 100) && (i < width-20))) {"
  
        if ((i > 20 && i < 50) || (i > 100 && i < width - 20)) {
          line(i, 151, i, height - 1);
        }
      }
    }

### Distance 1D

<img width="711" alt="Screen Shot 2023-08-21 at 7 41 42 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/b7c2cfa8-597d-4dec-be84-4538504d08c0">

**Move the mouse left and right to control the speed and direction of the moving shapes.
**

    let xpos1;
    let xpos2;
    let xpos3;
    let xpos4;
    let thin = 8;
    let thick = 36;

    function setup() {
      createCanvas(710, 400);
      noStroke();
      xpos1 = width / 2;
      xpos2 = width / 2;
      xpos3 = width / 2;
      xpos4 = width / 2;
    }

    function draw() {
      background(0);

      let mx = mouseX * 0.4 - width / 5.0;

      fill(102);
      rect(xpos2, 0, thick, height / 2);
      fill(204);
      rect(xpos1, 0, thin, height / 2);
      fill(102);
      rect(xpos4, height / 2, thick, height / 2);
      fill(204);
      rect(xpos3, height / 2, thin, height / 2);

      xpos1 += mx / 16;
      xpos2 += mx / 64;
      xpos3 -= mx / 16;
      xpos4 -= mx / 64;

      if (xpos1 < -thin) {
        xpos1 = width;
      }
      if (xpos1 > width) {
        xpos1 = -thin;
      }
      if (xpos2 < -thick) {
        xpos2 = width;
      }
      if (xpos2 > width) {
        xpos2 = -thick;
      }
      if (xpos3 < -thin) {
        xpos3 = width;
      }
      if (xpos3 > width) {
        xpos3 = -thin;
      }
      if (xpos4 < -thick) {
        xpos4 = width;
      }
      if (xpos4 > width) {
        xpos4 = -thick;
      }
    }

### Distance 2D

<img width="697" alt="Screen Shot 2023-08-21 at 8 12 21 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/8de350bb-605f-4b97-917a-509415ec3897">

**Move the mouse across the image to obscure and reveal the matrix. Measures the distance from the mouse to each circle and sets the size proportionally.
**

    let max_distance;

    function setup() {
      createCanvas(710, 400);
      noStroke();
      max_distance = dist(0, 0, width, height);
    }

    function draw() {
      background(0);

      for (let i = 0; i <= width; i += 20) {
        for (let j = 0; j <= height; j += 20) {
          let size = dist(mouseX, mouseY, i, j);
          size = (size / max_distance) * 66;
          ellipse(i, j, size, size);
        }
      }
    }

### Sine

<img width="710" alt="Screen Shot 2023-08-21 at 8 16 43 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/ee081481-bc37-4449-a048-d66aff7b8e2f">

**Smoothly scaling size with the sin() function.
**

    let diameter;
    let angle = 0;

    function setup() {
      createCanvas(710, 400);
      diameter = height - 10;
      noStroke();
      fill(255, 204, 0);
    }

    function draw() {
      background(0);

      let d1 = 10 + (sin(angle) * diameter) / 2 + diameter / 2;
      let d2 = 10 + (sin(angle + PI / 2) * diameter) / 2 + diameter / 2;
      let d3 = 10 + (sin(angle + PI) * diameter) / 2 + diameter / 2;

      ellipse(0, height / 2, d1, d1);
      ellipse(width / 2, height / 2, d2, d2);
      ellipse(width, height / 2, d3, d3);

      angle += 0.02;
    }

### Sine Cosine

<img width="711" alt="Screen Shot 2023-08-21 at 8 19 13 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/c0b32e6d-c0ca-4d5d-8e1e-a75ab85b6d1e">

**Linear movement with sin() and cos(). Numbers between 0 and 2π (2π which angles roughly 6.28) are put into these functions and numbers between -1 and 1 are returned. These values are then scaled to produce larger movements.
**

    let angle1 = 0;
    let angle2 = 0;
    let scalar = 70;

    function setup() {
      createCanvas(710, 400);
      noStroke();
      rectMode(CENTER);
    }

    function draw() {
      background(0);

      let ang1 = radians(angle1);
      let ang2 = radians(angle2);

      let x1 = width / 2 + scalar * cos(ang1);
      let x2 = width / 2 + scalar * cos(ang2);

      let y1 = height / 2 + scalar * sin(ang1);
      let y2 = height / 2 + scalar * sin(ang2);

      fill(255);
      rect(width * 0.5, height * 0.5, 140, 140);

      fill(0, 102, 153);
      ellipse(x1, height * 0.5 - 120, scalar, scalar);
      ellipse(x2, height * 0.5 + 120, scalar, scalar);

      fill(255, 204, 0);
      ellipse(width * 0.5 - 120, y1, scalar, scalar);
      ellipse(width * 0.5 + 120, y2, scalar, scalar);

      angle1 += 2;
      angle2 += 3;
    }

### Additive Wave

<img width="708" alt="Screen Shot 2023-08-21 at 8 21 43 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/eb215876-f713-4ecc-ab61-065de50c784b">

**Create a more complex wave by adding two waves together. Original by Daniel Shiffman
**

    let xspacing = 8; // Distance between each horizontal location
    let w; // Width of entire wave
    let maxwaves = 4; // total # of waves to add together

    let theta = 0.0;
    let amplitude = new Array(maxwaves); // Height of wave
// Value for incrementing X, to be calculated
// as a function of period and xspacing

    let dx = new Array(maxwaves);
// Using an array to store height values
// for the wave (not entirely necessary)

    let yvalues;

    function setup() {
      createCanvas(710, 400);
      frameRate(30);
      colorMode(RGB, 255, 255, 255, 100);
      w = width + 16;

      for (let i = 0; i < maxwaves; i++) {
        amplitude[i] = random(10, 30);
        let period = random(100, 300); // Num pixels before wave repeats
        dx[i] = (TWO_PI / period) * xspacing;
      }
      yvalues = new Array(floor(w / xspacing));
    }
    function draw() {
      background(0);
      calcWave();
      renderWave();
    }
    function calcWave() {
// Increment theta (try different values
// for 'angular velocity' here

      theta += 0.02;
// Set all height values to zero
 
      for (let i = 0; i < yvalues.length; i++) {
        yvalues[i] = 0;
      }
// Accumulate wave height values

      for (let j = 0; j < maxwaves; j++) {
        let x = theta;
        for (let i = 0; i < yvalues.length; i++) {
// Every other wave is cosine instead of sine
   
          if (j % 2 == 0) yvalues[i] += sin(x) * amplitude[j];
          else yvalues[i] += cos(x) * amplitude[j];
          x += dx[j];
        }
      }
    }
    function renderWave() {
// A simple way to draw the wave with an ellipse at each location
 
      noStroke();
      fill(255, 50);
      ellipseMode(CENTER);
      for (let x = 0; x < yvalues.length; x++) {
        ellipse(x * xspacing, width / 2 + yvalues[x], 16, 16);
      }
    }

### Sine Wave

<img width="711" alt="Screen Shot 2023-08-21 at 8 24 15 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/29acee21-9360-4fce-ad46-e0588b50603b">

**Render a simple sine wave. Original by Daniel Shiffman.
**

    let xspacing = 16; // Distance between each horizontal location
    let w; // Width of entire wave
    let theta = 0.0; // Start angle at 0
    let amplitude = 75.0; // Height of wave
    let period = 500.0; // How many pixels before the wave repeats
    let dx; // Value for incrementing x
    let yvalues; // Using an array to store height values for the wave
    function setup() {
      createCanvas(710, 400);
      w = width + 16;
      dx = (TWO_PI / period) * xspacing;
      yvalues = new Array(floor(w / xspacing));
    }
    function draw() {
      background(0);
      calcWave();
      renderWave();
    }
    function calcWave() {
// Increment theta (try different values for
// 'angular velocity' here)

      theta += 0.02;
// For every x value, calculate a y value with sine function

      let x = theta;
      for (let i = 0; i < yvalues.length; i++) {
        yvalues[i] = sin(x) * amplitude;
            x += dx;
     }
    }
    function renderWave() {
      noStroke();
      fill(255);
// A simple way to draw the wave with an ellipse at each location
 
      for (let x = 0; x < yvalues.length; x++) {
        ellipse(x * xspacing, height / 2 + yvalues[x], 16, 16);
      }
    }
    
### PolarToCartesian

<img width="707" alt="Screen Shot 2023-08-21 at 8 28 22 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/8f43fa47-26aa-40fc-9304-2ac355afa628">

**Convert a polar coordinate (r,θ) to cartesian (x,y): x = r cos(θ), y = r sin(θ) Original by Daniel Shiffman.
**

    let r;

// Angle and angular velocity, accleration

    let theta;
    let theta_vel;
    let theta_acc;
    function setup() {
      createCanvas(710, 400);

// Initialize all values
  
      r = height * 0.45;
      theta = 0;
      theta_vel = 0;
      theta_acc = 0.0001;
    }

    function draw() {
      background(0);

// Translate the origin point to the center of the screen

      translate(width / 2, height / 2);

// Convert polar to cartesian

      let x = r * cos(theta);
      let y = r * sin(theta);

// Draw the ellipse at the cartesian coordinate
 
      ellipseMode(CENTER);
      noStroke();
      fill(200);
      ellipse(x, y, 32, 32);

// Apply acceleration and velocity to angle
// (r remains static in this example)

      theta_vel += theta_acc;
      theta += theta_vel;
    }

### Double Random

<img width="707" alt="Screen Shot 2023-08-22 at 10 47 43 AM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/27edd09a-862f-465b-a51b-0d92b996aeb7">

**Using two random() calls and the point() function to create an irregular sawtooth line. Original by by Ira Greenberg.
**

    let totalPts = 300;
    let steps = totalPts + 1;

    function setup() {
      createCanvas(710, 400);
      stroke(255);
      frameRate(1);
    }

    function draw() {
      background(0);
      let rand = 0;
      for (let i = 1; i < steps; i++) {
        point((width / steps) * i, height / 2 + random(-rand, rand));
        rand += random(-5, 5);
      }
    }

### Random

<img width="711" alt="Screen Shot 2023-08-22 at 10 55 48 AM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/01a668ad-6348-4f13-ac07-e3c767e724e1">

**Random numbers create the basis of this image. Each time the program is loaded the result is different.
**

    function setup() {
      createCanvas(710, 400);
      background(0);
      strokeWeight(20);
      frameRate(2);
    }

    function draw() {
      for (let i = 0; i < width; i++) {
        let r = random(255);
        stroke(r);
        line(i, 0, i, height);
      }
    }

### Noise1D

<img width="709" alt="Screen Shot 2023-08-22 at 10 57 42 AM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/a6be2e97-a019-4184-a0f0-a0bef05e90ac">

**Using 1D Perlin Noise to assign location.
**

    let xoff = 0.0;
    let xincrement = 0.01;

    function setup() {
      createCanvas(710, 400);
      background(0);
      noStroke();
    }
    function draw() {
// Create an alpha blended background
 
      fill(0, 10);
      rect(0, 0, width, height);

//let n = random(0,width);  // Try this line instead of noise

// Get a noise value based on xoff and scale
// it according to the window's width
 
      let n = noise(xoff) * width;
// With each cycle, increment xoff
    
        xoff += xincrement;
// Draw the ellipse at the value produced by perlin noise

      fill(200);
      ellipse(n, height / 2, 64, 64);
    }

### Noise Wave

<img width="707" alt="Screen Shot 2023-08-22 at 11 02 58 AM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/4f1304c8-f1fe-497a-b359-5ab6a641cfb5">

**Using Perlin Noise to generate a wave-like pattern. Original by Daniel Shiffman.
**

    let yoff = 0.0; // 2nd dimension of perlin noise
    function setup() {
      createCanvas(710, 400);
    }
    function draw() {
      background(51);
      fill(255);
// We are going to draw a polygon out of the wave points

      beginShape();
      let xoff = 0; // Option #1: 2D Noise
// let xoff = yoff; // Option #2: 1D Noise

// Iterate over horizontal pixels
  
    for (let x = 0; x <= width; x += 10) {
// Calculate a y value according to noise, map to

// Option #1: 2D Noise
   
    let y = map(noise(xoff, yoff), 0, 1, 200, 300);
// Option #2: 1D Noise
// let y = map(noise(xoff), 0, 1, 200,300);

// Set the vertex
 
    vertex(x, y);
// Increment x dimension for noise
  
    xoff += 0.05;
      }
  // increment y dimension for noise
  
      yoff += 0.01;
      vertex(width, height);
      vertex(0, height);
      endShape(CLOSE);
    }

### Noise2D

<img width="640" alt="Screen Shot 2023-08-22 at 11 35 43 AM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/e7791d3d-940f-4864-9e4a-706fbcd519c3">

**Create a 2D noise with different parameters. *
**

    let noiseVal;
    let noiseScale = 0.02;

    function setup() {
      createCanvas(640, 360);
    }
    function draw() {
      background(0);
// Draw the left half of image
  
      for (let y = 0; y < height - 30; y++) {
        for (let x = 0; x < width / 2; x++) {
// noiseDetail of the pixels octave count and falloff value
        
          noiseDetail(2, 0.2);
          noiseVal = noise((mouseX + x) * noiseScale, (mouseY + y) * noiseScale);
          stroke(noiseVal * 255);
          point(x, y);
        }
      }
  // Draw the right half of image
  
      for (let y = 0; y < height - 30; y++) {
        for (let x = width / 2; x < width; x++) {
      // noiseDetail of the pixels octave count and falloff value
   
          noiseDetail(5, 0.5);
          noiseVal = noise((mouseX + x) * noiseScale, (mouseY + y) * noiseScale);
          stroke(noiseVal * 255);
          point(x, y);
        }
      }
  //Show the details of two partitions
 
      textSize(18);
      fill(255, 255, 255);
      text('Noise2D with 2 octaves and 0.2 falloff', 10, 350);
      text('Noise2D with 1 octaves and 0.7 falloff', 330, 350);
    }

### Noise3D

<img width="640" alt="Screen Shot 2023-08-22 at 11 40 56 AM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/45b2670d-c1cc-4d29-8d96-6d8bb7434f15">

**Using 3D noise to create simple animated texture.
**

    let noiseVal;
//Increment x by 0.01

    let x_increment = 0.01;
//Increment z by 0.02 every draw() cycle

    let z_increment = 0.02;
//Offset values

    let z_off, y_off, x_off;
    function setup() {
//Create the Canvas
 
      createCanvas(640, 360);
//Define frame rate

      frameRate(20);
//Initial value of z_off

      z_off = 0;
    }
    function draw() {
      x_off = 0;
      y_off = 0;
//Make the background black
 
      background(0);
//Adjust the noice detail
 
      noiseDetail(8, 0.65);
//For each x,y calculate noice value

      for (let y = 0; y < height; y++) {
        x_off += x_increment;
        y_off = 0;
        for (let x = 0; x < width; x++) {
//Calculate and Draw each pixel
  
      noiseVal = noise(x_off, y_off, z_off);
      stroke(noiseVal * 255);
      y_off += x_increment;
      point(x, y);
        }
      }
      z_off += z_increment;
    }

### Random Chords

<img width="705" alt="Screen Shot 2023-08-22 at 11 50 57 AM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/30d2ac2b-b697-4633-b3c7-0bb1ddec9ee6">

**Accumulates random chords of a circle. Each chord in translucent so they accumulate to give the illusion of a shaded sphere. Contributed by Aatish Bhatia, inspired by Anders Hoff
**

    function setup() {
      createCanvas(400, 400);
      background(255, 255, 255);
// translucent stroke using alpha value
  
      stroke(0, 0, 0, 15);
    }
    function draw() {
// draw two random chords each frame

      randomChord();
      randomChord();
    }
    function randomChord() {
// find a random point on a circle
  
      let angle1 = random(0, 2 * PI);
      let xpos1 = 200 + 200 * cos(angle1);
      let ypos1 = 200 + 200 * sin(angle1);
// find another random point on the circle

      let angle2 = random(0, 2 * PI);
      let xpos2 = 200 + 200 * cos(angle2);
      let ypos2 = 200 + 200 * sin(angle2);
// draw a line between them
  
      line(xpos1, ypos1, xpos2, ypos2);
    }

### Random Gaussian

<img width="716" alt="Screen Shot 2023-08-22 at 11 54 11 AM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/1fad1834-5948-481f-9e83-f31692265f99">

**This example is ported from the Random Gaussian example on the Processing website
**
**This sketch draws ellipses with x and y locations tied to a gaussian distribution of random numbers. 
**

      function setup() {
        createCanvas(720, 400);
        background(0);
      }
      function draw() {
// Get a gaussian random number w/ mean of 0 and standard deviation of 1.0
    
        let val = randomGaussian();
        let sd = 60;                
// Define a standard deviation
       
        let mean = width/2;          
// Define a mean value (middle of the screen along the x-axis)
       
        let x = ( val * sd ) + mean; 
// Scale the gaussian random number by standard deviation and mean
        
        noStroke();
        fill(255, 10);
        ellipse(x, height/2, 32, 32);   
// Draw an ellipse at our "normal" random location
          }

### Map

<img width="718" alt="Screen Shot 2023-08-22 at 12 04 19 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/fa951bc4-97a9-4ba4-8994-91bdd15ddb14">

**Use the map() function to take any number and scale it to a new number that is more useful for the project that you are working on. For example, use the numbers from the mouse position to control the size or color of a shape. In this example, the mouse’s x-coordinate (numbers between 0 and 360) are scaled to new numbers to define the color and size of a circle.
**

    function setup() {
      createCanvas(720, 400);
      noStroke();
    }
    function draw() {
      background(0);
// Scale the mouseX value from 0 to 720 to a range between 0 and 175
 
      let c = map(mouseX, 0, width, 0, 175);
// Scale the mouseX value from 0 to 720 to a range between 40 and 300
  
      let d = map(mouseX, 0, width, 40, 300);
      fill(255, c, 0);
      ellipse(width/2, height/2, d, d);
    }

### Parametric Equations

<img width="728" alt="Screen Shot 2023-08-22 at 12 12 45 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/905350ce-6ae3-49db-b7b4-abbeb6f93973">

**A parametric equation is where x and y coordinates are both written in terms of another letter. This is called a parameter and is usually given in the letter t or θ. The inspiration was taken from the YouTube channel of Alexander Miller.
**

    function setup(){
      createCanvas(720,400);
    }
// the parameter at which x and y depends is usually taken as either t or symbol of theta

    let t = 0;
    function draw(){
      background('#fff');
      translate(width/2,height/2);
      stroke('#0f0f0f');
      strokeWeight(1.5);
//loop for adding 100 lines
  
      for(let i = 0;i<100;i++){
        line(x1(t+i),y1(t+i),x2(t+i)+20,y2(t+i)+20);
      }
      t+=0.15;
    }
// function to change initial x co-ordinate of the line

    function x1(t){
      return sin(t/10)*125+sin(t/20)*125+sin(t/30)*125;
    }
// function to change initial y co-ordinate of the line

    function y1(t){
      return cos(t/10)*125+cos(t/20)*125+cos(t/30)*125;
    }
// function to change final x co-ordinate of the line

    function x2(t){
      return sin(t/15)*125+sin(t/25)*125+sin(t/35)*125;
    }
// function to change final y co-ordinate of the line

    function y2(t){
      return cos(t/15)*125+cos(t/25)*125+cos(t/35)*125;
    }

## Simulate
### Forces

<img width="634" alt="Screen Shot 2023-08-22 at 12 18 58 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/9d8289a9-9ac9-41d1-bba7-70a7ca7097e8">

**Demonstration of multiple force acting on bodies (natureofcode.com)
**

// Demonstration of multiple force acting on
// bodies (Mover class)
// Bodies experience gravity continuously
// Bodies experience fluid resistance when in "water"
// Nine moving bodies

    let movers = [];
// Liquid

    let liquid;
    function setup() {
      createCanvas(640, 360);
      reset();
// Create liquid object
  
      liquid = new Liquid(0, height / 2, width, height / 2, 0.1);
    }
    function draw() {
      background(127);
// Draw water

      liquid.display();
      for (let i = 0; i < movers.length; i++) {
// Is the Mover in the liquid?
   
        if (liquid.contains(movers[i])) {
// Calculate drag force
      
          let dragForce = liquid.calculateDrag(movers[i]);
// Apply drag force to Mover
         
          movers[i].applyForce(dragForce);
        }
// Gravity is scaled by mass here!

        let gravity = createVector(0, 0.1 * movers[i].mass);
// Apply gravity
   
        movers[i].applyForce(gravity);
// Update and display

        movers[i].update();
        movers[i].display();
        movers[i].checkEdges();
      }
    }
    function mousePressed() {
      reset();
    }
// Restart all the Mover objects randomly

    function reset() {
      for (let i = 0; i < 9; i++) {
        movers[i] = new Mover(random(0.5, 3), 40 + i * 70, 0);
      }
    }
    let Liquid = function(x, y, w, h, c) {
      this.x = x;
      this.y = y;
      this.w = w;
      this.h = h;
      this.c = c;
    };
// Is the Mover in the Liquid?

    Liquid.prototype.contains = function(m) {
      let l = m.position;
      return (
        l.x > this.x &&
        l.x < this.x + this.w &&
        l.y > this.y &&
        l.y < this.y + this.h
      );
    };
// Calculate drag force

    Liquid.prototype.calculateDrag = function(m) {
// Magnitude is coefficient * speed squared

      let speed = m.velocity.mag();
      let dragMagnitude = this.c * speed * speed;

// Direction is inverse of velocity

      let dragForce = m.velocity.copy();
      dragForce.mult(-1);
// Scale according to magnitude
// dragForce.setMag(dragMagnitude);
 
      dragForce.normalize();
      dragForce.mult(dragMagnitude);
      return dragForce;
    };
    Liquid.prototype.display = function() {
      noStroke();
      fill(50);
      rect(this.x, this.y, this.w, this.h);
    };
    function Mover(m, x, y) {
      this.mass = m;
      this.position = createVector(x, y);
      this.velocity = createVector(0, 0);
      this.acceleration = createVector(0, 0);
    }
// Newton's 2nd law: F = M * A
// or A = F / M

    Mover.prototype.applyForce = function(force) {
      let f = p5.Vector.div(force, this.mass);
      this.acceleration.add(f);
    };
    Mover.prototype.update = function() {
// Velocity changes according to acceleration

      this.velocity.add(this.acceleration);
// position changes by velocity
  
      this.position.add(this.velocity);
// We must clear acceleration each frame
 
      this.acceleration.mult(0);
    };
    Mover.prototype.display = function() {
      stroke(0);
      strokeWeight(2);
      fill(255, 127);
      ellipse(this.position.x, this.position.y, this.mass * 16, this.mass * 16);
    };
// Bounce off bottom of window

    Mover.prototype.checkEdges = function() {
      if (this.position.y > height - this.mass * 8) {
// A little dampening when hitting the bottom
  
        this.velocity.y *= -0.9;
        this.position.y = height - this.mass * 8;
      }
    };

### Particle System

<img width="718" alt="Screen Shot 2023-08-22 at 12 52 42 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/f8d19539-77b4-4dc0-bc41-9a136c648936">

**This is a basic Particle System (natureofcode.com)
**

    let system;
    function setup() {
      createCanvas(720, 400);
      system = new ParticleSystem(createVector(width / 2, 50));
    }
    function draw() {
      background(51);
      system.addParticle();
      system.run();
    }
// A simple Particle class

    let Particle = function(position) {
      this.acceleration = createVector(0, 0.05);
      this.velocity = createVector(random(-1, 1), random(-1, 0));
      this.position = position.copy();
      this.lifespan = 255;
    };
    Particle.prototype.run = function() {
      this.update();
      this.display();
    };
// Method to update position

    Particle.prototype.update = function(){
      this.velocity.add(this.acceleration);
      this.position.add(this.velocity);
      this.lifespan -= 2;
    };
// Method to display

    Particle.prototype.display = function() {
      stroke(200, this.lifespan);
      strokeWeight(2);
      fill(127, this.lifespan);
      ellipse(this.position.x, this.position.y, 12, 12);
    };
// Is the particle still useful?

    Particle.prototype.isDead = function(){
      return this.lifespan < 0;
    };
    let ParticleSystem = function(position) {
      this.origin = position.copy();
      this.particles = [];
    };
    ParticleSystem.prototype.addParticle = function() {
      this.particles.push(new Particle(this.origin));
    };
    ParticleSystem.prototype.run = function() {
      for (let i = this.particles.length-1; i >= 0; i--) {
        let p = this.particles[i];
        p.run();
        if (p.isDead()) {
          this.particles.splice(i, 1);
        }
      }
    };



### Flocking

<img width="645" alt="Screen Shot 2023-08-22 at 1 37 44 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/4ee4be6e-148d-4975-953c-7a9deb133520">

**Demonstration of Craig Reynolds' "Flocking" behavior. See: http://www.red3d.com/cwr/ Rules: Cohesion, Separation, Alignment (from natureofcode.com). Drag mouse to add boids into the system.
**
    let flock;

    function setup() {
      createCanvas(640, 360);
      createP("Drag the mouse to generate new boids.");
      flock = new Flock();
// Add an initial set of boids into the system

      for (let i = 0; i < 100; i++) {
        let b = new Boid(width / 2,height / 2);
        flock.addBoid(b);
      }
    }
    function draw() {
      background(51);
      flock.run();
    }
// Add a new boid into the System

    function mouseDragged() {
      flock.addBoid(new Boid(mouseX, mouseY));
    }
// The Nature of Code
// Daniel Shiffman
// http://natureofcode.com

// Flock object
// Does very little, simply manages the array of all the boids

    function Flock() {
// An array for all the boids
  
      this.boids = []; // Initialize the array
    }
    Flock.prototype.run = function() {
      for (let i = 0; i < this.boids.length; i++) {
        this.boids[i].run(this.boids);  // Passing the entire list of boids to each boid individually
      }
    }
    Flock.prototype.addBoid = function(b) {
      this.boids.push(b);
    }
// The Nature of Code
// Daniel Shiffman
// http://natureofcode.com

// Boid class
// Methods for Separation, Cohesion, Alignment added

    function Boid(x, y) {
      this.acceleration = createVector(0, 0);
      this.velocity = createVector(random(-1, 1), random(-1, 1));
      this.position = createVector(x, y);
      this.r = 3.0;
      this.maxspeed = 3;    // Maximum speed
      this.maxforce = 0.05; // Maximum steering force
    }
    Boid.prototype.run = function(boids) {
      this.flock(boids);
      this.update();
      this.borders();
      this.render();
    }
    Boid.prototype.applyForce = function(force) {
// We could add mass here if we want A = F / M

      this.acceleration.add(force);
    }
// We accumulate a new acceleration each time based on three rules

    Boid.prototype.flock = function(boids) {
      let sep = this.separate(boids);   // Separation
      let ali = this.align(boids);      // Alignment
      let coh = this.cohesion(boids);   // Cohesion
// Arbitrarily weight these forces

      sep.mult(1.5);
      ali.mult(1.0);
      coh.mult(1.0);
// Add the force vectors to acceleration
 
      this.applyForce(sep);
      this.applyForce(ali);
      this.applyForce(coh);
    }
// Method to update location

    Boid.prototype.update = function() {
// Update velocity

      this.velocity.add(this.acceleration);
// Limit speed

      this.velocity.limit(this.maxspeed);
      this.position.add(this.velocity);
// Reset accelertion to 0 each cycle
  
      this.acceleration.mult(0);
    }
// A method that calculates and applies a steering force towards a target
// STEER = DESIRED MINUS VELOCITY

    Boid.prototype.seek = function(target) {
      let desired = p5.Vector.sub(target,this.position);  // A vector pointing from the location to the target
// Normalize desired and scale to maximum speed

      desired.normalize();
      desired.mult(this.maxspeed);
// Steering = Desired minus Velocity
  
      let steer = p5.Vector.sub(desired,this.velocity);
      steer.limit(this.maxforce);  // Limit to maximum steering force
      return steer;
    }
    Boid.prototype.render = function() {
// Draw a triangle rotated in the direction of velocity
  
      let theta = this.velocity.heading() + radians(90);
      fill(127);
      stroke(200);
      push();
      translate(this.position.x, this.position.y);
      rotate(theta);
      beginShape();
      vertex(0, -this.r * 2);
      vertex(-this.r, this.r * 2);
      vertex(this.r, this.r * 2);
      endShape(CLOSE);
      pop();
    }
// Wraparound

    Boid.prototype.borders = function() {
      if (this.position.x < -this.r)  this.position.x = width + this.r;
      if (this.position.y < -this.r)  this.position.y = height + this.r;
      if (this.position.x > width + this.r) this.position.x = -this.r;
      if (this.position.y > height + this.r) this.position.y = -this.r;
    }
// Separation
// Method checks for nearby boids and steers away

    Boid.prototype.separate = function(boids) {
      let desiredseparation = 25.0;
      let steer = createVector(0, 0);
      let count = 0;
// For every boid in the system, check if it's too close
 
      for (let i = 0; i < boids.length; i++) {
        let d = p5.Vector.dist(this.position,boids[i].position);
// If the distance is greater than 0 and less than an arbitrary amount (0 when you are yourself)
   
        if ((d > 0) && (d < desiredseparation)) {
          // Calculate vector pointing away from neighbor
          let diff = p5.Vector.sub(this.position, boids[i].position);
          diff.normalize();
          diff.div(d);        // Weight by distance
          steer.add(diff);
          count++;            // Keep track of how many
        }
      }
// Average -- divide by how many
     
      if (count > 0) {
        steer.div(count);
      }
// As long as the vector is greater than 0
  
      if (steer.mag() > 0) {
// Implement Reynolds: Steering = Desired - Velocity
      
        steer.normalize();
        steer.mult(this.maxspeed);
        steer.sub(this.velocity);
        steer.limit(this.maxforce);
      }
      return steer;
    }
// Alignment
// For every nearby boid in the system, calculate the average velocity

    Boid.prototype.align = function(boids) {
      let neighbordist = 50;
      let sum = createVector(0,0);
      let count = 0;
      for (let i = 0; i < boids.length; i++) {
        let d = p5.Vector.dist(this.position,boids[i].position);
        if ((d > 0) && (d < neighbordist)) {
          sum.add(boids[i].velocity);
          count++;
        }
      }
      if (count > 0) {
        sum.div(count);
        sum.normalize();
        sum.mult(this.maxspeed);
        let steer = p5.Vector.sub(sum, this.velocity);
        steer.limit(this.maxforce);
        return steer;
      } else {
        return createVector(0, 0);
      }
    }
// Cohesion
// For the average location (i.e. center) of all nearby boids, calculate steering vector towards that location

    Boid.prototype.cohesion = function(boids) {
      let neighbordist = 50;
      let sum = createVector(0, 0);   // Start with empty vector to accumulate all locations
      let count = 0;
      for (let i = 0; i < boids.length; i++) {
        let d = p5.Vector.dist(this.position,boids[i].position);
        if ((d > 0) && (d < neighbordist)) {
          sum.add(boids[i].position); // Add location
          count++;
        }
      }
      if (count > 0) {
        sum.div(count);
        return this.seek(sum);  // Steer towards the location
      } else {
        return createVector(0, 0);
      }
    }

### Multiple Particle Systems

<img width="702" alt="Screen Shot 2023-08-22 at 1 53 11 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/9c88f83b-3538-4b2b-8723-d11f733d644e">

**This sketch uses simple transformations to create a Spirograph-like effect with interlocking circles (called sines). Press the spacebar to switch between tracing and showing the underlying geometry.
Example created by R. Luke DuBois.
http://en.wikipedia.org/wiki/Spirograph
**

    let NUMSINES = 20;
// how many of these things can we do at once?

    let sines = new Array(NUMSINES); 
// an array to hold all the current angles

    let rad;
// an initial radius value for the central sine

    let i; 
// a counter variable

// play with these to get a sense of what's going on:

    let fund = 0.005; 
// the speed of the central sine

    let ratio = 1; 
// what multiplier for speed is each additional sine?

    let alpha = 50; 
// how opaque is the tracing system

    let trace = false; 
// are we tracing?

    function setup() {
      createCanvas(710, 400);
      rad = height / 4; 
// compute radius for central circle
 
      background(204); 
// clear the screen

      for (let i = 0; i<sines.length; i++) {
        sines[i] = PI; 
// start EVERYBODY facing NORTH
 
      }
    }
    function draw() {
      if (!trace) {
        background(204); 
// clear screen if showing geometry
   
        stroke(0, 255); 
// black pen
    
        noFill(); 
// don't fill
 
      }
// MAIN ACTION
 
      push(); 
// start a transformation matrix
 
      translate(width / 2, height / 2); 
// move to middle of screen

      for (let i = 0; i < sines.length; i++) {
        let erad = 0; 
// radius for small "point" within circle... this is the 'pen' when tracing
// setup for tracing
      
        if (trace) {
          stroke(0, 0, 255 * (float(i) / sines.length), alpha); 
// blue
     
          fill(0, 0, 255, alpha / 2); 
// also, um, blue
     
          erad = 5.0 * (1.0 - float(i) / sines.length); 
// pen width will be related to which sine
  
        }
        let radius = rad / (i + 1); 
// radius for circle itself //( This (x) f*xCn joks))
   
        rotate(sines[i]); 
// rotate circle
    
        if (!trace) ellipse(0, 0, radius * 2, radius * 2);
// if we're simulating, draw the sine
   
        push(); // go up one level
        translate(0, radius); 
// move to sine edge
  
        if (!trace) ellipse(0, 0, 5, 5); 
// draw a little circle
 
        if (trace) ellipse(0, 0, erad, erad); 
// draw with erad if tracing
  
        pop(); 
// go down one level
  
        translate(0, radius); // move into position for next sine
        sines[i] = (sines[i] + (fund + (fund * i * ratio))) % TWO_PI; 
// update angle based on fundamental
    
          }
      pop();
// pop down final transformation

    }
    function keyReleased() {
      if (key==' ') {
        trace = !trace;
        background(255);
      }
    }

### Spring

<img width="708" alt="Screen Shot 2023-08-22 at 2 06 59 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/0283b5d8-3ec9-4588-a16e-748a13d39c62">

**Click, drag, and release the horizontal bar to start the spring.
**

// Spring drawing constants for top bar

    let springHeight = 32,
        left,
        right,
        maxHeight = 200,
        minHeight = 100,
        over = false,
        move = false;
// Spring simulation constants

    let M = 0.8,  // Mass
        K = 0.2,  // Spring constant
        D = 0.92, // Damping
        R = 150;  // Rest position
// Spring simulation variables

    let ps = R,   // Position
        vs = 0.0, // Velocity
        as = 0,   // Acceleration
        f = 0;    // Force
    function setup() {
      createCanvas(710, 400);
      rectMode(CORNERS);
      noStroke();
      left = width / 2 - 100;
      right = width / 2 + 100;
    }
    function draw() {
      background(102);
      updateSpring();
      drawSpring();
    }
    function drawSpring() {
// Draw base
 
      fill(0.2);
      let baseWidth = 0.5 * ps + -8;
      rect(width / 2 - baseWidth, ps + springHeight, width / 2 + baseWidth, height);
// Set color and draw top bar
 
      if (over || move) {
        fill(255);
      } else {
        fill(204);
      }
      rect(left, ps, right, ps + springHeight);
    }
    function updateSpring() {
// Update the spring position
 
      if ( !move ) {
        f = -K * ( ps - R ); // f=-ky
        as = f / M;          // Set the acceleration, f=ma == a=f/m
        vs = D * (vs + as);  // Set the velocity
        ps = ps + vs;        // Updated position
      }
      if (abs(vs) < 0.1) {
        vs = 0.0;
      }
// Test if mouse if over the top bar

      if (mouseX > left && mouseX < right && mouseY > ps && mouseY < ps + springHeight) {
        over = true;
      } else {
        over = false;
      }
// Set and constrain the position of top bar

      if (move) {
        ps = mouseY - springHeight / 2;
        ps = constrain(ps, minHeight, maxHeight);
      }
    }
    function mousePressed() {
      if (over) {
        move = true;
      }
    }
    function mouseReleased() {
      move = false;
    }

### Soft Body

<img width="699" alt="Screen Shot 2023-08-22 at 2 21 07 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/3bb5fb55-9c1a-4503-9d71-7564a3f8b840">

**Original example by Ira Greenberg. 
Softbody dynamics simulation using curveVertex() and curveTightness().
**

// center point

    let centerX = 0.0, centerY = 0.0;
    let radius = 45, rotAngle = -90;
    let accelX = 0.0, accelY = 0.0;
    let deltaX = 0.0, deltaY = 0.0;
    let springing = 0.0009, damping = 0.98;
//corner nodes

    let nodes = 5;
//zero fill arrays

    let nodeStartX = [];
    let nodeStartY = [];
    let nodeX = [];
    let nodeY = [];
    let angle = [];
    let frequency = [];
// soft-body dynamics

    let organicConstant = 1.0;
    function setup() {
      createCanvas(710, 400);
//center shape in window

      centerX = width / 2;
      centerY = height / 2;
//initialize arrays to 0

      for (let i = 0; i < nodes; i++){
        nodeStartX[i] = 0;
        nodeStartY[i] = 0;
        nodeY[i] = 0;
        nodeY[i] = 0;
        angle[i] = 0;
      }
// iniitalize frequencies for corner nodes

      for (let i = 0; i < nodes; i++){
        frequency[i] = random(5, 12);
      }
      noStroke();
      frameRate(30);
    }
    function draw() {
//fade background
 
      fill(0, 100);
      rect(0, 0, width, height);
      drawShape();
      moveShape();
    }
    function drawShape() {
//  calculate node  starting locations

      for (let i = 0; i < nodes; i++){
        nodeStartX[i] = centerX + cos(radians(rotAngle)) * radius;
        nodeStartY[i] = centerY + sin(radians(rotAngle)) * radius;
        rotAngle += 360.0 / nodes;
      }
// draw polygon

      curveTightness(organicConstant);
      fill(255);
      beginShape();
      for (let i = 0; i < nodes; i++){
        curveVertex(nodeX[i], nodeY[i]);
      }
      for (let i = 0; i < nodes-1; i++){
        curveVertex(nodeX[i], nodeY[i]);
      }
      endShape(CLOSE);
    }
    function moveShape() {
//move center point
 
      deltaX = mouseX - centerX;
      deltaY = mouseY - centerY;
// create springing effect

      deltaX *= springing;
      deltaY *= springing;
      accelX += deltaX;
      accelY += deltaY;
// move predator's center

      centerX += accelX;
      centerY += accelY;
// slow down springing

      accelX *= damping;
      accelY *= damping;
// change curve tightness
 
      organicConstant = 1 - ((abs(accelX) + abs(accelY)) * 0.1);
//move nodes

      for (let i = 0; i < nodes; i++){
        nodeX[i] = nodeStartX[i] + sin(radians(angle[i])) * (accelX * 2);
        nodeY[i] = nodeStartY[i] + sin(radians(angle[i])) * (accelY * 2);
        angle[i] += frequency[i];
      }
    }

### Brownian Motion

<img width="702" alt="Screen Shot 2023-08-22 at 3 21 04 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/c98e3816-8115-4468-a982-94bb21eefa5c">

**Recording random movement as a continuous line. Port of original example from the Processing examples page.
**

    let num = 2000;
    let range = 6;
    let ax = [];
    let ay = [];
    function setup() {
      createCanvas(710, 400);
      for ( let i = 0; i < num; i++ ) {
        ax[i] = width / 2;
        ay[i] = height / 2;
      }
      frameRate(30);
    }
    function draw() {
      background(51);
// Shift all elements 1 place to the left
 
      for ( let i = 1; i < num; i++ ) {
        ax[i - 1] = ax[i];
        ay[i - 1] = ay[i];
      }
// Put a new value at the end of the array
 
      ax[num - 1] += random(-range, range);
      ay[num - 1] += random(-range, range);
// Constrain all points to the screen

      ax[num - 1] = constrain(ax[num - 1], 0, width);
      ay[num - 1] = constrain(ay[num - 1], 0, height);
// Draw a line connecting the points
 
      for ( let j = 1; j < num; j++ ) {
        let val = j / num * 204.0 + 51;
        stroke(val);
        line(ax[j - 1], ay[j - 1], ax[j], ay[j]);
      }
    }


### Snowflakes

<img width="392" alt="Screen Shot 2023-08-22 at 3 24 34 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/56d9bd1a-34cc-49cc-a366-ac5c261a4436">

**Particle system simulating the motion of falling snowflakes. Uses an array of objects to hold the snowflake particles. Contributed by Aatish Bhatia.
**

    let num = 2000;
    let range = 6;
    let ax = [];
    let ay = [];
    function setup() {
      createCanvas(710, 400);
      for ( let i = 0; i < num; i++ ) {
        ax[i] = width / 2;
        ay[i] = height / 2;
      }
      frameRate(30);
    }
    function draw() {
      background(51);
  // Shift all elements 1 place to the left
  
      for ( let i = 1; i < num; i++ ) {
        ax[i - 1] = ax[i];
        ay[i - 1] = ay[i];
      }
  // Put a new value at the end of the array

      ax[num - 1] += random(-range, range);
      ay[num - 1] += random(-range, range);
  // Constrain all points to the screen
  
      ax[num - 1] = constrain(ax[num - 1], 0, width);
      ay[num - 1] = constrain(ay[num - 1], 0, height);
  // Draw a line connecting the points
  
      for ( let j = 1; j < num; j++ ) {
        let val = j / num * 204.0 + 51;
        stroke(val);
        line(ax[j - 1], ay[j - 1], ax[j], ay[j]);
      }
    }


### Penrose Tiles

<img width="702" alt="Screen Shot 2023-08-22 at 3 28 34 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/6bb228df-b702-4357-8c1b-eab309f70f96">

**This is a port by David Blitz of the "Penrose Tile" example from processing.org/examples
**

    let ds;
    function setup() {
      createCanvas(710, 400);
      ds = new PenroseLSystem();
//please, play around with the following line🥚✨
 
      ds.simulate(5);
    }
    function draw() {
      background(0);
      ds.render();
    }
    function PenroseLSystem() {
        this.steps = 0;
//these are axiom and rules for the penrose rhombus l-system
//a reference would be cool, but I couldn't find a good one
  
        this.axiom = "[X]++[X]++[X]++[X]++[X]";
        this.ruleW = "YF++ZF----XF[-YF----WF]++";
        this.ruleX = "+YF--ZF[---WF--XF]+";
        this.ruleY = "-WF++XF[+++YF++ZF]-";
        this.ruleZ = "--YF++++WF[+ZF++++XF]--XF";

//please play around with the following two lines🥚✨
   
    this.startLength = 460.0;
    this.theta = TWO_PI / 10.0; //36 degrees, try TWO_PI / 6.0, ...
    this.reset();
    }
    PenroseLSystem.prototype.simulate = function (gen) {
      while (this.getAge() < gen) {
        this.iterate(this.production);
      }
    }
    PenroseLSystem.prototype.reset = function () {
        this.production = this.axiom;
        this.drawLength = this.startLength;
        this.generations = 0;
      }
    PenroseLSystem.prototype.getAge = function () {
        return this.generations;
      }
//apply substitution rules to create new iteration of production string

    PenroseLSystem.prototype.iterate = function() {
        let newProduction = "";
        for(let i=0; i < this.production.length; ++i) {
          let step = this.production.charAt(i);
//if current character is 'W', replace current character
//by corresponding rule

          if (step == 'W') {
            newProduction = newProduction + this.ruleW;
          }
          else if (step == 'X') {
            newProduction = newProduction + this.ruleX;
          }
          else if (step == 'Y') {
            newProduction = newProduction + this.ruleY;
          }
          else if (step == 'Z') {
            newProduction = newProduction + this.ruleZ;
          }
          else {
//drop all 'F' characters, don't touch other
//characters (i.e. '+', '-', '[', ']'
     
            if (step != 'F') {
              newProduction = newProduction + step;
            }
          }
        }
        this.drawLength = this.drawLength * 0.5;
        this.generations++;
        this.production = newProduction;
    }
//convert production string to a turtle graphic

    PenroseLSystem.prototype.render = function () {
        translate(width / 2, height / 2);
        this.steps += 20;
        if(this.steps > this.production.length) {
          this.steps = this.production.length;
        }
        for(let i=0; i<this.steps; ++i) {
          let step = this.production.charAt(i);
//'W', 'X', 'Y', 'Z' symbols don't actually correspond to a turtle action
     
          if( step == 'F') {
            stroke(255, 60);
            for(let j=0; j < this.repeats; j++) {
              line(0, 0, 0, -this.drawLength);
              noFill();
              translate(0, -this.drawLength);
            }
        this.repeats = 1;
          }
          else if (step == '+') {
            rotate(this.theta);
          }
          else if (step == '-') {
            rotate(-this.theta);
          }
          else if (step == '[') {
            push();
          }
          else if (step == ']') {
            pop();
          }
        }
      }
      
### Particles

<img width="713" alt="Screen Shot 2023-08-22 at 3 43 13 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/c6c6eb83-a3ed-466b-9cb4-3f8aa199e30c">

**There is a light-weight JavaScript library named particle.js which creates a very pleasing particle system. This is an attempt to recreate that particle system using p5.js. Inspired by Particle.js, contributed by Sagar Arora.
**

// this class describes the properties of a single particle.

    class Particle {
// setting the co-ordinates, radius and the
// speed of a particle in both the co-ordinates axes.
  
      constructor(){
        this.x = random(0,width);
        this.y = random(0,height);
        this.r = random(1,8);
        this.xSpeed = random(-2,2);
        this.ySpeed = random(-1,1.5);
      }
// creation of a particle.
 
      createParticle() {
        noStroke();
        fill('rgba(200,169,169,0.5)');
        circle(this.x,this.y,this.r);
      }
// setting the particle in motion.
  
      moveParticle() {
        if(this.x < 0 || this.x > width)
          this.xSpeed*=-1;
        if(this.y < 0 || this.y > height)
          this.ySpeed*=-1;
        this.x+=this.xSpeed;
        this.y+=this.ySpeed;
      }
// this function creates the connections(lines)
// between particles which are less than a certain distance apart

      joinParticles(particles) {
        particles.forEach(element =>{
          let dis = dist(this.x,this.y,element.x,element.y);
          if(dis<85) {
            stroke('rgba(255,255,255,0.04)');
            line(this.x,this.y,element.x,element.y);
          }
        });
      }
    }
// an array to add multiple particles

    let particles = [];
    function setup() {
      createCanvas(720, 400);
      for(let i = 0;i<width/10;i++){
        particles.push(new Particle());
      }
    }
    function draw() {
      background('#0f0f0f');
      for(let i = 0;i<particles.length;i++) {
        particles[i].createParticle();
        particles[i].moveParticle();
        particles[i].joinParticles(particles.slice(i));
      }
    }

## Interaction
### Tickle

<img width="702" alt="Screen Shot 2023-08-22 at 3 56 01 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/bc3e0878-2b1c-47cb-9f74-5be631f56c74">

**The word "tickle" jitters when the cursor hovers over. Sometimes, it can be tickled off the screen.
**

    let message = 'tickle',
      font,
      bounds, // holds x, y, w, h of the text's bounding box
      fontsize = 60,
      x,
      y; // x and y coordinates of the text
    function preload() {
      font = loadFont('assets/SourceSansPro-Regular.otf');
    }
    function setup() {
      createCanvas(710, 400);
// set up the font
 
      textFont(font);
      textSize(fontsize);
// get the width and height of the text so we can center it initially
 
      bounds = font.textBounds(message, 0, 0, fontsize);
      x = width / 2 - bounds.w / 2;
      y = height / 2 - bounds.h / 2;
    }
    function draw() {
      background(204, 120);
// write the text in black and get its bounding box
  
      fill(0);
      text(message, x, y);
      bounds = font.textBounds(message, x, y, fontsize);
// check if the mouse is inside the bounding box and tickle if so
 
      if (
        mouseX >= bounds.x &&
        mouseX <= bounds.x + bounds.w &&
        mouseY >= bounds.y &&
        mouseY <= bounds.y + bounds.h
      ) {
        x += random(-5, 5);
        y += random(-5, 5);
      }
    }

### Weight Line (automate maybe?)

<img width="399" alt="Screen Shot 2023-08-22 at 4 21 27 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/441546e7-a792-4ccf-aef1-6f8d45442228">

**
contributed by Prof WM Harris, using the random function with events to color/weight a line
How to use the random function with events to color/ weight a line dependent on mouse location, left mouse button clicks, character key types, and random key releases.
Functions are created for both the canvas set up as well as the creation of the line. Depending on the action taken by the user the line can vary in width and color. Left mouse button clicks result in a color change to blue, while the typing of any character key will change the color to turquoise, each resulting in a variable stroke weight; the width of the former will be between 0 – 1 while the width of the latter will be 0 – 5. The release of any key will result in a random hue, saturation, and brightness change to the line.
**

    function setup() {
        createCanvas(400, 400);
        background("beige");
        colorMode(HSB);
      }
      function draw() {
//Line from prev pt to current pt
//of mouse position
   
        line(mouseX, mouseY, pmouseX, pmouseY);
      }
//listen when we click the mouse
 
      function mouseClicked() {
//weights 0 to 1
  
        stroke("slateBlue");
        strokeWeight(random());
//what if want weights 0 to .4?
//strokeWeight( random(.4) );
  
       }
//listen when we release *any* key

      function keyReleased() {
//color hue values between 20 and 145
//saturation 0 to 100
//brightness 80 to 100
    
        stroke(random(20, 145), random(100), random(80, 100));
      }
//listen for only character keys
 
      function keyTyped() {
//weights 0 to 5
   
        stroke("turquoise");
        strokeWeight(random(5));
      }

### Wavemaker

<img width="605" alt="Screen Shot 2023-08-22 at 4 26 16 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/855ea0b6-d047-4a14-af06-88c0e32e7520">

**This illustrates how waves (like water waves) emerge from particles oscillating in place. Move your mouse to direct the wave. Contributed by Aatish Bhatia, inspired by Orbiters by Dave Whyte.
**

    let t = 0; // time variable
    function setup() {
      createCanvas(600, 600);
      noStroke();
      fill(40, 200, 40);
    }
    function draw() {
      background(10, 10); 
// translucent background (creates trails)
// make a x and y grid of ellipses
  
      for (let x = 0; x <= width; x = x + 30) {
        for (let y = 0; y <= height; y = y + 30) {
// starting point of each circle depends on mouse position
     
          const xAngle = map(mouseX, 0, width, -4 * PI, 4 * PI, true);
          const yAngle = map(mouseY, 0, height, -4 * PI, 4 * PI, true);
// and also varies based on the particle's location
     
          const angle = xAngle * (x / width) + yAngle * (y / height);
// each particle moves in a circle
    
          const myX = x + 20 * cos(2 * PI * t + angle);
          const myY = y + 20 * sin(2 * PI * t + angle);
          ellipse(myX, myY, 10); // draw particle
        }
      }
      t = t + 0.01; // update time
    }

### Reach 3

<img width="708" alt="Screen Shot 2023-08-22 at 4 36 18 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/4d5a7566-b857-4cdc-8414-c53207e73a06">

**The arm follows the position of the ball by calculating the angles with atan2(). Based on code from Keith Peters.
**

    let numSegments = 8,
      x = [],
      y = [],
      angle = [],
      segLength = 26,
      targetX,
      targetY,
      ballX = 50,
      ballY = 50,
      ballXDirection = 1,
      ballYDirection = -1;
    for (let i = 0; i < numSegments; i++) {
      x[i] = 0;
      y[i] = 0;
      angle[i] = 0;
    }
    function setup() {
      createCanvas(710, 400);
      strokeWeight(20);
      stroke(255, 100);
      noFill();
      x[x.length - 1] = width / 2; // Set base x-coordinate
      y[x.length - 1] = height; // Set base y-coordinate
    }
    function draw() {
      background(0);
      strokeWeight(20);
      ballX = ballX + 1.0 * ballXDirection;
      ballY = ballY + 0.8 * ballYDirection;
      if (ballX > width - 25 || ballX < 25) {
        ballXDirection *= -1;
      }
      if (ballY > height - 25 || ballY < 25) {
        ballYDirection *= -1;
      }
      ellipse(ballX, ballY, 30, 30);

      reachSegment(0, ballX, ballY);
      for (let i = 1; i < numSegments; i++) {
        reachSegment(i, targetX, targetY);
      }
      for (let j = x.length - 1; j >= 1; j--) {
        positionSegment(j, j - 1);
      }
      for (let k = 0; k < x.length; k++) {
        segment(x[k], y[k], angle[k], (k + 1) * 2);
      }
    }
    function positionSegment(a, b) {
      x[b] = x[a] + cos(angle[a]) * segLength;
      y[b] = y[a] + sin(angle[a]) * segLength;
    }
    function reachSegment(i, xin, yin) {
      const dx = xin - x[i];
      const dy = yin - y[i];
      angle[i] = atan2(dy, dx);
      targetX = xin - cos(angle[i]) * segLength;
      targetY = yin - sin(angle[i]) * segLength;
    }
    function segment(x, y, a, sw) {
      strokeWeight(sw);
      push();
      translate(x, y);
      rotate(a);
      line(0, 0, segLength, 0);
      pop();
    }

### Arduino sensor data via WebJack

**WebJack is a way to read data from an Arduino (and other sources) using audio -- it basically turns your Arduino into an audio modem. https://github.com/publiclab/webjack Note: WebJack and p5-webjack libraries must be added to your index.html as follows:
<script src="https://webjack.io/dist/webjack.js"></script>
<script src="https://jywarren.github.io/p5-webjack/lib.js"></script>
Working example: https://editor.p5js.org/jywarren/sketches/rkztwSt8M Testing audio: https://www.youtube.com/watch?v=GtJW1Dlt3cg Load this sketch onto an Arduino: https://create.arduino.cc/editor/jywarren/023158d8-be51-4c78-99ff-36c63126b554/preview Arduino will output audio from pin 3 + ground. Use microphone or an audio cable.
**

    function setup() { 
      createCanvas(400, 400);
      noStroke();
      fill('#ff00aa22');
      receiveSensorData(handleData);
    }
    function handleData(data, connection) {
      console.log(data); // output the values to log
  // data[0] is the 1st value, data[1] 2nd, etc.
  // draw stuff! Browse http://p5js.org/reference/
 
      background('#ddd');
      ellipse(100, 200, data[0]+10, data[0]+10);
  // connection.send('send data back to the Arduino if its listening');
 
    }
## Objects
### Objects

<img width="701" alt="Screen Shot 2023-08-22 at 4 46 03 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/5e3b94a0-19f1-4e32-ba5a-6108618fb790">

**Create a Jitter class, instantiate an object, and move it around the screen. Adapted from Getting Started with Processing by Casey Reas and Ben Fry.
**

    let bug; 
// Declare object

    function setup() {
      createCanvas(710, 400);
// Create object
 
      bug = new Jitter();
    }
    function draw() {
      background(50, 89, 100);
      bug.move();
      bug.display();
    }
// Jitter class

    class Jitter {
      constructor() {
        this.x = random(width);
        this.y = random(height);
        this.diameter = random(10, 30);
        this.speed = 1;
      }
      move() {
        this.x += random(-this.speed, this.speed);
        this.y += random(-this.speed, this.speed);
      }
      display() {
        ellipse(this.x, this.y, this.diameter, this.diameter);
      }
    }

### Multiple Objects

<img width="708" alt="Screen Shot 2023-08-22 at 4 51 35 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/63b11e0b-aafa-412d-8247-699649341bb1">

**Create a Jitter class, instantiate multiple objects, and move it around the screen.
**

    let bug1; 
    let bug2;
    let bug3;
    let bug4;
// Declare objects

    function setup() {
      createCanvas(710, 400);
// Create object

      bug1 = new Jitter();
      bug2 = new Jitter();
      bug3 = new Jitter();
      bug4 = new Jitter();
    }
    function draw() {
      background(50, 89, 100);
      bug1.move();
      bug1.display();
      bug2.move();
      bug2.display();
      bug3.move();
      bug3.display();
      bug4.move();
      bug4.display();
    }
// Jitter class

    class Jitter {
      constructor() {
        this.x = random(width);
        this.y = random(height);
        this.diameter = random(10, 30);
        this.speed = 1;
      }
      move() {
        this.x += random(-this.speed, this.speed);
        this.y += random(-this.speed, this.speed);
      }
      display() {
        ellipse(this.x, this.y, this.diameter, this.diameter);
      }
    }

### Array of Objects

<img width="707" alt="Screen Shot 2023-08-22 at 4 52 21 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/f0508ebb-b097-4fa8-a4b6-49991b2f1bdf">

**Create a Jitter class, instantiate an array of objects and move them around the screen.
**

    let bugs = []; 
// array of Jitter objects

    function setup() {
      createCanvas(710, 400);
// Create objects
 
      for (let i = 0; i < 50; i++) {
        bugs.push(new Jitter());
      }
    }
    function draw() {
      background(50, 89, 100);
      for (let i = 0; i < bugs.length; i++) {
        bugs[i].move();
        bugs[i].display();
      }
    }
// Jitter class

    class Jitter {
      constructor() {
        this.x = random(width);
        this.y = random(height);
        this.diameter = random(10, 30);
        this.speed = 1;
      }
      move() {
        this.x += random(-this.speed, this.speed);
        this.y += random(-this.speed, this.speed);
      }
      display() {
        ellipse(this.x, this.y, this.diameter, this.diameter);
      }
    }

### Objects 2

<img width="709" alt="Screen Shot 2023-08-22 at 4 55 02 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/c86e1f2f-d531-4849-b441-159780958a9c">

**Ported from example by hbarragan. Move the cursor across the image to change the speed and positions of the geometry. The class MRect defines a group of lines.
**


    let r1, r2, r3, r4;
    function setup() {
    createCanvas(710, 400);
    fill(255, 204);
    noStroke();
    r1 = new MRect(1, 134.0, 0.532, 0.1 * height, 10.0, 60.0);
    r2 = new MRect(2, 44.0, 0.166, 0.3 * height, 5.0, 50.0);
    r3 = new MRect(2, 58.0, 0.332, 0.4 * height, 10.0, 35.0);
    r4 = new MRect(1, 120.0, 0.0498, 0.9 * height, 15.0, 60.0);
    }
    function draw() {
    background(0);
    r1.display();
    r2.display();
    r3.display();
    r4.display();
    r1.move(mouseX - width / 2, mouseY + height * 0.1, 30);
    r2.move((mouseX + width * 0.05) % width, mouseY + height * 0.025, 20);
    r3.move(mouseX / 4, mouseY - height * 0.025, 40);
    r4.move(mouseX - width / 2, height - mouseY, 50);
    }
    class MRect {
        constructor(iw, ixp, ih, iyp, id, it) {
        this.w = iw; // single bar width
        this.xpos = ixp; // rect xposition
        this.h = ih; // rect height
        this.ypos = iyp; // rect yposition
        this.d = id; // single bar distance
        this.t = it; // number of bars
        }
        move(posX, posY, damping) {
            let dif = this.ypos - posY;
            if (abs(dif) > 1) {
                this.ypos -= dif / damping;
            }
            dif = this.xpos - posX;
            if (abs(dif) > 1) {
                this.xpos -= dif / damping;
            }
        }
        display() {
            for (let i = 0; i < this.t; i++) {
                rect(
                this.xpos + i * (this.d + this.w),
                this.ypos,
                this.w,
                height * this.h
                );
            }
        }
    }

### Inheritance

<img width="638" alt="Screen Shot 2023-08-22 at 4 59 05 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/92f2718f-8748-41c8-8e4f-c466dd668d1a">

**A class can be defined using another class as a foundation. In object-oriented programming terminology, one class can inherit fields and methods from another. An object that inherits from another is called a subclass, and the object it inherits from is called a superclass. A subclass extends the superclass.
**

    let spots, arm;
    function setup() {
    createCanvas(640, 360);
    arm = new SpinArm(width/2, height/2, 0.01);
    spots = new SpinSpots(width/2, height/2, -0.02, 90.0);
    }
    function draw() {
    background(204);
    arm.update();
    arm.display();
    spots.update();
    spots.display();
    }
    class Spin {
    constructor(x, y, s) {
        this.x = x;
        this.y = y;
        this.speed = s;
        this.angle = 0.0;
    }
    update() {
        this.angle += this.speed;
    }
    }
    class SpinArm extends Spin {
    constructor(x, y, s) {
        super(x, y, s)
    }
    display() {
        strokeWeight(1);
        stroke(0);
        push();
        translate(this.x, this.y);
        this.angle += this.speed;
        rotate(this.angle);
        line(0, 0, 165, 0);
        pop();
    }
    }
    class SpinSpots extends Spin {
    constructor(x, y, s, d) {
        super(x, y, s)
        this.dim = d;
    }
    display() {
        noStroke();
        push();
        translate(this.x, this.y);
        this.angle += this.speed;
        rotate(this.angle);
        ellipse(-this.dim/2, 0, this.dim, this.dim);
        ellipse(this.dim/2, 0, this.dim, this.dim);
        pop();
    }
    }

### Composite Objects

<img width="638" alt="Screen Shot 2023-08-22 at 5 06 51 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/a31717a1-2d62-4a9b-9acc-a43f46a88d2e">

**An object can include several other objects. Creating such composite objects is a good way to use the principles of modularity and build higher levels of abstraction within a program.
**

    let er1, er2;
    function setup() {
    createCanvas(640, 360);
    er1 = new EggRing(width * 0.45, height * 0.5, 0.1, 120);
    er2 = new EggRing(width * 0.65, height * 0.8, 0.05, 180);
    }
    function draw() {
    background(0);
    er1.transmit();
    er2.transmit();
    }
    class Egg {
    constructor(xpos, ypos, t, s) {
        this.x = xpos;
        this.y = ypos;
        this.tilt = t;
        this.scalar = s / 100.0;
        this.angle = 0.0;
    }
    wobble() {
        this.tilt = cos(this.angle) / 8;
        this.angle += 0.1;
    }
    display() {
        noStroke();
        fill(255);
        push();
        translate(this.x, this.y);
        rotate(this.tilt);
        scale(this.scalar);
        beginShape();
        vertex(0, -100);
        bezierVertex(25, -100, 40, -65, 40, -40);
        bezierVertex(40, -15, 25, 0, 0, 0);
        bezierVertex(-25, 0, -40, -15, -40, -40);
        bezierVertex(-40, -65, -25, -100, 0, -100);
        endShape();
        pop();
    }
    }
    class Ring {
    start(xpos, ypos) {
        this.x = xpos;
        this.y = ypos;
        this.on = true;
        this.diameter = 1;
    }
    grow() {
        if (this.on == true) {
            this.diameter += 0.5;
            if (this.diameter > width * 2) {
                this.diameter = 0.0;
            }
        }
        }
    display() {
        if (this.on == true) {
            noFill();
            strokeWeight(4);
            stroke(155, 153);
            ellipse(this.x, this.y, this.diameter, this.diameter);
        }
    }
    }
    class EggRing {
    constructor(x, y, t, sp) {
        this.x = x;
        this.y = y;
        this.t = t;
        this.sp = sp;
        this.circle = new Ring();
        this.ovoid = new Egg(this.x, this.y, this.t, this.sp);
        this.circle.start(this.x, this.y - this.sp/2);
    }
    transmit() {
        this.ovoid.wobble();
        this.ovoid.display();
        this.circle.grow();
        this.circle.display();
        if (circle.on == false) {
            circle.on = true;
        }
    }
    }

### Car Instances

<img width="193" alt="Screen Shot 2023-08-22 at 5 14 36 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/79f92f11-4128-4dc9-9ba2-fadfeed1a576">

**
contributed by Prof WM Harris, How to create three instances of Car Class and invoke class methods.
A function is created for the canvas setup, and 3 car instances are initialized with different colors and canvas positions. The speed of each car is set by passing value to the instance’s start method. A second function calls class methods to display and move the cars.
**

    class Car {
  /* Constructor expects parameters for
  fill color, x and y coordinates that
  will be used to initialize class properties.
  */
 
      constructor(cColor, x, y) {
        this.color = cColor;
        this.doors = 4;
        this.isConvertible = false;
        this.x = x;
        this.y = y;
        this.speed = 0;
      }
      start(speed) { // method expects parameter!
        this.speed = speed;
      }
      display() { // method!
        fill(this.color);
        rect(this.x, this.y, 20, 10);
      }
      move() { // method!
        this.x += this.speed;
// Wrap x around boundaries
       
        if (this.x < -20) {
          this.x = width;
        } else if (this.x > width) {
          this.x = -20;
        }
      }
    } 
//end class Car

    let rav4;
    let charger;
    let nova;
    function setup() {
      createCanvas(200, 400);
  /* Construct the 3 Cars */
  //constructor expects cColor, x, y
 
      rav4 = new Car("silver", 100, 300);
      charger = new Car("gold", 0, 200);  
      nova = new Car("blue", 200, 100); 
      nova.doors = 2; //update nova's doors property
      console.log("rav4", rav4);
      console.log("charger", charger);
      console.log("nova", nova);
  //call start methods of Car instances
  //the start method expects a number for speed

      rav4.start(2.3);
      charger.start(-4);
      nova.start(random(-1, 1));
    }
    function draw() {
      background("beige");
  //display and move all 3 Cars
  
      rav4.display();
      charger.display();
      nova.display();
      rav4.move();
      charger.move();
      nova.move();
    }

## Lights
### Directional

<img width="710" alt="Screen Shot 2023-08-22 at 5 20 21 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/07906f53-e758-4fa0-a770-95340ce06916">

**Move the mouse to change the direction of the light. Directional light comes from one direction and is stronger when hitting a surface squarely and weaker if it hits at a a gentle angle. After hitting a surface, a directional light scatters in all directions.
**

    const radius = 200;
    function setup() {
      createCanvas(710, 400, WEBGL);
      noStroke();
      fill(200);
    }
    function draw() {
      noStroke();
      background(0);
      const dirY = (mouseY / height - 0.5) * 4;
      const dirX = (mouseX / width - 0.5) * 4;
      directionalLight(204, 204, 204, dirX, dirY, 1);
      translate(-1.5 * radius, 0, 0);
      sphere(radius);
      translate(3 * radius, 0, 0);
      sphere(radius);
    }

### Mixture

<img width="706" alt="Screen Shot 2023-08-22 at 5 22 38 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/205b9c3b-7053-4d91-b915-bf75d1c0a8aa">

**Display a box with three different kinds of lights.
**

    function setup() {
      createCanvas(710, 400, WEBGL);
      noStroke();
    }
    function draw() {
      background(0);
  // ambient light
 
       ambientLight(0, 255/4, 0);
  // to set the light position,
  // think of the world's coordinate as:
  // -width/2,-height/2 -------- width/2,-height/2
  //                |            |
  //                |     0,0    |
  //                |            |
  // -width/2,height/2--------width/2,height/2
  // blue directional light from the left
 
      directionalLight(0, 0, 255, -1, 0, 0);
  // calculate distance from center to mouseX
 
      let lightX = mouseX - width / 2;
      let lightY = mouseY - height / 2;
  // red spotlight
  // axis located at lightX, lightY, 500
  // axis direction of light: 0, 0, -1
 
      spotLight(255, 0, 0, lightX, lightY, 500, 0, 0, -1);
  // rotate on X axis

      rotateX(-PI/4);
  // rotate on Y axis

      rotateY(PI/4);
  // place box on (0, 0, 0), size 100

      box(100);
    }

## Motion
### Non Orthogonal Reflection

<img width="705" alt="Screen Shot 2023-08-22 at 5 28 54 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/8ebf7ddb-ed4a-4ce6-9f09-7ccc49db25ea">

**This is a port by David Blitz of the "Reflection 1" example from processing.org/examples
**

//Position of left hand side of floor

    let base1;
//Position of right hand side of floor

    let base2;
//Length of floor
//let baseLength;
// Variables related to moving ball

    let position;
    let velocity;
    let r = 6;
    let speed = 3.5;
    function setup() {
      createCanvas(710, 400);
      fill(128);
      base1 = createVector(0, height - 150);
      base2 = createVector(width, height);
//createGround();
//start ellipse at middle top of screen

      position = createVector(width / 2, 0);
//calculate initial random velocity
  
      velocity = p5.Vector.random2D();
      velocity.mult(speed);
    }
    function draw() {
//draw background
 
      fill(0, 12);
      noStroke();
      rect(0, 0, width, height);
//draw base
 
      fill(200);
      quad(base1.x, base1.y, base2.x, base2.y, base2.x, height, 0, height);
//calculate base top normal
  
      let baseDelta = p5.Vector.sub(base2, base1);
      baseDelta.normalize();
      let normal = createVector(-baseDelta.y, baseDelta.x);
      let intercept = p5.Vector.dot(base1, normal);
//draw ellipse
 
      noStroke();
      fill(255);
      ellipse(position.x, position.y, r * 2, r * 2);
//move ellipse
  
      position.add(velocity);
//normalized incidence vector
 
      incidence = p5.Vector.mult(velocity, -1);
      incidence.normalize();
// detect and handle collision with base

      if (p5.Vector.dot(normal, position) > intercept) {
//calculate dot product of incident vector and base top
    
        let dot = incidence.dot(normal);
//calculate reflection vector
//assign reflection vector to direction vector
    
        velocity.set(
          2 * normal.x * dot - incidence.x,
          2 * normal.y * dot - incidence.y,
          0
        );
        velocity.mult(speed);
// draw base top normal at collision point
  
        stroke(255, 128, 0);
        line(
          position.x,
          position.y,
          position.x - normal.x * 100,
          position.y - normal.y * 100
        );
      }
//}
// detect boundary collision
// right
 
      if (position.x > width - r) {
        position.x = width - r;
        velocity.x *= -1;
      }
// left

      if (position.x < r) {
        position.x = r;
        velocity.x *= -1;
      }
// top
  
      if (position.y < r) {
        position.y = r;
        velocity.y *= -1;
//randomize base top
   
        base1.y = random(height - 100, height);
        base2.y = random(height - 100, height);
      }
    }

### Bounce

<img width="712" alt="Screen Shot 2023-08-23 at 11 14 07 AM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/5f1809fc-c9ec-4253-ad2c-d0a82f459a47">

**When the shape hits the edge of the window, it reverses its direction.
**

    let rad = 60; // Width of the shape
    let xpos, ypos; // Starting position of shape
    let xspeed = 2.8; // Speed of the shape
    let yspeed = 2.2; // Speed of the shape
    let xdirection = 1; // Left or Right
    let ydirection = 1; // Top to Bottom
    function setup() {
      createCanvas(720, 400);
      noStroke();
      frameRate(30);
      ellipseMode(RADIUS);
// Set the starting position of the shape
  
      xpos = width / 2;
      ypos = height / 2;
    }
    function draw() {
      background(102);
// Update the position of the shape
 
      xpos = xpos + xspeed * xdirection;
      ypos = ypos + yspeed * ydirection;
// Test to see if the shape exceeds the boundaries of the screen
// If it does, reverse its direction by multiplying by -1
  
      if (xpos > width - rad || xpos < rad) {
        xdirection *= -1;
      }
      if (ypos > height - rad || ypos < rad) {
        ydirection *= -1;
      }
// Draw the shape
    
      ellipse(xpos, ypos, rad, rad);
    }

### Bouncy Bubbles

<img width="710" alt="Screen Shot 2023-08-23 at 11 33 59 AM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/b984af83-8cab-46c5-9475-07998ac03d01">

**based on code from Keith Peters. Multiple-object collision..
**

    let numBalls = 13;
    let spring = 0.05;
    let gravity = 0.03;
    let friction = -0.9;
    let balls = [];
    function setup() {
      createCanvas(720, 400);
      for (let i = 0; i < numBalls; i++) {
        balls[i] = new Ball(
          random(width),
          random(height),
          random(30, 70),
          i,
          balls
        );
      }
      noStroke();
      fill(255, 204);
    }
    function draw() {
      background(0);
      balls.forEach(ball => {
        ball.collide();
        ball.move();
        ball.display();
      });
    }
    class Ball {
      constructor(xin, yin, din, idin, oin) {
        this.x = xin;
        this.y = yin;
        this.vx = 0;
        this.vy = 0;
        this.diameter = din;
        this.id = idin;
        this.others = oin;
      }
      collide() {
        for (let i = this.id + 1; i < numBalls; i++) {
// console.log(others[i]);
       
          let dx = this.others[i].x - this.x;
          let dy = this.others[i].y - this.y;
          let distance = sqrt(dx * dx + dy * dy);
          let minDist = this.others[i].diameter / 2 + this.diameter / 2;
//console.log(distance);
//console.log(minDist);
     
          if (distance < minDist) {
//console.log("2");
           
            let angle = atan2(dy, dx);
            let targetX = this.x + cos(angle) * minDist;
            let targetY = this.y + sin(angle) * minDist;
            let ax = (targetX - this.others[i].x) * spring;
            let ay = (targetY - this.others[i].y) * spring;
            this.vx -= ax;
            this.vy -= ay;
            this.others[i].vx += ax;
            this.others[i].vy += ay;
          }
        }
      }
      move() {
        this.vy += gravity;
        this.x += this.vx;
        this.y += this.vy;
        if (this.x + this.diameter / 2 > width) {
          this.x = width - this.diameter / 2;
          this.vx *= friction;
        } else if (this.x - this.diameter / 2 < 0) {
          this.x = this.diameter / 2;
          this.vx *= friction;
        }
        if (this.y + this.diameter / 2 > height) {
          this.y = height - this.diameter / 2;
          this.vy *= friction;
        } else if (this.y - this.diameter / 2 < 0) {
          this.y = this.diameter / 2;
          this.vy *= friction;
        }
      }
      display() {
        ellipse(this.x, this.y, this.diameter, this.diameter);
      }
    }

### Morph

<img width="719" alt="Screen Shot 2023-08-23 at 11 42 39 AM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/b16eb9e8-32a2-4a36-a609-be34c82d943a">

**Changing one shape into another by interpolating vertices from one to another.
**

// Two ArrayLists to store the vertices for two shapes
// This example assumes that each shape will have the same
// number of vertices, i.e. the size of each ArrayList will be the same

    let circle = [];
    let square = [];
// An ArrayList for a third set of vertices, the ones we will be drawing
// in the window

    let morph = [];
// This boolean variable will control if we are morphing to a circle or square

    let state = false;
    function setup() {
      createCanvas(720, 400);
// Create a circle using vectors pointing from center
 
      for (let angle = 0; angle < 360; angle += 9) {
// Note we are not starting from 0 in order to match the
// path of a circle.
   
        let v = p5.Vector.fromAngle(radians(angle - 135));
        v.mult(100);
        circle.push(v);
// Let's fill out morph ArrayList with blank PVectors while we are at it
   
    morph.push(createVector());
  }
// A square is a bunch of vertices along straight lines
// Top of square
 
      for (let x = -50; x < 50; x += 10) {
        square.push(createVector(x, -50));
      }
// Right side
 
      for (let y = -50; y < 50; y += 10) {
        square.push(createVector(50, y));
      }
// Bottom

      for (let x = 50; x > -50; x -= 10) {
        square.push(createVector(x, 50));
      }
// Left side
     
      for (let y = 50; y > -50; y -= 10) {
        square.push(createVector(-50, y));
      }
    }
    function draw() {
      background(51);
  // We will keep how far the vertices are from their target
 
      let totalDistance = 0;
// Look at each vertex
    
      for (let i = 0; i < circle.length; i++) {
        let v1;
// Are we lerping to the circle or square?
   
        if (state) {
          v1 = circle[i];
        } else {
          v1 = square[i];
        }
// Get the vertex we will draw
   
        let v2 = morph[i];
// Lerp to the target
    
        v2.lerp(v1, 0.1);
// Check how far we are from target
  
        totalDistance += p5.Vector.dist(v1, v2);
      }
// If all the vertices are close, switch shape
  
      if (totalDistance < 0.1) {
        state = !state;
      }
// Draw relative to center
 
      translate(width / 2, height / 2);
      strokeWeight(4);
// Draw a polygon that makes up all the vertices

      beginShape();
      noFill();
      stroke(255);
      morph.forEach(v => {
        vertex(v.x, v.y);
      });
      endShape(CLOSE);
    }

### Moving On Curves

<img width="710" alt="Screen Shot 2023-08-23 at 12 23 53 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/67e0611b-6318-49d1-85bb-c88b65ac8064">

**In this example, the circles moves along the curve y = x^4. Click the mouse to have it move to a new position.
**

    let beginX = 20.0; 
// Initial x-coordinate

    let beginY = 10.0; 
// Initial y-coordinate

    let endX = 570.0; 
// Final x-coordinate

    let endY = 320.0; 
// Final y-coordinate

    let distX; 
// X-axis distance to move

    let distY; 
// Y-axis distance to move

    let exponent = 4; 
// Determines the curve

    let x = 0.0; 
// Current x-coordinate

    let y = 0.0; 
// Current y-coordinate

    let step = 0.01; 
// Size of each step along the path

    let pct = 0.0; 
// Percentage traveled (0.0 to 1.0)

    function setup() {
      createCanvas(720, 400);
      noStroke();
      distX = endX - beginX;
      distY = endY - beginY;
    }
    function draw() {
      fill(0, 2);
      rect(0, 0, width, height);
      pct += step;
      if (pct < 1.0) {
        x = beginX + pct * distX;
        y = beginY + pow(pct, exponent) * distY;
      }
      fill(255);
      ellipse(x, y, 20, 20);
    }
    function mousePressed() {
      pct = 0.0;
      beginX = x;
      beginY = y;
      endX = mouseX;
      endY = mouseY;
      distX = endX - beginX;
      distY = endY - beginY;
    }


### Circle Collision

<img width="703" alt="Screen Shot 2023-08-23 at 12 28 49 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/bac36a84-a42e-4e41-9bd2-0aae0189f23c">

**This is a port of the "Circle Collision" example from processing.org/examples 
This example uses vectors for better visualization of physical Quantity**

    class Ball {
      constructor(x, y, r) {
        this.position = new p5.Vector(x, y);
        this.velocity = p5.Vector.random2D();
        this.velocity.mult(3);
        this.r = r;
        this.m = r * 0.1;
      }
      update() {
        this.position.add(this.velocity);
      }
      checkBoundaryCollision() {
        if (this.position.x > width - this.r) {
          this.position.x = width - this.r;
          this.velocity.x *= -1;
        } else if (this.position.x < this.r) {
          this.position.x = this.r;
          this.velocity.x *= -1;
        } else if (this.position.y > height - this.r) {
          this.position.y = height - this.r;
          this.velocity.y *= -1;
        } else if (this.position.y < this.r) {
          this.position.y = this.r;
          this.velocity.y *= -1;
        }
      }
      checkCollision(other) {
// Get distances between the balls components
    
        let distanceVect = p5.Vector.sub(other.position, this.position);
// Calculate magnitude of the vector separating the balls
    
        let distanceVectMag = distanceVect.mag();
// Minimum distance before they are touching
    
        let minDistance = this.r + other.r;
        if (distanceVectMag < minDistance) {
          let distanceCorrection = (minDistance - distanceVectMag) / 2.0;
          let d = distanceVect.copy();
          let correctionVector = d.normalize().mult(distanceCorrection);
          other.position.add(correctionVector);
          this.position.sub(correctionVector);
// get angle of distanceVect
   
          let theta = distanceVect.heading();
// precalculate trig values
     
          let sine = sin(theta);
          let cosine = cos(theta);
          /* bTemp will hold rotated ball this.positions. You 
           just need to worry about bTemp[1] this.position*/
          let bTemp = [new p5.Vector(), new p5.Vector()];

          /* this ball's this.position is relative to the other
           so you can use the vector between them (bVect) as the 
           reference point in the rotation expressions.
           bTemp[0].this.position.x and bTemp[0].this.position.y will initialize
           automatically to 0.0, which is what you want
           since b[1] will rotate around b[0] */
          bTemp[1].x = cosine * distanceVect.x + sine * distanceVect.y;
          bTemp[1].y = cosine * distanceVect.y - sine * distanceVect.x;
// rotate Temporary velocities
     
          let vTemp = [new p5.Vector(), new p5.Vector()];

          vTemp[0].x = cosine * this.velocity.x + sine * this.velocity.y;
          vTemp[0].y = cosine * this.velocity.y - sine * this.velocity.x;
          vTemp[1].x = cosine * other.velocity.x + sine * other.velocity.y;
          vTemp[1].y = cosine * other.velocity.y - sine * other.velocity.x;

          /* Now that velocities are rotated, you can use 1D
           conservation of momentum equations to calculate 
           the final this.velocity along the x-axis. */
          let vFinal = [new p5.Vector(), new p5.Vector()];

// final rotated this.velocity for b[0]
  
          vFinal[0].x =
            ((this.m - other.m) * vTemp[0].x + 2 * other.m * vTemp[1].x) /
            (this.m + other.m);
          vFinal[0].y = vTemp[0].y;
// final rotated this.velocity for b[0]
     
          vFinal[1].x =
            ((other.m - this.m) * vTemp[1].x + 2 * this.m * vTemp[0].x) /
            (this.m + other.m);
          vFinal[1].y = vTemp[1].y;
// hack to avoid clumping
     
          bTemp[0].x += vFinal[0].x;
          bTemp[1].x += vFinal[1].x;

          /* Rotate ball this.positions and velocities back
           Reverse signs in trig expressions to rotate 
           in the opposite direction */
// rotate balls
     
          let bFinal = [new p5.Vector(), new p5.Vector()];

          bFinal[0].x = cosine * bTemp[0].x - sine * bTemp[0].y;
          bFinal[0].y = cosine * bTemp[0].y + sine * bTemp[0].x;
          bFinal[1].x = cosine * bTemp[1].x - sine * bTemp[1].y;
          bFinal[1].y = cosine * bTemp[1].y + sine * bTemp[1].x;
// update balls to screen this.position
     
          other.position.x = this.position.x + bFinal[1].x;
          other.position.y = this.position.y + bFinal[1].y;

          this.position.add(bFinal[0]);
// update velocities

          this.velocity.x = cosine * vFinal[0].x - sine * vFinal[0].y;
          this.velocity.y = cosine * vFinal[0].y + sine * vFinal[0].x;
          other.velocity.x = cosine * vFinal[1].x - sine * vFinal[1].y;
          other.velocity.y = cosine * vFinal[1].y + sine * vFinal[1].x;
        }
      }
      display() {
        noStroke();
        fill(204);
        ellipse(this.position.x, this.position.y, this.r * 2, this.r * 2);
      }
    }
    let balls = [new Ball(100, 400, 20), new Ball(700, 400, 80)];
    console.log(balls);
    function setup() {
      createCanvas(710, 400);
    }
    function draw() {
      background(51);
      for (let i = 0; i < balls.length; i++) {
        let b = balls[i];
        b.update();
        b.display();
        b.checkBoundaryCollision();
        balls[0].checkCollision(balls[1]);
      }
    }


## DOM

**Input text and click the button to see it affect the the canvas.**

    let input, button, greeting;

    function setup() {
      // create canvas
      createCanvas(710, 400);

      input = createInput();
      input.position(20, 65);

      button = createButton('submit');
      button.position(input.x + input.width, 65);
      button.mousePressed(greet);

      greeting = createElement('h2', 'what is your name?');
      greeting.position(20, 5);

      textAlign(CENTER);
      textSize(50);
    }

    function greet() {
      const name = input.value();
      greeting.html('hello ' + name + '!');
      input.value('');

      for (let i = 0; i < 200; i++) {
        push();
        fill(random(255), 255, 255);
        translate(random(width), random(height));
        rotate(random(2 * PI));
        text(name, 0, 0);
        pop();
      }
    }

### Slider 

![IMG_5893](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/807707ec-a0a8-4734-9ad0-953db655ab5e)

**Move the sliders to control the R, G, B values of the background.**

    let rSlider, gSlider, bSlider;
    function setup() {
// create canvas

    createCanvas(710, 400);
    textSize(15);
    noStroke();
// create sliders
    
    rSlider = createSlider(0, 255, 100);
    rSlider.position(20, 20);
    gSlider = createSlider(0, 255, 0);
    gSlider.position(20, 50);
    bSlider = createSlider(0, 255, 255);
    bSlider.position(20, 80);
    }

    function draw() {
    const r = rSlider.value();
    const g = gSlider.value();
    const b = bSlider.value();
    background(r, g, b);
    text('red', rSlider.x * 2 + rSlider.width, 35)
    text('green', gSlider.x * 2 + gSlider.width, 65);
    text('blue', bSlider.x * 2 + bSlider.width, 95);
    }   

### Modifying the DOM

![IMG_5895](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/0f53daa8-05b2-4eaa-9183-abd1051be3b6)

**Create DOM elements and modify their properties every time draw() is called.**

    let dancingWords = [];
    class DanceSpan {
      constructor(element, x, y) {
        element.position(x, y);
        this.element = element;
        this.x = x;
        this.y = y;
      }
      brownian() {
        this.x += random(-6, 6);
        this.y += random(-6, 6);
        this.element.position(this.x, this.y);
      }
    }
    function setup() {
// This paragraph is created aside of the main block of code.
// It's to differentiate the creation of an element from its
// selection. Selected elements don't need to be created by
// p5js, they can be just plain HTML.

      createP(
        'I learn in this Letter, that Don Peter of Aragon, ' +
          ' comes this night to Messina'
      ).addClass('text').hide();
  // This line grabs the paragraph just created, but it would
  // also grab any other elements with class 'text' in the HTML
  // page.
  
      const texts = selectAll('.text');
      for (let i = 0; i < texts.length; i++) {
        const paragraph = texts[i].html();
        const words = paragraph.split(' ');
        for (let j = 0; j < words.length; j++) {
          const spannedWord = createSpan(words[j]);
          const dw = new DanceSpan(spannedWord, random(600), random(200));
          dancingWords.push(dw);
        }
      }
    }
    function draw() {
      for (let i = 0; i < dancingWords.length; i++) {
        dancingWords[i].brownian();
      }
    }

### Video

**Load a video with multiple formats and toggle between playing and paused with a button press.**

    let playing = false;
    let fingers;
    let button;
    function setup() {
      noCanvas();
// specify multiple formats for different browsers

      fingers = createVideo(['assets/fingers.mov', 'assets/fingers.webm']);
      button = createButton('play');
      button.mousePressed(toggleVid); // attach button listener
    }
// plays or pauses the video depending on current state

    function toggleVid() {
      if (playing) {
        fingers.pause();
        button.html('play');
      } else {
        fingers.loop();
        button.html('pause');
      }
      playing = !playing;
    }

### Video Canvas

![IMG_5896](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/8bdf6158-61de-452d-8c2b-a6d5d05fab05)

**Load a video with multiple formats and draw it to the canvas. To run this example locally, you will need a running local server.**

    let fingers;
    function setup() {
      createCanvas(710, 400);
  // specify multiple formats for different browsers
  
      fingers = createVideo(['assets/fingers.mov', 'assets/fingers.webm']);
      fingers.hide(); 
  // by default video shows up in separate dom
  // element. hide it and draw it to the canvas
  // instead
  
    }
    function draw() {
      background(150);
      image(fingers, 10, 10); // draw the video frame to canvas
      filter(GRAY);
      image(fingers, 150, 150); // draw a second copy to canvas
    }
    function mousePressed() {
      fingers.loop(); // set the video to loop and start playing
    }

### Video Pixels

![IMG_5898](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/8559ec5f-12d6-4d47-abee-e924ea5ba8c3)

**Load a video, manipulate its pixels and draw to canvas. To run this example locally, you will need a running local server.**

    let fingers;
    function setup() {
      createCanvas(320, 240);
// specify multiple formats for different browsers
  
      fingers = createVideo(['assets/fingers.mov', 'assets/fingers.webm']);
      fingers.loop();
      fingers.hide();
      noStroke();
      fill(0);
    }
    function draw() {
      background(255);
      fingers.loadPixels();
      const stepSize = round(constrain(mouseX / 8, 6, 32));
      for (let y = 0; y < height; y += stepSize) {
        for (let x = 0; x < width; x += stepSize) {
          const i = y * width + x;
          const darkness = (255 - fingers.pixels[i * 4]) / 255;
          const radius = stepSize * darkness;
          ellipse(x, y, radius, radius);
        }
      }
    }

### Video Capture

**Capture video from the webcam and display on the canvas as well with invert filter. Note that by default the capture feed shows up, too. You can hide the feed by uncommenting the capture.hide() line.**

    let capture;
    function setup() {
      createCanvas(390, 240);
      capture = createCapture(VIDEO);
      capture.size(320, 240);
//capture.hide();

    }
    function draw() {
      background(255);
      image(capture, 0, 0, 320, 240);
      filter(INVERT);
    }
### Drop

**Drag an image file onto the canvas to see it displayed.**

    function setup() {
  // create canvas
  
      const c = createCanvas(710, 400);
      background(100);
  // Add an event for when a file is dropped onto the canvas
  
      c.drop(gotFile);
    }
    function draw() {
      fill(255);
      noStroke();
      textSize(24);
      textAlign(CENTER);
      text('Drag an image file onto the canvas.', width / 2, height / 2);
      noLoop();
    }
    function gotFile(file) {
// If it's an image file
  
    if (file.type === 'image') {
// Create an image DOM element but don't show it
    
    const img = createImg(file.data).hide();
// Draw the image onto the canvas

    image(img, 0, 0, width, height);
    } else {
    console.log('Not an image file!');
      }
    }

## Drawing
### Continous Lines

**Click and drag the mouse to draw a line.**

    function setup() {
      createCanvas(710, 400);
      background(102);
    }
    function draw() {
      stroke(255);
      if (mouseIsPressed === true) {
        line(mouseX, mouseY, pmouseX, pmouseY);
      }
    }

### Patterns

![IMG_5903](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/8cc379f5-e701-4a9d-be0c-e8f901672e21)

**Move the cursor over the image to draw with a software tool which responds to the speed of the mouse.**

    function setup() {
      createCanvas(710, 400);
      background(102);
    }
    function draw() {
// Call the variableEllipse() method and send it the
// parameters for the current mouse position
// and the previous mouse position

      variableEllipse(mouseX, mouseY, pmouseX, pmouseY);
    }
// The simple method variableEllipse() was created specifically
// for this program. It calculates the speed of the mouse
// and draws a small ellipse if the mouse is moving slowly
// and draws a large ellipse if the mouse is moving quickly

    function variableEllipse(x, y, px, py) {
      let speed = abs(x - px) + abs(y - py);
      stroke(speed);
      ellipse(x, y, speed, speed);
    }

### Pulses

![IMG_5904](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/672a1f3f-db49-40f8-b0a5-28aa65beacf4)

**Software drawing instruments can follow a rhythm or abide by rules independent of drawn gestures. This is a form of collaborative drawing in which the draftsperson controls some aspects of the image and the software controls others.**

    let angle = 0;
    function setup() {
      createCanvas(710, 400);
      background(102);
      noStroke();
      fill(0, 102);
    }
    function draw() {
// Draw only when mouse is pressed

      if (mouseIsPressed === true) {
        angle += 5;    
        let val = cos(radians(angle)) * 12.0;
        for (let a = 0; a < 360; a += 75) {
          let xoff = cos(radians(a)) * val;
          let yoff = sin(radians(a)) * val;
          fill(0);
          ellipse(mouseX + xoff, mouseY + yoff, val, val);
        }
        fill(255);
        ellipse(mouseX, mouseY, 2, 2);
      }
    }

## Transform

### Translate

![IMG_5905](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/9278cf8d-3957-4a30-a275-26ebe0da68c5)

**The translate() function allows objects to be moved to any location within the window. The first parameter sets the x-axis offset and the second parameter sets the y-axis offset. This example shows how transforms accumulate.**


    let x = 0;
    let y = 0;
    let dim = 80.0;
    function setup() {
      createCanvas(720, 400);
      noStroke();
    }
    function draw() {
      background(102);
// Animate by increasing our x value

      x = x + 0.8;
// If the shape goes off the canvas, reset the position

      if (x > width + dim) {
        x = -dim;
      }
// Even though our rect command draws the shape with its
// center at the origin, translate moves it to the new
// x and y position

      translate(x, height / 2 - dim / 2);
      fill(255);
      rect(-dim / 2, -dim / 2, dim, dim);
// Transforms accumulate. Notice how this rect moves
// twice as fast as the other, but it has the same
// parameter for the x-axis value

      translate(x, dim);
      fill(0);
      rect(-dim / 2, -dim / 2, dim, dim);
    }

### Scale

![IMG_5907](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/12cb2bb3-13a1-47b2-8cd1-9344d3820cb0)

**Paramenters for the scale() function are values specified as decimal percentages. For example, the method call scale(2.0) will increase the dimension of the shape by 200 percent. Objects always scale from the origin. This example shows how transforms accumulate and also how scale and translate interact depending on their order.**

    let a = 0.0;
    let s = 0.0;
    function setup() {
      createCanvas(720, 400);
      noStroke();
//Draw all rectangles from their center as opposed to
// the default upper left corner

      rectMode(CENTER);
    }
    function draw() {
      background(102);
//Slowly increase 'a' and then animate 's' with
//a smooth cyclical motion by finding the cosine of 'a'

      a = a + 0.04;
      s = cos(a) * 2;
//Translate our rectangle from the origin to the middle of
//the canvas, then scale it with 's'

      translate(width / 2, height / 2);
      scale(s);
      fill(51);
      rect(0, 0, 50, 50);
//Translate and scale are accumulating, so this translate
//moves the second rectangle further right than the first
//and the scale is getting doubled. Note that cosine is
//making 's' both negative and positive, thus it cycles
//from left to right.

      translate(75, 0);
      fill(255);
      scale(s);
      rect(0, 0, 50, 50);
    }


### Rotate

![IMG_5908](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/04406085-7fe4-47ab-83e5-8ce73b30f23b)

**Rotating a square around the Z axis. To get the results you expect, send the rotate function angle parameters that are values between 0 and PI*2 (TWO_PI which is roughly 6.28). If you prefer to think about angles as degrees (0-360), you can use the radians() method to convert your values. For example: rotate(radians(90)) is identical to the statement rotate(PI/2). In this example, every even numbered second a jitter is added to the rotation. During odd seconds, rotation moves CW and CCW at the speed determined by the last jitter value.**

    let angle = 0.0;
    let jitter = 0.0;
    function setup() {
      createCanvas(720, 400);
      noStroke();
      fill(255);
//Draw the rectangle from the center and it will also be the
//rotate around that center

      rectMode(CENTER);
    }
    function draw() {
      background(51);
// during even-numbered seconds (0, 2, 4, 6...) add jitter to
// the rotation

      if (second() % 2 === 0) {
        jitter = random(-0.1, 0.1);
      }
//increase the angle value using the most recent jitter value

      angle = angle + jitter;
//use cosine to get a smooth CW and CCW motion when not jittering

      let c = cos(angle);
//move the shape to the center of the canvas

      translate(width / 2, height / 2);
//apply the final rotation

      rotate(c);
      rect(0, 0, 180, 180);
    }
### Arm

![IMG_5909](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/948dfea2-4a59-4005-be0d-d51027e2c750)

**This example uses transform matrices to create an arm. The angle of each segment is controlled with the mouseX and mouseY position. The transformations applied to the first segment are also applied to the second segment because they are inside the same push() and pop() matrix group.**

    let x, y;
    let angle1 = 0.0;
    let angle2 = 0.0;
    let segLength = 100;
    function setup() {
      createCanvas(720, 400);
      strokeWeight(30);
//Stroke with a semi-transparent white
  
      stroke(255, 160);
//Position the "shoulder" of the arm in the center of the canvas
  
      x = width * 0.5;
      y = height * 0.5;
    }
    function draw() {
      background(0);
//Change the angle of the segments according to the mouse positions
  
      angle1 = (mouseX / float(width) - 0.5) * -TWO_PI;
      angle2 = (mouseY / float(height) - 0.5) * PI;
//use push and pop to "contain" the transforms. Note that
// even though we draw the segments using a custom function,
// the transforms still accumulate
  
      push();
      segment(x, y, angle1);
      segment(segLength, 0, angle2);
      pop();
    }
//a custom function for drawing segments

    function segment(x, y, a) {
      translate(x, y);
      rotate(a);
      line(0, 0, segLength, 0);
    }


## Typography

### Letters

![IMG_5910](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/b69772eb-ba5b-431f-924e-c6eef0c26bab)

**Letters can be drawn to the screen by loading a font, setting its characteristics and then drawing the letters. This example uses a for loop and unicode reference numbers to automatically fill the canvas with characters in a grid. Vowels are selected and given a specific fill color.**

    let font,
      fontsize = 32;
    function preload() {
// Ensure the .ttf or .otf font stored in the assets directory
// is loaded before setup() and draw() are called
  
      font = loadFont('assets/SourceSansPro-Regular.otf');
    }
    function setup() {
      createCanvas(710, 400);
  // Set text characteristics
  
      textFont(font);
      textSize(fontsize);
      textAlign(CENTER, CENTER);
    }
    function draw() {
      background(160);
// Set the gap between letters and the left and top margin
  
      let gap = 52;
      let margin = 10;
      translate(margin * 4, margin * 4);
// Set the counter to start at the character you want
// in this case 35, which is the # symbol
  
      let counter = 35;
// Loop as long as there is space on the canvas
  
      for (let y = 0; y < height - gap; y += gap) {
        for (let x = 0; x < width - gap; x += gap) {
// Use the counter to retrieve individual letters by their Unicode number

          let letter = char(counter);
// Add different color to the vowels and other characters

          if (
            letter === 'A' ||
            letter === 'E' ||
            letter === 'I' ||
            letter === 'O' ||
            letter === 'U'
          ) {
            fill('#ed225d');
          } else {
            fill(255);
          }
// Draw the letter to the screen

          text(letter, x, y);
// Increment the counter

          counter++;
        }
      }
    }

### Words

![IMG_5911](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/f677d2d7-cb9e-43d7-bf08-ee880380aa12)

**The text() function is used for writing words to the screen. The words can be aligned left, center, or right with the textAlign() function, and like with shapes, words can be colored with fill().**

    let font,
      fontsize = 40;
    function preload() {
  // Ensure the .ttf or .otf font stored in the assets directory
  // is loaded before setup() and draw() are called
  
      font = loadFont('assets/SourceSansPro-Regular.otf');
    }
    function setup() {
      createCanvas(710, 400);
  // Set text characteristics
  
      textFont(font);
      textSize(fontsize);
      textAlign(CENTER, CENTER);
    }
    function draw() {
      background(160);
  // Align the text to the right
  // and run drawWords() in the left third of the canvas
  
      textAlign(RIGHT);
      drawWords(width * 0.25);
  // Align the text in the center
  // and run drawWords() in the middle of the canvas
  
      textAlign(CENTER);
      drawWords(width * 0.5);
  // Align the text to the left
  // and run drawWords() in the right third of the canvas
  
      textAlign(LEFT);
      drawWords(width * 0.75);
    }
    function drawWords(x) {
  // The text() function needs three parameters:
  // the text to draw, the horizontal position,
  // and the vertical position
  
      fill(0);
      text('ichi', x, 80);
      fill(65);
      text('ni', x, 150);
      fill(190);
      text('san', x, 220);
      fill(255);
      text('shi', x, 290);
    }

### Text Rotation

![IMG_5912](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/8da83fcc-15f8-4836-abfc-6d9f6e7502bb)

**Draws letters to the screen and rotates them at different angles.
This example is ported from the Text Rotation example on the Processing website**


    let font,
      fontsize = 32;
    let angleRotate = 0.0;
    function setup() {
      createCanvas(710, 400);
      background(0);
// Ensure the .ttf or .otf font stored in the assets directory
// is loaded before setup() and draw() are called
  
      font = loadFont('assets/SourceSansPro-Regular.otf');
// Set text characteristics
  
      textFont(font);
    } 
    function draw() {
      background(0);
      strokeWeight(1);
      stroke(153);
      push();
      let angle1 = radians(45);
      translate(100, 180);
      rotate(angle1);
// Draw the letter to the screen

      text("45 DEGREES", 0, 0);
      line(0, 0, 150, 0);
      pop();
      push();
      let angle2 = radians(270);
      translate(200, 180);
      rotate(angle2);
// Draw the letter to the screen

      text("270 DEGREES", 0, 0);
      line(0, 0, 150, 0);
      pop();
      push();
      translate(440, 180);
      rotate(radians(angleRotate));
      text(int(angleRotate) % 360 + " DEGREES ", 0, 0);
      line(0, 0, 150, 0);
      pop();
      angleRotate += 0.25;
      stroke(255, 0, 0);
      strokeWeight(4);
      point(100, 180);
      point(200, 180);
      point(440, 180);
    }


## 3D

### Geometries

![IMG_5913](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/b307853f-ff49-4f54-8437-4590777e9a11)

**There are six 3D primitives in p5 now.**

    function setup() {
      createCanvas(710, 400, WEBGL);
    }
    function draw() {
      background(250);
      translate(-240, -100, 0);
      normalMaterial();
      push();
      rotateZ(frameCount * 0.01);
      rotateX(frameCount * 0.01);
      rotateY(frameCount * 0.01);
      plane(70);
      pop();
      translate(240, 0, 0);
      push();
      rotateZ(frameCount * 0.01);
      rotateX(frameCount * 0.01);
      rotateY(frameCount * 0.01);
      box(70, 70, 70);
      pop();
      translate(240, 0, 0);
      push();
      rotateZ(frameCount * 0.01);
      rotateX(frameCount * 0.01);
      rotateY(frameCount * 0.01);
      cylinder(70, 70);
      pop();
      translate(-240 * 2, 200, 0);
      push();
      rotateZ(frameCount * 0.01);
      rotateX(frameCount * 0.01);
      rotateY(frameCount * 0.01);
      cone(70, 70);
      pop();
      translate(240, 0, 0);
      push();
      rotateZ(frameCount * 0.01);
      rotateX(frameCount * 0.01);
      rotateY(frameCount * 0.01);
      torus(70, 20);
      pop();
      translate(240, 0, 0);
      push();
      rotateZ(frameCount * 0.01);
      rotateX(frameCount * 0.01);
      rotateY(frameCount * 0.01);
      sphere(70);
      pop();
    }

### Sine Cosine in 3D

![IMG_5919](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/26c7a2a7-0b21-46e5-a7e9-07fcc6cb96eb)

**Sine, cosine and push / pop could be applied in 3D as well.**

    function setup() {
      createCanvas(710, 400, WEBGL);
    }
    function draw() {
      background(250);
      rotateY(frameCount * 0.01);
      for (let j = 0; j < 5; j++) {
        push();
        for (let i = 0; i < 80; i++) {
          translate(
            sin(frameCount * 0.001 + j) * 100,
            sin(frameCount * 0.001 + j) * 100,
            i * 0.1
          );
          rotateZ(frameCount * 0.002);
          push();
          sphere(8, 6, 4);
          pop();
        }
        pop();
      }
    }


### Multiple Lights

![IMG_5923](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/c835b319-a3f2-4b3a-b6ed-6f18cc9bcb69)

**All types of lights could be used in one sketch.**

    function setup() {
      createCanvas(710, 400, WEBGL);
    }
    function draw() {
      background(0);
      let locX = mouseX - height / 2;
      let locY = mouseY - width / 2;
      ambientLight(50);
      directionalLight(255, 0, 0, 0.25, 0.25, 0);
      pointLight(0, 0, 255, locX, locY, 250);
      push();
      translate(-width / 4, 0, 0);
      rotateZ(frameCount * 0.02);
      rotateX(frameCount * 0.02);
      specularMaterial(250);
      box(100, 100, 100);
      pop();
      translate(width / 4, 0, 0);
      ambientMaterial(250);
      sphere(120, 64);
    }


### Materials

![IMG_5926](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/c0e74317-e3c6-431f-924f-ee6413cdb87d)


**There are five types of materials supported. They respond to light differently. Move your mouse to change the light position.**

    let img;
    function setup() {
      createCanvas(710, 400, WEBGL);
      img = loadImage('assets/cat.jpg');
    }
    function draw() {
      background(0);
      let locX = mouseX - height / 2;
      let locY = mouseY - width / 2;
      ambientLight(60, 60, 60);
      pointLight(255, 255, 255, locX, locY, 100);
      push();
      rotateZ(frameCount * 0.01);
      rotateX(frameCount * 0.01);
      rotateY(frameCount * 0.01);
      texture(img);
      box(80);
      pop();
      push();
      translate(-width / 4, -height / 4, 0);
      rotateZ(frameCount * 0.01);
      rotateX(frameCount * 0.01);
      rotateY(frameCount * 0.01);
      fill(250, 0, 0);
      torus(80, 20, 64, 64);
      pop();
      push();
      translate(width / 4, -height / 4, 0);
      rotateZ(frameCount * 0.01);
      rotateX(frameCount * 0.01);
      rotateY(frameCount * 0.01);
      normalMaterial();
      torus(80, 20, 64, 64);
      pop();
      push();
      translate(-width / 4, height / 4, 0);
      rotateZ(frameCount * 0.01);
      rotateX(frameCount * 0.01);
      rotateY(frameCount * 0.01);
      ambientMaterial(250);
      torus(80, 20, 64, 64);
      pop();
      push();
      translate(width / 4, height / 4, 0);
      rotateZ(frameCount * 0.01);
      rotateX(frameCount * 0.01);
      rotateY(frameCount * 0.01);
      specularMaterial(250);
      torus(80, 20, 64, 64);
      pop();
    }

### Textures

![IMG_5927](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/e839a8c6-f237-43c4-8c24-1cf2805a45cf)

**Images and videos are supported for texture.**

// video source: https://vimeo.com/90312869

    let img;
    let vid;
    let theta = 0;
    function setup() {
      createCanvas(710, 400, WEBGL);
      img = loadImage('assets/cat.jpg');
      vid = createVideo(['assets/360video_256crop_v2.mp4']);
      vid.elt.muted = true;
      vid.loop();
      vid.hide();
    }
    function draw() {
      background(250);
      translate(-220, 0, 0);
      push();
      rotateZ(theta * mouseX * 0.001);
      rotateX(theta * mouseX * 0.001);
      rotateY(theta * mouseX * 0.001);
//pass image as texture

      texture(vid);
      sphere(150);
      pop();
      translate(440, 0, 0);
      push();
      rotateZ(theta * 0.1);
      rotateX(theta * 0.1);
      rotateY(theta * 0.1);
      texture(img);
      box(100, 100, 100);
      pop();
      theta += 0.05;
    }

### Ray Casting

![IMG_5928](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/e9879e71-66d6-42a0-a8dd-b9339c1e8bb4)

**Original example by Jonathan Watson.
Detecting the position of the mouse in 3D space with ray casting.**

    const objects = [];
    let eyeZ;
    function setup() {
      createCanvas(710, 400, WEBGL);
      eyeZ = height / 2 / tan((30 * PI) / 180); 
// The default distance the camera is away from the origin.

      objects.push(new IntersectPlane(1, 0, 0, -100, 0, 0)); 
// Left wall

      objects.push(new IntersectPlane(1, 0, 0, 100, 0, 0)); 
// Right wall

      objects.push(new IntersectPlane(0, 1, 0, 0, -100, 0)); 
// Bottom wall

      objects.push(new IntersectPlane(0, 1, 0, 0, 100, 0)); 
// Top wall

      objects.push(new IntersectPlane(0, 0, 1, 0, 0, 0)); 
// Back wall

      noStroke();
      ambientMaterial(250);
    }
    function draw() {
      background(0);
// Lights

      pointLight(255, 255, 255, 0, 0, 400);
      ambientLight(244, 122, 158);
// Left wall

      push();
      translate(-100, 0, 200);
      rotateY((90 * PI) / 180);
      plane(400, 200);
      pop();
// Right wall

      push();
      translate(100, 0, 200);
      rotateY((90 * PI) / 180);
      plane(400, 200);
      pop();
// Bottom wall

      push();
      translate(0, 100, 200);
      rotateX((90 * PI) / 180);
      plane(200, 400);
      pop();
// Top wall

      push();
      translate(0, -100, 200);
      rotateX((90 * PI) / 180);
      plane(200, 400);
      pop();
      plane(200, 200); 
// Back wall

      const x = mouseX - width / 2;
      const y = mouseY - height / 2;
      const Q = createVector(0, 0, eyeZ); 
// A point on the ray and the default position of the camera.

      const v = createVector(x, y, -eyeZ);  
// The direction vector of the ray.

      let intersect; 
// The point of intersection between the ray and a plane.

      let closestLambda = eyeZ * 10; 
// The draw distance.

      for (let x = 0; x < objects.length; x += 1) {
        let object = objects[x];
        let lambda = object.getLambda(Q, v); 
// The value of lambda where the ray intersects the object

        if (lambda < closestLambda && lambda > 0) {
// Find the position of the intersection of the ray and the object.

          intersect = p5.Vector.add(Q, p5.Vector.mult(v, lambda));
          closestLambda = lambda;
        }
      }
// Cursor

      push();
      translate(intersect);
      fill(237, 34, 93);
      sphere(10);
      pop();
    }
// Class for a plane that extends to infinity.

    class IntersectPlane {
      constructor(n1, n2, n3, p1, p2, p3) {
        this.normal = createVector(n1, n2, n3); 
// The normal vector of the plane

        this.point = createVector(p1, p2, p3); 
// A point on the plane

        this.d = this.point.dot(this.normal);
      }
      getLambda(Q, v) {
        return (-this.d - this.normal.dot(Q)) / this.normal.dot(v);
      }
    }

### Orbit Control

![IMG_5929](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/8d3aa7ab-7895-422f-8ee9-7f0027b83c36)

**Orbit control allows you to drag and move around the world.**

    function setup() {
      createCanvas(710, 400, WEBGL);
    }
    function draw() {
      background(250);
      let radius = width * 1.5;
//drag to move the world.

      orbitControl();
      normalMaterial();
      translate(0, 0, -600);
      for (let i = 0; i <= 12; i++) {
        for (let j = 0; j <= 12; j++) {
          push();
          let a = (j / 12) * PI;
          let b = (i / 12) * PI;
          translate(
            sin(2 * a) * radius * sin(b),
            (cos(b) * radius) / 2,
            cos(2 * a) * radius * sin(b)
          );
          if (j % 2 === 0) {
            cone(30, 30);
          } else {
            box(30, 30, 30);
          }
          pop();
        }
      }
    }

### Basic Shader

![IMG_5930](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/64d1d1d9-ce73-4ba6-a075-16c16abe2101)

**This is a basic example showing how to load shaders in p5.js.
To learn more about using shaders in p5.js: p5.js Shaders**

// this variable will hold our shader object

    let theShader;
    function preload(){
// load the shader

      theShader = loadShader('assets/basic.vert', 'assets/basic.frag');
    }
    function setup() {
// shaders require WEBGL mode to work

      createCanvas(710, 400, WEBGL);
      noStroke();
    }
    function draw() {
// shader() sets the active shader with our shader

      shader(theShader);
// rect gives us some geometry on the screen

      rect(0,0,width, height);
    }

### Shader as a Texture

![IMG_5931](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/8dca72ed-a9c1-42a8-8556-81440f387952)

**Shaders can be applied to 2D/3D shapes as textures.
To learn more about using shaders in p5.js: p5.js Shaders**

// this variable will hold our shader object

     let theShader;
// this variable will hold our createGraphics layer

     let shaderTexture;
     let theta = 0;
     let x;
     let y;
     let outsideRadius = 200;
     let insideRadius = 100;
     function preload(){
// load the shader

       theShader = loadShader('assets/texture.vert','assets/texture.frag');
     }
     function setup() {
// shaders require WEBGL mode to work

       createCanvas(710, 400, WEBGL);
       noStroke();
// initialize the createGraphics layers
   
       shaderTexture = createGraphics(710, 400, WEBGL);
// turn off the createGraphics layers stroke
   
       shaderTexture.noStroke();
        x = -50;
        y = 0;
     }
     function draw() {
// instead of just setting the active shader we are passing it to the createGraphics layer

       shaderTexture.shader(theShader);
// here we're using setUniform() to send our uniform values to the shader

       theShader.setUniform("resolution", [width, height]);
       theShader.setUniform("time", millis() / 1000.0);
       theShader.setUniform("mouse", [mouseX, map(mouseY, 0, height, height, 0)]);
// passing the shaderTexture layer geometry to render on
   
       shaderTexture.rect(0,0,width,height);
       background(255);
// pass the shader as a texture

       texture(shaderTexture);
       translate(-150, 0, 0);
       push();
       rotateZ(theta * mouseX * 0.0001);
       rotateX(theta * mouseX * 0.0001);
       rotateY(theta * mouseX * 0.0001);
       theta += 0.05;
       sphere(125);
       pop();
// passing a fifth parameter to ellipse for smooth edges in 3D

       ellipse(260,0,200,200,100);
     }


### Passing Shader Uniforms

### ![IMG_5933](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/4a605443-0c47-4e46-874f-bdc81b962791)

### ![IMG_5934](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/c5d5d0f4-88b3-4083-a68d-ab10656e2db8)

**Uniforms are the way in which information is passed from p5 to the shader.
To learn more about using shaders in p5.js: p5.js Shaders**

// this variable will hold our shader object

     let theShader;
     function preload(){
// load the shader

       theShader = loadShader('assets/uniforms.vert', 'assets/uniforms.frag');
     }
     function setup() {
// shaders require WEBGL mode to work

       createCanvas(710, 400, WEBGL);
       noStroke();
     }
     function draw() {
// shader() sets the active shader with our shader

       shader(theShader);
// lets send the resolution, mouse, and time to our shader
// before sending mouse + time we modify the data so it's more easily usable by the shader

       theShader.setUniform('resolution', [width, height]);
       theShader.setUniform('mouse', map(mouseX, 0, width, 0, 7));
       theShader.setUniform('time', frameCount * 0.01);
// rect gives us some geometry on the screen

       rect(0,0,width, height);
     }

### Shader Using Webcam

![IMG_5935](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/3ffdacab-33df-445a-ab77-6c57a0920234)

**The webcam can be passed to shaders as a texture.
To learn more about using shaders in p5.js: p5.js Shaders**

 // this variable will hold our shader object
 
     let theShader;
 // this variable will hold our webcam video

     let cam;
     function preload(){
// load the shader

       theShader = loadShader('assets/webcam.vert', 'assets/webcam.frag');
     }
     function setup() {
// shaders require WEBGL mode to work

       createCanvas(710, 400, WEBGL);
       noStroke();
       cam = createCapture(VIDEO);
       cam.size(710, 400);
       cam.hide();
     }
     function draw() {
// shader() sets the active shader with our shader

       shader(theShader);
// passing cam as a texture

       theShader.setUniform('tex0', cam);
// rect gives us some geometry on the screen

       rect(0,0,width,height);
     }

### Blur using Framebuffer Depth

![IMG_5938](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/796572b5-8d0f-4fb1-84fb-29a11aaba645)

**A shader that uses depth information from a p5.Framebuffer to draw a scene with focal blur.**

    let layer;
    let blur;
    function setup() {
      createCanvas(windowWidth, windowHeight, WEBGL);
      layer = createFramebuffer();
      blur = createShader(vert, frag);
      noStroke();
    }
    function draw() {
// Draw a scene

      layer.begin();
      background(255);
      ambientLight(100);
      directionalLight(255, 255, 255, -1, 1, -1);
      ambientMaterial(255, 0, 0);
      fill(255, 255, 100);
      specularMaterial(255);
      shininess(150);  
      rotateY(millis() * 0.001);
      for (let i = 0; i < 5; i++) {
        push();
        translate((i-2)*100, 0, 0);
        sphere();
        pop();
      }
      layer.end();
// Render the scene with depth of field blur

      shader(blur);
      blur.setUniform('img', layer.color);
      blur.setUniform('depth', layer.depth);
      rect(0, 0, width, height);
    }
    function windowResized() {
      resizeCanvas(windowWidth, windowHeight);
    }
    let vert = `
    precision highp float;
    attribute vec3 aPosition;
    attribute vec2 aTexCoord;
    varying vec2 vTexCoord;
    void main() {
      vec4 positionVec4 = vec4(aPosition, 1.0);
      positionVec4.xy = positionVec4.xy * 2.0 - 1.0;
      positionVec4.y *= -1.0;
      gl_Position = positionVec4;
      vTexCoord = aTexCoord;
    }`;
    let frag = `
    precision highp float;
    varying vec2 vTexCoord;
    uniform sampler2D img;
    uniform sampler2D depth;
    float getBlurriness(float d) {
// Blur more the farther away we go from the
// focal point at depth=0.9

      return abs(d - 0.9) * 40.;
    }
    float maxBlurDistance(float blurriness) {
      return blurriness * 0.01;
    }
    void main() {
      vec4 color = texture2D(img, vTexCoord);
      float samples = 1.;
      float centerDepth = texture2D(depth, vTexCoord).r;
      float blurriness = getBlurriness(centerDepth);
      for (int sample = 0; sample < 20; sample++) {
// Sample nearby pixels in a spiral going out from the
// current pixel

        float angle = float(sample);
        float distance = float(sample)/20.
          * maxBlurDistance(blurriness);
        vec2 offset = vec2(cos(angle), sin(angle)) * distance;
// How close is the object at the nearby pixel?

        float sampleDepth = texture2D(depth, vTexCoord + offset).r;
// How far should its blur reach?

        float sampleBlurDistance =
          maxBlurDistance(getBlurriness(sampleDepth));
// If it's in front of the current pixel, or its blur overlaps
// with the current pixel, add its color to the average

        if (
          sampleDepth >= centerDepth ||
          sampleBlurDistance >= distance
        ) {
          color += texture2D(img, vTexCoord + offset);
          samples++;
        }
      }
      color /= samples;
      gl_FragColor = color;
    }`;


## Input

### Clock

![IMG_5940](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/8234a30c-4e8c-44ca-93f7-cc3c54f10e9b)

**The current time can be read with the second(), minute(), and hour() functions. In this example, sin() and cos() values are used to set the position of the hands.**

    let cx, cy;
    let secondsRadius;
    let minutesRadius;
    let hoursRadius;
    let clockDiameter;
    function setup() {
      createCanvas(720, 400);
      stroke(255);
      let radius = min(width, height) / 2;
      secondsRadius = radius * 0.71;
      minutesRadius = radius * 0.6;
      hoursRadius = radius * 0.5;
      clockDiameter = radius * 1.7;
      cx = width / 2;
      cy = height / 2;
    }
    function draw() {
      background(230);
// Draw the clock background

      noStroke();
      fill(244, 122, 158);
      ellipse(cx, cy, clockDiameter + 25, clockDiameter + 25);
      fill(237, 34, 93);
      ellipse(cx, cy, clockDiameter, clockDiameter);
// Angles for sin() and cos() start at 3 o'clock;
// subtract HALF_PI to make them start at the top

      let s = map(second(), 0, 60, 0, TWO_PI) - HALF_PI;
      let m = map(minute() + norm(second(), 0, 60), 0, 60, 0, TWO_PI) - HALF_PI;
      let h = map(hour() + norm(minute(), 0, 60), 0, 24, 0, TWO_PI * 2) - HALF_PI;
// Draw the hands of the clock

      stroke(255);
      strokeWeight(1);
      line(cx, cy, cx + cos(s) * secondsRadius, cy + sin(s) * secondsRadius);
      strokeWeight(2);
      line(cx, cy, cx + cos(m) * minutesRadius, cy + sin(m) * minutesRadius);
      strokeWeight(4);
      line(cx, cy, cx + cos(h) * hoursRadius, cy + sin(h) * hoursRadius);
// Draw the minute ticks

      strokeWeight(2);
      beginShape(POINTS);
      for (let a = 0; a < 360; a += 6) {
        let angle = radians(a);
        let x = cx + cos(angle) * secondsRadius;
        let y = cy + sin(angle) * secondsRadius;
        vertex(x, y);
      }
      endShape();
    }

### Constrain

![IMG_5941](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/4a97e909-e1a0-44be-bde3-47a9e96eb64a)

**Move the mouse across the screen to move the circle. The program constrains the circle to its box.**

    let mx = 1;
    let my = 1;
    let easing = 0.05;
    let radius = 24;
    let edge = 100;
    let inner = edge + radius;
    function setup() {
      createCanvas(720, 400);
      noStroke();
      ellipseMode(RADIUS);
      rectMode(CORNERS);
    }
    function draw() {
      background(230);
      if (abs(mouseX - mx) > 0.1) {
        mx = mx + (mouseX - mx) * easing;
      }
      if (abs(mouseY - my) > 0.1) {
        my = my + (mouseY - my) * easing;
      }
      mx = constrain(mx, inner, width - inner);
      my = constrain(my, inner, height - inner);
      fill(237, 34, 93);
      rect(edge, edge, width - edge, height - edge);
      fill(255);
      ellipse(mx, my, radius, radius);
    }

### Easing

![IMG_5941](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/3454d417-1f7b-492d-917d-a5de5aee5f3e)

**Move the mouse across the screen and the symbol will follow. Between drawing each frame of the animation, the program calculates the difference between the position of the symbol and the cursor. If the distance is larger than 1 pixel, the symbol moves part of the distance (0.05) from its current position toward the cursor.**

    let x = 1;
    let y = 1;
    let easing = 0.05;
    function setup() {
      createCanvas(720, 400);
      noStroke();
    }
    function draw() {
      background(237, 34, 93);
      let targetX = mouseX;
      let dx = targetX - x;
      x += dx * easing;
      let targetY = mouseY;
      let dy = targetY - y;
      y += dy * easing;
      ellipse(x, y, 66, 66);
    }


### Keyboard

**Click on the image to give it focus and press the letter keys to create forms in time and space. Each key has a unique identifying number. These numbers can be used to position shapes in space.**

    let rectWidth;
    function setup() {
      createCanvas(720, 400);
      noStroke();
      background(230);
      rectWidth = width / 4;
    }
    function draw() {
// keep draw() here to continue looping while waiting for keys

    }
    function keyPressed() {
      let keyIndex = -1;
      if (key >= 'a' && key <= 'z') {
        keyIndex = key.charCodeAt(0) - 'a'.charCodeAt(0);
      }
      if (keyIndex === -1) {
// If it's not a letter key, clear the screen

        background(230);
      } else {
// It's a letter key, fill a rectangle

        randFill_r = Math.floor(Math.random() * 255 + 1);
        randFill_g = Math.floor(Math.random() * 255 + 1);
        randFill_b = Math.floor(Math.random() * 255 + 1);
        fill(randFill_r, randFill_g, randFill_b);
        let x = map(keyIndex, 0, 25, 0, width - rectWidth);
        rect(x, 0, rectWidth, height);
      }
    }


### Milliseconds

![IMG_5946](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/05612f50-fd5c-4a4d-9bc7-6ec98c4a7f6f)

**A millisecond is 1/1000 of a second. Processing keeps track of the number of milliseconds a program has run. By modifying this number with the modulo(%) operator, different patterns in time are created.**

**This example is ported from the Milliseconds example on the Processing website**

    let scale;
    function setup() {
      createCanvas(720, 400);
      noStroke();
      scale = width/20;
    }
    function draw() { 
      let i;
      for ( i = 0; i < scale; i++) {
        colorMode(RGB, (i+1) * scale * 10);
        fill(millis()%((i+1) * scale * 10));
        rect(i*scale, 0, scale, height);
      }
    }

### Rollover

<img width="719" alt="Screen Shot 2023-10-19 at 5 42 35 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/6d2107d4-70ea-4863-ae70-003c483770db">

**Roll over the colored squares in the center of the image to change the color of the outside rectangle.** 
**This example is ported from the Rollover example on the Processing website**

    let squareX, squareY;  // Position of square button
    let circleX, circleY;  // Position of circle button
    let squareSize = 90;   // Width/height of square
    let circleSize = 93;   // Diameter of circle
    let squareColor;
    let circleColor;
    let baseColor;
    let squareOver = false;
    let circleOver = false;
    function setup() {
      createCanvas(710, 400);
      squareColor = color(0);
      circleColor = color(255);
      baseColor = color(102);
      circleX = width/2+circleSize/2+10;
      circleY = height/2;
      squareX = width/2-squareSize-10;
      squareY = height/2-squareSize/2;
    }
    function draw() {
      update(mouseX, mouseY);
      noStroke();
      if (squareOver) {
        background(squareColor);
      } else if (circleOver) {
        background(circleColor);
      } else {
        background(baseColor);
      }
      stroke(255);
      fill(squareColor);
      square(squareX, squareY, squareSize);
      stroke(0);
      fill(circleColor);
      circle(circleX, circleY, circleSize);
    }
    function update(x, y) {
      if( overCircle(circleX, circleY, circleSize) ) {
        circleOver = true;
        squareOver = false;
      } else if ( overSquare(squareX, squareY, squareSize) ) {
        squareOver = true;
        circleOver = false;
      } else {
        circleOver = squareOver = false;
      }
    }
    function overSquare(x, y, size) {
      if (mouseX >= x && mouseX <= x+size && 
          mouseY >= y && mouseY <= y+size) {
        return true;
      } else {
        return false;
      }
    }
    function overCircle(x, y, diameter) {
      const disX = x - mouseX;
      const disY = y - mouseY;
      if(sqrt(sq(disX) + sq(disY)) < diameter/2 ) {
        return true;
      } else {
        return false;
      }
    }

### Storing Input

<img width="725" alt="Screen Shot 2023-10-19 at 5 49 33 PM" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/5584183a-8253-4b1e-abaf-3f995107dbed">

**Move the mouse across the screen to change the position of the circles. The positions of the mouse are recorded into an array and played back every frame. Between each frame, the newest value are added to the end of each array and the oldest value is deleted.**

    let num = 60;
    let mx = [];
    let my = [];
    function setup() {
      createCanvas(720, 400);
      noStroke();
      fill(255, 153);
      for (let i = 0; i < num; i++) {
        mx.push(i);
        my.push(i);
      }
    }
    function draw() {
      background(237, 34, 93);
// Cycle through the array, using a different entry on each frame.
// Using modulo (%) like this is faster than moving all the values over.

      let which = frameCount % num;
      mx[which] = mouseX;
      my[which] = mouseY;
      for (let i = 0; i < num; i++) {
// which+1 is the smallest (the oldest in the array)

        let index = (which + 1 + i) % num;
        ellipse(mx[index], my[index], i, i);
      }
    }


## Advanced Data

### Load Saved JSON

**Create a Bubble class, instantiate multiple bubbles using data from a JSON file, and display results on the screen. Because web browsers differ in where they save files, we do not make use of saveJSON(), unlike the Processing example.**

**Based on Daniel Shiffman's LoadSaveJSON Example for Processing.**

// Bubble class

    class Bubble {
      constructor(x, y, diameter, name) {
        this.x = x;
        this.y = y;
        this.diameter = diameter;
        this.radius = diameter / 2;
        this.name = name;
        this.over = false;
      }
// Check if mouse is over the bubble

      rollover(px, py) {
        let d = dist(px, py, this.x, this.y);
        this.over = d < this.radius;
      }
// Display the Bubble

      display() {
        stroke(0);
        strokeWeight(0.8);
        noFill();
        ellipse(this.x, this.y, this.diameter, this.diameter);
        if (this.over) {
          fill(0);
          textAlign(CENTER);
          text(this.name, this.x, this.y + this.radius + 20);
        }
      }
    }
    let data = {}; // Global object to hold results from the loadJSON call
    let bubbles = []; // Global array to hold all bubble objects
// Put any asynchronous data loading in preload to complete before "setup" is run

    function preload() {
      data = loadJSON('assets/bubbles.json');
    }
// Convert saved Bubble data into Bubble Objects

    function loadData() {
      let bubbleData = data['bubbles'];
      for (let i = 0; i < bubbleData.length; i++) {
// Get each object in the array

        let bubble = bubbleData[i];
// Get a position object

        let position = bubble['position'];
// Get x,y from position

        let x = position['x'];
        let y = position['y'];
// Get diameter and label

        let diameter = bubble['diameter'];
        let label = bubble['label'];
// Put object in array

        bubbles.push(new Bubble(x, y, diameter, label));
      }
    }
// Create a new Bubble each time the mouse is clicked.

    function mousePressed() {
// Add diameter and label to bubble

      let diameter = random(40, 80);
      let label = 'New Label';
// Append the new JSON bubble object to the array

      bubbles.push(new Bubble(mouseX, mouseY, diameter, label));
// Prune Bubble Count if there are too many

      if (bubbles.length > 10) {
        bubbles.shift(); // remove first item from array
      }
    }
    function setup() {
      createCanvas(640, 360);
      loadData();
    }
    function draw() {
      background(255);
// Display all bubbles

      for (let i = 0; i < bubbles.length; i++) {
        bubbles[i].display();
        bubbles[i].rollover(mouseX, mouseY);
      }
// Label directions at bottom

      textAlign(LEFT);
      fill(0);
      text('Click to add bubbles.', 10, height - 10);
    }


### Load Saved Table

**Create a Bubble class, instantiate multiple bubbles using data from a csv file, and display results on the screen. Because web browsers differ in where they save files, we do not make use of saveTable(), unlike the Processing example.**

**Based on Daniel Shiffman's LoadSaveTable Example for Processing.**


## Sound

### Load/Play Sound

**Load sound during preload(). Play a sound when canvas is clicked.**

**To run this example locally, you will need the p5.sound library a sound file, and a running local server.**

    let song;
    function setup() {
      song = loadSound('assets/lucky_dragons_-_power_melody.mp3');
      createCanvas(720, 200);
      background(255, 0, 0);
    }
    function mousePressed() {
      if (song.isPlaying()) {
// .isPlaying() returns a boolean

        song.stop();
        background(255, 0, 0);
      } else {
        song.play();
        background(0, 255, 0);
      }
    }

### Preload SoundFile

**Call loadSound() during preload() to ensure that the sound is completely loaded before setup() is called. It's best to always call loadSound() in preload(), otherwise sounds won't necessarily be loaded by the time you want to play them in your sketch.**

**To run this example locally, you will need the p5.sound library a sound file, and a running local server.**

    let song;
    function preload() {
      song = loadSound('assets/lucky_dragons_-_power_melody.mp3');
    }
    function setup() {
      createCanvas(710, 200);
      song.loop(); 
// song is ready to play during setup() because it was loaded during preload

      background(0, 255, 0);
    }
    function mousePressed() {
      if (song.isPlaying()) {
// .isPlaying() returns a boolean

        song.pause(); 
// .play() will resume from .pause() position

        background(255, 0, 0);
      } else {
        song.play();
        background(0, 255, 0);
      }
    }

### SoundFormats

**Technically, due to patent issues, there is no single sound format that is supported by all web browsers. While mp3 is supported across the latest versions of major browsers on OS X and Windows, for example, it may not be available on some less mainstream operating systems and browsers.
*
To ensure full compatibility, you can include the same sound file in multiple formats, e.g. 'sound.mp3' and 'sound.ogg'. (Ogg is an open source alternative to mp3.) You can convert audio files into web friendly formats for free online at media.io
. *
The soundFormats() method tells loadSound which formats we have included with our sketch. Then, loadSound will attempt to load the first format that is supported by the client's web browser.**

**To run this example locally, you will need the p5.sound library a sound file, and a running local server.**

    let song;
    function preload() {
  // we have included both an .ogg file and an .mp3 file
  
      soundFormats('ogg', 'mp3');
  // if mp3 is not supported by this browser,
  // loadSound will load the ogg file
  // we have included with our sketch
  
      song = loadSound('assets/lucky_dragons_-_power_melody.mp3');
    }
    function setup() {
      createCanvas(710, 200);
// song loaded during preload(), ready to play in setup()

      song.play();
      background(0, 255, 0);
    }
    function mousePressed() {
      if (song.isPlaying()) {
// .isPlaying() returns a boolean

        song.pause();
        background(255, 0, 0);
      } else {
        song.play(); 
// playback will resume from the pause position

        background(0, 255, 0);
      }
    }


### Play Mode

**In 'sustain' mode, the sound will overlap with itself. In 'restart' mode it will stop and then start again. Click mouse to play a sound file. Trigger lots of sounds at once! Press any key to change playmode.**

**To run this example locally, you will need the p5.sound library a sound file, and a running local server.**

    let playMode = 'sustain';
    let sample;
    function setup() {
      createCanvas(710, 50);
      soundFormats('mp3', 'ogg');
      sample = loadSound('assets/Damscray_-_Dancing_Tiger_02.mp3');
    }
    function draw() {
      background(255, 255, 0);
      let str = 'Click here to play! Press key to toggle play mode.';
      str += ' Current Play Mode: ' + playMode + '.';
      text(str, 10, height / 2);
    }
    function mouseClicked() {
      sample.play();
    }
    function keyPressed(k) {
      togglePlayMode();
    }
    function togglePlayMode() {
      if (playMode === 'sustain') {
        playMode = 'restart';
      } else {
        playMode = 'sustain';
      }
      sample.playMode(playMode);
    }

### Pan Sound

<img width="725" src="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/55c1b0c0-ebbe-4f6a-811a-52eb54a38d68">

**Click mouse to play the sound. Ball position follows mouse and correlates to panning of sound.**

**To run this example locally, you will need the p5.sound library a sound file, and a running local server.**

    let ball = {};
    let soundFile;
    function preload() {
      soundFormats('mp3', 'ogg');
      soundFile = loadSound('assets/beatbox.ogg');
    }
    function setup() {
      createCanvas(710, 100);
    }
    function draw() {
      background(0);
      ball.x = constrain(mouseX, 0, width);
      ellipse(ball.x, height / 2, 100, 100);
    }
    function mousePressed() {
// map the ball's x location to a panning degree
// between -1.0 (left) and 1.0 (right)

      let panning = map(ball.x, 0, width, -1.0, 1.0);
      soundFile.pan(panning);
      soundFile.play();
    }


### Sound Effect

**Play a sound effect when the mouse is clicked inside the circle.**

**To run this example locally, you will need the p5.sound library a sound file, and a running local server.**

// Adapted from Learning Processing by Daniel Shiffman
// http://www.learningprocessing.com
// Doorbell sample by Corsica_S via freesound.org,
// Creative Commons BY 3.0
// A Class to describe a "doorbell" (really a button)

    class Doorbell {
      constructor(x_, y_, r_) {
// Location and size

        this.x = x_;
        this.y = y_;
        this.r = r_;
      }
// Is a point inside the doorbell? (used for mouse rollover, etc.)

      contains(mx, my) {
        return dist(mx, my, this.x, this.y) < this.r;
      }
// Show the doorbell (hardcoded colors, could be improved)
  
      display(mx, my) {
        if (this.contains(mx, my)) {
          fill(100);
        } else {
          fill(175);
        }
        stroke(0);
        strokeWeight(4);
        ellipseMode(RADIUS);
        ellipse(this.x, this.y, this.r, this.r);
      }
    }
// A sound file object

    let dingdong;
// A doorbell object (that will trigger the sound)

    let doorbell;
    function setup() {
      createCanvas(200, 200);
// Load the sound file.
// We have included both an MP3 and an OGG version.

      soundFormats('mp3', 'ogg');
      dingdong = loadSound('assets/doorbell.mp3');
// Create a new doorbell

      doorbell = new Doorbell(width / 2, height / 2, 32);
    }
    function draw() {
      background(255);
// Show the doorbell

      doorbell.display(mouseX, mouseY);
    }
    function mousePressed() {
// If the user clicks on the doorbell, play the sound!

      if (doorbell.contains(mouseX, mouseY)) {
        dingdong.play();
      }
    }

### Playback Rate

<IMG width="725" scr="https://github.com/SC36-11-1/SC36-11-1/assets/133059820/fd53d872-d3cc-4ae6-9dbb-f892ea6811da"> 

**Load a SoundFile and map its playback rate to mouseY, volume to mouseX. Playback rate is the speed with which the web audio context processings the sound file information. Slower rates not only increase the duration of the sound, but also decrease the pitch because it is being played back at a slower frequency。**

**To run this example locally, you will need the p5.sound library a sound file, and a running local server.**

// A sound file object

    let song;
    function preload() {
// Load a sound file

      song = loadSound('assets/Damscray_DancingTiger.mp3');
    }
    function setup() {
      createCanvas(710, 400);
// Loop the sound forever
// (well, at least until stop() is called)

      song.loop();
    }
    function draw() {
      background(200);
// Set the volume to a range between 0 and 1.0

      let volume = map(mouseX, 0, width, 0, 1);
      volume = constrain(volume, 0, 1);
      song.amp(volume);
// Set the rate to a range between 0.1 and 4
// Changing the rate alters the pitch

      let speed = map(mouseY, 0.1, height, 0, 2);
      speed = constrain(speed, 0.01, 4);
      song.rate(speed);
// Draw some circles to show what is going on

      stroke(0);
      fill(51, 100);
      ellipse(mouseX, 100, 48, 48);
      stroke(0);
      fill(51, 100);
      ellipse(100, mouseY, 48, 48);
    }

### Measuring Amplitude

**Analyze the amplitude of sound with p5.Amplitude.
*
Amplitude is the magnitude of vibration. Sound is vibration, so its amplitude is is closely related to volume / loudness.
*
The getLevel() method takes an array of amplitude values collected over a small period of time (1024 samples). Then it returns the Root Mean Square (RMS) of these values.
*
The original amplitude values for digital audio are between -1.0 and 1.0. But the RMS will always be positive, because it is squared. And, rather than use instantanous amplitude readings that are sampled at a rate of 44,100 times per second, the RMS is an average over time (1024 samples, in this case), which better represents how we hear amplitude.**

**To run this example locally, you will need the p5.sound library a sound file, and a running local server.**

    let song, analyzer;
    function preload() {
      song = loadSound('assets/lucky_dragons_-_power_melody.mp3');
    }
    function setup() {
      createCanvas(710, 200);
      song.loop();
// create a new Amplitude analyzer

      analyzer = new p5.Amplitude();
// Patch the input to an volume analyzer

      analyzer.setInput(song);
    }
    function draw() {
      background(255);
// Get the average (root mean square) amplitude

      let rms = analyzer.getLevel();
      fill(127);
      stroke(0);
// Draw an ellipse with size based on volume

      ellipse(width / 2, height / 2, 10 + rms * 200, 10 + rms * 200);
    }


### Noise Drum Envelope

White Noise is a random audio signal with equal energy at every part of the frequency spectrum*
An Envelope is a series of fades, defined as time / value pairs.
In this example, the p5.Env will be used to "play" the p5.Noise like a drum by controlling its output amplitude. A p5.Amplitude will get the level of all sound in the sketch, and we'll use this value to draw a green rectangle that shows the envelope in action.

*To run this example locally, you will need the p5.sound library and a sound file.*

    let noise, env, analyzer;
    function setup() {
      createCanvas(710, 200);
      noise = new p5.Noise(); // other types include 'brown' and 'pink'
      noise.start();

// multiply noise volume by 0
// (keep it quiet until we're ready to make noise!)

      noise.amp(0);
      env = new p5.Env();
      
// set attackTime, decayTime, sustainRatio, releaseTime

      env.setADSR(0.001, 0.1, 0.2, 0.1);
  
// set attackLevel, releaseLevel

      env.setRange(1, 0);

// p5.Amplitude will analyze all sound in the sketch
// unless the setInput() method is used to specify an input.
  
      analyzer = new p5.Amplitude();
    }
    function draw() {
      background(0);

// get volume reading from the p5.Amplitude analyzer

      let level = analyzer.getLevel();

// use level to draw a green rectangle

      let levelHeight = map(level, 0, 0.4, 0, height);
      fill(100, 250, 100);
      rect(0, height, width, -levelHeight);
    }
    function mousePressed() {
      env.play(noise);
    }


### Oscillator Frequency

Control an Oscillator and view the waveform using FFT. MouseX is mapped to frequency, mouseY is mapped to amplitude.

*To run this example locally, you will need the p5.sound library and a sound file.*

    let osc, fft;
    function setup() {
      createCanvas(720, 256);
      osc = new p5.TriOsc(); 

// set frequency and type

      osc.amp(0.5);
      fft = new p5.FFT();
      osc.start();
    }
    function draw() {
      background(255);


// analyze the waveform

      let waveform = fft.waveform(); 
      beginShape();
      strokeWeight(5);
      for (let i = 0; i < waveform.length; i++) {
        let x = map(i, 0, waveform.length, 0, width);
        let y = map(waveform[i], -1, 1, height, 0);
        vertex(x, y);
      }
      endShape();

// change oscillator frequency based on mouseX

      let freq = map(mouseX, 0, width, 40, 880);
      osc.freq(freq);
      let amp = map(mouseY, 0, height, 1, 0.01);
      osc.amp(amp);
    }



### Mic Input

Get audio input from your computer's microphone. Make noise to float the ellipse.
Note: p5.AudioIn contains its own p5.Amplitude object, so you can call getLevel on p5.AudioIn without creating a p5.Amplitude.

To run this example locally, you will need the p5.sound library and a running local server.

    let mic;
    function setup() {
      createCanvas(710, 200);

// Create an Audio input

      mic = new p5.AudioIn();

// start the Audio Input.
// By default, it does not .connect() (to the computer speakers)

      mic.start();
    }
    function draw() {
      background(200);

// Get the overall volume (between 0 and 1.0)

      let vol = mic.getLevel();
      fill(127);
      stroke(0);

// Draw an ellipse with height based on volume

      let h = map(vol, 0, 1, height, 0);
      ellipse(width / 2, h - 25, 50, 50);
    }



### Frequency Spectrum

Visualize the frequency spectrum of live audio input.

*To run this example locally, you will need the p5.sound library and a running local server.*

    let mic, fft;
    function setup() {
      createCanvas(710, 400);
      noFill();
      mic = new p5.AudioIn();
      mic.start();
      fft = new p5.FFT();
      fft.setInput(mic);
    }
    function draw() {
      background(200);
      let spectrum = fft.analyze();
      beginShape();
      for (i = 0; i < spectrum.length; i++) {
        vertex(i, map(spectrum[i], 0, 255, height, 0));
      }
      endShape();
    }


### Mic Threshold

Trigger an event (draw a rectangle) when the Audio Input volume surpasses a threshold.

*To run this example locally, you will need the p5.sound library and a running local server.*

// Adapted from Learning Processing, Daniel Shiffman
// learningprocessing.com

    let input;
    let analyzer;
    function setup() {
      createCanvas(710, 200);
      background(255);

// Create an Audio input

      input = new p5.AudioIn();
      input.start();
    }
    function draw() {

// Get the overall volume (between 0 and 1.0)

      let volume = input.getLevel();

// If the volume > 0.1,  a rect is drawn at a random location.
// The louder the volume, the larger the rectangle.

      let threshold = 0.1;
      if (volume > threshold) {
        stroke(0);
        fill(0, 100);
        rect(random(40, width), random(height), volume * 50, volume * 50);
      }

// Graph the overall potential volume, w/ a line at the threshold
  
      let y = map(volume, 0, 1, height, 0);
      let ythreshold = map(threshold, 0, 1, height, 0);
      noStroke();
      fill(175);
      rect(0, 0, 20, height);

// Then draw a rectangle on the graph, sized according to volume

      fill(0);
      rect(0, y, 20, y);
      stroke(0);
      line(0, ythreshold, 19, ythreshold);
    }

### Filter LowPass

Apply a p5.LowPass filter to a p5.SoundFile. Visualize the sound with FFT. Map mouseX to the the filter's cutoff frequency and mouseY to resonance/width of the a BandPass filter *

*To run this example locally, you will need the p5.sound library a sound file, and a running local server.*

    let soundFile;
    let fft;
    let filter, filterFreq, filterRes;
    function preload() {
      soundFormats('mp3', 'ogg');
      soundFile = loadSound('assets/beat');
    }
    function setup() {
      createCanvas(710, 256);
      fill(255, 40, 255);

// loop the sound file
 
      soundFile.loop();
      filter = new p5.LowPass();

// Disconnect soundfile from master output.
// Then, connect it to the filter, so that we only hear the filtered sound

      soundFile.disconnect();
      soundFile.connect(filter);
      fft = new p5.FFT();
    }
    function draw() {
      background(30);

// Map mouseX to a the cutoff frequency from the lowest
// frequency (10Hz) to the highest (22050Hz) that humans can hear

      filterFreq = map(mouseX, 0, width, 10, 22050);

// Map mouseY to resonance (volume boost) at the cutoff frequency

      filterRes = map(mouseY, 0, height, 15, 5);

// set filter parameters

      filter.set(filterFreq, filterRes);

// Draw every value in the FFT spectrum analysis where
// x = lowest (10Hz) to highest (22050Hz) frequencies,
// h = energy (amplitude / volume) at that frequency

      let spectrum = fft.analyze();
      noStroke();
      for (let i = 0; i < spectrum.length; i++) {
        let x = map(i, 0, spectrum.length, 0, width);
        let h = -height + map(spectrum[i], 0, 255, height, 0);
        rect(x, height, width / spectrum.length, h);
      }
    }


### Filter BandPass

Apply a p5.BandPass filter to white noise. Visualize the sound with FFT. Map mouseX to the bandpass frequency and mouseY to resonance/width of the a BandPass filter *

*To run this example locally, you will need the p5.sound library a sound file, and a running local server.*

    let noise;
    let fft;
    let filter, filterFreq, filterWidth;
    function setup() {
      createCanvas(710, 256);
      fill(255, 40, 255);
      filter = new p5.BandPass();
      noise = new p5.Noise();

// Disconnect soundfile from master output...

      noise.disconnect(); 

// ...and connect to filter so we'll only hear BandPass.

      filter.process(noise); 
      noise.start();
      fft = new p5.FFT();
    }
    function draw() {
      background(30);

// Map mouseX to a bandpass freq from the FFT spectrum range: 10Hz - 22050Hz

      filterFreq = map(mouseX, 0, width, 10, 22050);
  
// Map mouseY to resonance/width

      filterWidth = map(mouseY, 0, height, 0, 90);
  
// set filter parameters

      filter.set(filterFreq, filterWidth);

// Draw every value in the FFT spectrum analysis where
// x = lowest (10Hz) to highest (22050Hz) frequencies,
// h = energy / amplitude at that frequency

      let spectrum = fft.analyze();
      noStroke();
      for (let i = 0; i < spectrum.length; i++) {
        let x = map(i, 0, spectrum.length, 0, width);
        let h = -height + map(spectrum[i], 0, 255, height, 0);
        rect(x, height, width / spectrum.length, h);
      }
    }


### Delay

Click the mouse to hear the p5.Delay process a SoundFile. MouseX controls the p5.Delay Filter Frequency. MouseY controls both the p5.Delay Time and Resonance. Visualize the resulting sound's volume with an Amplitude object. *

*To run this example locally, you will need the p5.sound library a sound file, and a running local server.*


    let soundFile, analyzer, delay;
    function preload() {
      soundFormats('ogg', 'mp3');
      soundFile = loadSound('assets/beatbox.mp3');
    }
    function setup() {
      createCanvas(710, 400);

// so we'll only hear delay

      soundFile.disconnect(); 
      delay = new p5.Delay();
      delay.process(soundFile, 0.12, 0.7, 2300);

// a stereo effect
  
      delay.setType('pingPong'); 
      analyzer = new p5.Amplitude();
    }
    function draw() {
      background(0);

// get volume reading from the p5.Amplitude analyzer

      let level = analyzer.getLevel();

// use level to draw a green rectangle

      let levelHeight = map(level, 0, 0.1, 0, height);
      fill(100, 250, 100);
      rect(0, height, width, -levelHeight);
      let filterFreq = map(mouseX, 0, width, 60, 15000);
      filterFreq = constrain(filterFreq, 60, 15000);
      let filterRes = map(mouseY, 0, height, 3, 0.01);
      filterRes = constrain(filterRes, 0.01, 3);
      delay.filter(filterFreq, filterRes);
      let delTime = map(mouseY, 0, width, 0.2, 0.01);
      delTime = constrain(delTime, 0.01, 0.2);
      delay.delayTime(delTime);
    }
    function mousePressed() {
      soundFile.play();
    }


### Reverb

Reverb gives depth and perceived space to a sound. Here, noise is processed with reverb. *

*To run this example locally, you will need the p5.sound library a sound file, and a running local server.*

    let sound, reverb;
    function preload() {
      soundFormats('mp3', 'ogg');
      soundFile = loadSound('assets/Damscray_DancingTiger');

// disconnect the default connection
// so that we only hear the sound via the reverb.process
  
      soundFile.disconnect();
    }
    function setup() {
      createCanvas(720, 100);
      background(0);
      reverb = new p5.Reverb();

// sonnects soundFile to reverb with a
// reverbTime of 6 seconds, decayRate of 0.2%

      reverb.process(soundFile, 6, 0.2);

// turn it up!

      reverb.amp(4); 
    }
    function mousePressed() {
      soundFile.play();
    }



### Convolution Reverb

The p5.Convolver can recreate the sound of actual spaces using convolution. Convolution takes an Impulse Response, (the sound of a room reverberating), and uses that to recreate the sound of that space.
Click to play a sound through convolution. Every time you click, the sound is convolved with a different Impulse Response. To hear the Impulse Response itself, press any key.

*To run this example locally, you will need the p5.sound library a sound file, and a running local server. These convolution samples are Creative Commons BY recordinghopkins*

    let sound, env, cVerb, fft;
    let currentIR = 0;
    let rawImpulse;
    function preload() {

// we have included both MP3 and OGG versions of all the impulses/sounds

      soundFormats('ogg', 'mp3');

// create a p5.Convolver

      cVerb = createConvolver('assets/bx-spring');

// add Impulse Responses to cVerb.impulses array, in addition to bx-spring

      cVerb.addImpulse('assets/small-plate');
      cVerb.addImpulse('assets/drum');
      cVerb.addImpulse('assets/beatbox');
      cVerb.addImpulse('assets/concrete-tunnel');

// load a sound that will be processed by the p5.ConvultionReverb

      sound = loadSound('assets/Damscray_DancingTiger');
    }
    function setup() {
      createCanvas(710, 400);
      rawImpulse = loadSound('assets/' + cVerb.impulses[currentIR].name);

// disconnect from master output...
  
      sound.disconnect();
  
// ... and process with cVerb
// so that we only hear the reverb

      cVerb.process(sound);
      fft = new p5.FFT();
    }
    function draw() {
      background(30);
      fill(0, 255, 40);
      let spectrum = fft.analyze();

// Draw every value in the frequencySpectrum array as a rectangle

      noStroke();
      for (let i = 0; i < spectrum.length; i++) {
        let x = map(i, 0, spectrum.length, 0, width);
        let h = -height + map(spectrum[i], 0, 255, height, 0);
        rect(x, height, width / spectrum.length, h);
      }
    }
    function mousePressed() {

// cycle through the array of cVerb.impulses

      currentIR++;
      if (currentIR >= cVerb.impulses.length) {
        currentIR = 0;
      }
      cVerb.toggleImpulse(currentIR);

// play the sound through the impulse

      sound.play();

// display the current Impulse Response name (the filepath)

      println('Convolution Impulse Response: ' + cVerb.impulses[currentIR].name);
      rawImpulse.setPath('assets/' + cVerb.impulses[currentIR].name);
    }

// play the impulse (without convolution)

    function keyPressed() {
      rawImpulse.play();
    }


### Record Save Audio

Record a sound, play it back and save it as a .wav file to the client's computer. We need three objects: a p5.AudioIn (mic / sound source), p5.SoundRecorder (records the sound), and a p5.SoundFile (play back / save).

*To run this example locally, you will need the p5.sound library a sound file, and a running local server.*'

    let mic, recorder, soundFile;
    let state = 0; 

// mousePress will increment from Record, to Stop, to Play

    function setup() {
      createCanvas(400, 400);
      background(200);
      fill(0);
      text('Enable mic and click the mouse to begin recording', 20, 20);

// create an audio in
  
      mic = new p5.AudioIn();

// users must manually enable their browser microphone for recording to work properly!

      mic.start();

// create a sound recorder

      recorder = new p5.SoundRecorder();

// connect the mic to the recorder

      recorder.setInput(mic);

// create an empty sound file that we will use to playback the recording

      soundFile = new p5.SoundFile();
    }
    function mousePressed() {

// use the '.enabled' boolean to make sure user enabled the mic (otherwise we'd record silence)

      if (state === 0 && mic.enabled) {

// Tell recorder to record to a p5.SoundFile which we will use for playback

        recorder.record(soundFile);
        background(255, 0, 0);
        text('Recording now! Click to stop.', 20, 20);
        state++;
      } else if (state === 1) {
        recorder.stop(); 
    
// stop recorder, and send the result to soundFile

        background(0, 255, 0);
        text('Recording stopped. Click to play & save', 20, 20);
        state++;
      } else if (state === 2) {
        soundFile.play(); 

// play the result!

        saveSound(soundFile, 'mySound.wav'); 

// save file

        state++;
      }
    }



### Frequency Modulation

Frequency Modulation is a powerful form of synthesis. In its simplest form, FM involves two oscillators, referred to as the carrier and the modulator. As the modulator's waveform oscillates between some minimum and maximum amplitude value, that momentary value is added to ("modulates") the frequency of the carrier.

The **carrier** is typically set to oscillate at an audible frequency that we perceive as a pitch—in this case, it is a sine wave oscilaltor at 220Hz, equivalent to an "A3" note. The carrier is connected to master output by default (this is the case for all p5.Oscillators).

We will disconnect the **modulator** from master output, and instead connect to the frequency of the carrier: carrier.freq(modulator). This adds the output amplitude of the modulator to the frequency of the carrier.

**Modulation Depth** describes how much the carrier frequency will modulate. It is based on the amplitude of the modulator. The modulator produces a continuous stream of amplitude values that we will add to the carrier frequency. An amplitude of zero means silence, so the modulation will have no effect. An amplitude of 1.0 scales the range of output values between +1.0 and -1.0. That is the standard range for sound that gets sent to your speakers, but in FM we are instead sending the modulator's output to the carrier frequency, where we'd barely notice the +1Hz / -1Hz modulation. So we will typically increase the amplitude ("depth") of the modulator to numbers much higher than what we might send to our speakers.

**Modulation Frequency** is the speed of modulation. When the modulation frequency is lower than 20Hz, we stop hearing its frequency as pitch, and start to hear it as a beating rhythm. For example, try 7.5Hz at a depth of 20 to mimic the "vibrato" effect of an operatic vocalist. The term for this is Low Frequency Oscillator, or LFO. Modulators set to higher frequencies can also produce interesting effects, especially when the frequency has a harmonic relationship to the carrier signal. For example, listen to what happens when the modulator's frequency is half or twice that of the carrier. This is the basis for FM Synthesis, developed by John Chowning in the 1960s, which came to revolutionize synthesis in the 1980s and is often used to synthesize brass and bell-like sounds. *

In this example,

- MouseX controls the modulation depth (the amplitude of the modulator) from -150 to 150. When the modulator's amplitude is set to 0 (in the middle), notice how the modulation has no effect. The greater (the absolute value of) the number, the greater the effect. If the modulator waveform is symetrical like a square [], sine ~ or triangle /\, the negative amplitude will be the same as positive amplitude. But in this example, the modulator is an asymetrical sawtooth wave, shaped like this /. When we multiply it by a negative number, it goes backwards like this \. To best observe the difference, try lowering the frequency.
- MouseY controls the frequency of the modulator from 0 to 112 Hz. Try comparing modulation frequencies below the audible range (which starts around 20hz), and above it, especially in a harmonic relationship to the carrier frequency (which is 220hz, so try half that, 1/3, 1/4 etc...). *

*You will need to include the p5.sound library for this example to work in your own project.*

![IMG_6211](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/7538e985-3878-4dd0-981b-d16a842de370)


    let carrier; 

// this is the oscillator we will hear

    let modulator; 

// this oscillator will modulate the frequency of the carrier

    let analyzer; 

// we'll use this visualize the waveform
// the carrier frequency pre-modulation

    let carrierBaseFreq = 220;

// min/max ranges for modulator

    let modMaxFreq = 112;
    let modMinFreq = 0;
    let modMaxDepth = 150;
    let modMinDepth = -150;
    function setup() {
      let cnv = createCanvas(800, 400);
      noFill();
      carrier = new p5.Oscillator('sine');
      carrier.amp(0); 

// set amplitude

      carrier.freq(carrierBaseFreq); 
  
// set frequency

      carrier.start(); 
  
// start oscillating
// try changing the type to 'square', 'sine' or 'triangle'

      modulator = new p5.Oscillator('sawtooth');
      modulator.start();

// add the modulator's output to modulate the carrier's frequency

      modulator.disconnect();
      carrier.freq(modulator);

// create an FFT to analyze the audio

      analyzer = new p5.FFT();

// fade carrier in/out on mouseover / touch start

      toggleAudio(cnv);
    }
    function draw() {
      background(30);

// map mouseY to modulator freq between a maximum and minimum frequency

      let modFreq = map(mouseY, height, 0, modMinFreq, modMaxFreq);
      modulator.freq(modFreq);

// change the amplitude of the modulator
// negative amp reverses the sawtooth waveform, and sounds percussive

      let modDepth = map(mouseX, 0, width, modMinDepth, modMaxDepth);
      modulator.amp(modDepth);

// analyze the waveform
  
      waveform = analyzer.waveform();

// draw the shape of the waveform

      stroke(255);
      strokeWeight(10);
      beginShape();
      for (let i = 0; i < waveform.length; i++) {
        let x = map(i, 0, waveform.length, 0, width);
        let y = map(waveform[i], -1, 1, -height / 2, height / 2);
        vertex(x, y + height / 2);
      }
      endShape();
      strokeWeight(1);

// add a note about what's happening

      text('Modulator Frequency: ' + modFreq.toFixed(3) + ' Hz', 20, 20);
      text(
        'Modulator Amplitude (Modulation Depth): ' + modDepth.toFixed(3),
        20,
        40
      );
      text(
        'Carrier Frequency (pre-modulation): ' + carrierBaseFreq + ' Hz',
        width / 2,
        20
      );
    }

// helper function to toggle sound

    function toggleAudio(cnv) {
      cnv.mouseOver(function() {
        carrier.amp(1.0, 0.01);
      });
      cnv.touchStarted(function() {
        carrier.amp(1.0, 0.01);
      });
      cnv.mouseOut(function() {
        carrier.amp(0.0, 1.0);
      });
    }



### Amplitude Modulation

Amplitude Modulation involves two oscillators, referred to as the carrier and the modulator, where the modulator controls the carrier's amplitude.
*
The carrier is typically set at an audible frequency (i.e. 440 Hz) and connected to master output by default. The carrier.amp is set to zero because we will have the modulator control its amplitude.
*
The modulator is disconnected from master output. Instead, it is connected to the amplitude of the Carrier, like this: carrier.amp(modulator).
*
In this example...
- MouseX controls the amplitude of the modulator from 0 to 1. When the modulator's amplitude is set to 0, the amplitude modulation has no effect.
*
- MouseY controls the frequency of the modulator from 0 to 20hz. This range is lower frequencies than humans can hear, and we perceive the modulation as a rhythm. This range can simulate effects such as Tremolo. Ring Modulation is a type of Amplitude Modulation where the original carrier signal is not present, and often involves modulation at a faster frequency.
*
*You will need to include the p5.sound library for this example to work in your own project.*

![IMG_6213](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/b3d4747f-3578-453f-bc8d-62fa6b081e8d)

// this is the oscillator we will hear

    let carrier; 

// this oscillator will modulate the amplitude of the carrier

    let modulator;

// we'll visualize the waveform

    let fft; 
    function setup() {
      createCanvas(800, 400);
      noFill();
      background(30); 

// alpha
// connects to master output by default

      carrier = new p5.Oscillator(); 
      carrier.freq(340);
      carrier.amp(0);

// carrier's amp is 0 by default, giving our modulator total control

      carrier.start();
      modulator = new p5.Oscillator('triangle');

// disconnect the modulator from master output
 
      modulator.disconnect();
      modulator.freq(5);
      modulator.amp(1);
      modulator.start();

// Modulate the carrier's amplitude with the modulator
// Optionally, we can scale the signal.

      carrier.amp(modulator.scale(-1, 1, 1, -1));

// create an fft to analyze the audio

      fft = new p5.FFT();
    }
    function draw() {
      background(30, 30, 30, 100); // alpha

// map mouseY to moodulator freq between 0 and 20hz

      let modFreq = map(mouseY, 0, height, 20, 0);
      modulator.freq(modFreq);
      let modAmp = map(mouseX, 0, width, 0, 1);

// fade time of 0.1 for smooth fading

      modulator.amp(modAmp, 0.01); 

// analyze the waveform
  
      waveform = fft.waveform();

// draw the shape of the waveform
  
      drawWaveform();
      drawText(modFreq, modAmp);
    }
    function drawWaveform() {
      stroke(240);
      strokeWeight(4);
      beginShape();
      for (let i = 0; i < waveform.length; i++) {
        let x = map(i, 0, waveform.length, 0, width);
        let y = map(waveform[i], -1, 1, -height / 2, height / 2);
        vertex(x, y + height / 2);
      }
      endShape();
    }
    function drawText(modFreq, modAmp) {
      strokeWeight(1);
      text('Modulator Frequency: ' + modFreq.toFixed(3) + ' Hz', 20, 20);
      text('Modulator Amplitude: ' + modAmp.toFixed(3), 20, 40);
    }



## Hello p5

### Simple Shapes

This examples includes a circle, square, triangle, and a flower.

![image](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/efa0f6a1-8dd2-4f1c-a5ed-19ee40a24281)

    function setup() {

// Create the canvas

      createCanvas(720, 400);
      background(200);

// Set colors

      fill(204, 101, 192, 127);
      stroke(127, 63, 120);

// A rectangle

      rect(40, 120, 120, 40);
  
// An ellipse

      ellipse(240, 240, 80, 80);
  
// A triangle

      triangle(300, 100, 320, 100, 310, 80);

// A design for a simple flower

      translate(580, 200);
      noStroke();
      for (let i = 0; i < 10; i ++) {
        ellipse(0, 30, 20, 80);
        rotate(PI/5);
      }
    }


### Interactivity 1

The circle changes color when you click on it.

![image](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/d138c87d-4f40-42b7-b561-06d8ca460414)


// for red, green, and blue color values

    let r, g, b;
    function setup() {
      createCanvas(720, 400);
// Pick colors randomly

      r = random(255);
      g = random(255);
      b = random(255);
    }
    function draw() {
      background(127);
  
// Draw a circle

      strokeWeight(2);
      stroke(r, g, b);
      fill(r, g, b, 127);
      ellipse(360, 200, 200, 200);
    }

// When the user clicks the mouse

    function mousePressed() {
  
// Check if mouse is inside the circle

      let d = dist(mouseX, mouseY, 360, 200);
      if (d < 100) {
// Pick new random color values

        r = random(255);
        g = random(255);
        b = random(255);
      }
    }



### Interactivity 2

The circle changes color when you move the slider.

![image](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/db605cff-2ee3-4db2-8c00-cceb881edcae)


// A HTML range slider

    let slider;
    function setup() {
      createCanvas(720, 400);
  
// hue, saturation, and brightness

      colorMode(HSB, 255);
  
// slider has a range between 0 and 255 with a starting value of 127

      slider = createSlider(0, 255, 127);
    }
    function draw() {
      background(127);
      strokeWeight(2);

// Set the hue according to the slider

      stroke(slider.value(), 255, 255);
      fill(slider.value(), 255, 255, 127);
      ellipse(360, 200, 200, 200);
    }

### Animation

The circle moves.

![image](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/5fc47584-03ea-4d67-afaf-f51d29c23ddd)

// Where is the circle

    let x, y;
    function setup() {
      createCanvas(720, 400);

// Starts in the middle

      x = width / 2;
      y = height;
    }
    function draw() {
      background(200);
  
// Draw a circle

      stroke(50);
      fill(100);
      ellipse(x, y, 24, 24);
  
// Jiggling randomly on the horizontal axis

      x = x + random(-1, 1);
  
// Moving up at a constant speed

      y = y - 1;
  
// Reset to the bottom

      if (y < 0) {
        y = height;
      }
    }



### Flocking

Demonstration of Craig Reynolds' "Flocking" behavior.
(Rules: Cohesion, Separation, Alignment.)
From natureofcode.com.

![image](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/261cf04d-019d-49bf-9c24-46656bd2198d)


    let boids = [];
    function setup() {
      createCanvas(720, 400);

// Add an initial set of boids into the system

      for (let i = 0; i < 100; i++) {
        boids[i] = new Boid(random(width), random(height));
      }
    }
    function draw() {
      background(51);

// Run all the boids

      for (let i = 0; i < boids.length; i++) {
        boids[i].run(boids);
      }
    }

// Boid class
// Methods for Separation, Cohesion, Alignment added

    class Boid {
      constructor(x, y) {
        this.acceleration = createVector(0, 0);
        this.velocity = p5.Vector.random2D();
        this.position = createVector(x, y);
        this.r = 3.0;
        this.maxspeed = 3;    

// Maximum speed
    
        this.maxforce = 0.05; 

// Maximum steering force
    
      }
      run(boids) {
        this.flock(boids);
        this.update();
        this.borders();
        this.render();
      }
  
// Forces go into acceleration

      applyForce(force) {
        this.acceleration.add(force);
      }
  
// We accumulate a new acceleration each time based on three rules
 
      flock(boids) {

// Separation

        let sep = this.separate(boids); 
    
// Alignment
  
        let ali = this.align(boids);    

// Cohesion

        let coh = this.cohesion(boids); 

// Arbitrarily weight these forces

        sep.mult(2.5);
        ali.mult(1.0);
        coh.mult(1.0);

// Add the force vectors to acceleration
   
        this.applyForce(sep);
        this.applyForce(ali);
        this.applyForce(coh);
      }
  
// Method to update location
  
      update() {

// Update velocity

        this.velocity.add(this.acceleration);/

// Limit speed

        this.velocity.limit(this.maxspeed);
        this.position.add(this.velocity);
    
// Reset acceleration to 0 each cycle

        this.acceleration.mult(0);
      }
  
// A method that calculates and applies a steering force towards a target
// STEER = DESIRED MINUS VELOCITY

      seek(target) {
         let desired = p5.Vector.sub(target, this.position); // A vector pointing from the location to the target
    
// Normalize desired and scale to maximum speed

        desired.normalize();
        desired.mult(this.maxspeed);

// Steering = Desired minus Velocity

        let steer = p5.Vector.sub(desired, this.velocity);
        steer.limit(this.maxforce); // Limit to maximum steering force
        return steer;
      }
  
// Draw boid as a circle

      render() {
        fill(127, 127);
        stroke(200);
        ellipse(this.position.x, this.position.y, 16, 16);
      }
  
// Wraparound

      borders() {
        if (this.position.x < -this.r) this.position.x = width + this.r;
        if (this.position.y < -this.r) this.position.y = height + this.r;
        if (this.position.x > width + this.r) this.position.x = -this.r;
        if (this.position.y > height + this.r) this.position.y = -this.r;
      }
  
// Separation
// Method checks for nearby boids and steers away

      separate(boids) {
        let desiredseparation = 25.0;
        let steer = createVector(0, 0);
        let count = 0;
    
// For every boid in the system, check if it's too close

        for (let i = 0; i < boids.length; i++) {
          let d = p5.Vector.dist(this.position, boids[i].position);
      
// If the distance is greater than 0 and less than an arbitrary amount (0 when you are yourself)
      
          if ((d > 0) && (d < desiredseparation)) {
      
// Calculate vector pointing away from neighbor

            let diff = p5.Vector.sub(this.position, boids[i].position);
            diff.normalize();

// Weight by distance

            diff.div(d); 
            steer.add(diff);
        
// Keep track of how many
        
            count++; 
          }
        }

// Average -- divide by how many

        if (count > 0) {
          steer.div(count);
        }
  
// As long as the vector is greater than 0

        if (steer.mag() > 0) {
    
// Implement Reynolds: Steering = Desired - Velocity

          steer.normalize();
          steer.mult(this.maxspeed);
          steer.sub(this.velocity);
          steer.limit(this.maxforce);
        }
        return steer;
      }
  
// Alignment
// For every nearby boid in the system, calculate the average velocity

      align(boids) {
        let neighbordist = 50;
        let sum = createVector(0, 0);
        let count = 0;
        for (let i = 0; i < boids.length; i++) {
          let d = p5.Vector.dist(this.position, boids[i].position);
          if ((d > 0) && (d < neighbordist)) {
            sum.add(boids[i].velocity);
            count++;
          }
        }
        if (count > 0) {
          sum.div(count);
          sum.normalize();
          sum.mult(this.maxspeed);
          let steer = p5.Vector.sub(sum, this.velocity);
          steer.limit(this.maxforce);
          return steer;
        } else {
          return createVector(0, 0);
        }
      }
  
// Cohesion
// For the average location (i.e. center) of all nearby boids, calculate steering vector towards that location

      cohesion(boids) {
        let neighbordist = 50;
    
 // Start with empty vector to accumulate all locations
    
        let sum = createVector(0, 0);
        let count = 0;
        for (let i = 0; i < boids.length; i++) {
          let d = p5.Vector.dist(this.position, boids[i].position);
          if ((d > 0) && (d < neighbordist)) {

// Add location

            sum.add(boids[i].position); 
            count++;
          }
        }
        if (count > 0) {
          sum.div(count);

// Steer towards the location

          return this.seek(sum); 
        } else {
          return createVector(0, 0);
        }
      }  
    }



### Weather

This example grabs JSON weather data from www.metaweather.com.

![image](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/21072377-e10d-48ff-8cba-cfd2fdd6b877)


// A wind direction vector

    let wind;

// Circle position

    let position;
    function setup() {
      createCanvas(720, 200);

// Request the data from metaweather.com

      let url = 'https://cors-anywhere.herokuapp.com/https://www.metaweather.com/api/location/2459115/';
      loadJSON(url,gotWeather);

// Circle starts in the middle
 
      position = createVector(width/2, height/2);

// wind starts as (0,0)

      wind = createVector();
    }
    function draw() {
      background(200);

 // This section draws an arrow pointing in the direction of wind
 
      push();
      translate(32, height - 32);

// Rotate by the wind's angle

      rotate(wind.heading() + PI/2);
      noStroke();
      fill(255);
      ellipse(0, 0, 48, 48);

      stroke(45, 123, 182);
      strokeWeight(3);
      line(0, -16, 0, 16);

      noStroke();
      fill(45, 123, 182);
      triangle(0, -18, -6, -10, 6, -10);
      pop();
  
// Move in the wind's direction

      position.add(wind);  
      stroke(0);
      fill(51);
      ellipse(position.x, position.y, 16, 16);

      if (position.x > width)  position.x = 0;
      if (position.x < 0)      position.x = width;
      if (position.y > height) position.y = 0;
      if (position.y < 0)      position.y = height;
    }
    function gotWeather(weather) {
      let weather_today = weather.consolidated_weather[0]

// Get the angle (convert to radians)
 
      let angle = radians(Number(weather_today.wind_direction));

// Get the wind speed

      let windmag = Number(weather_today.wind_speed);
  
// Display as HTML elements

      let temperatureDiv = createDiv(floor(weather_today.the_temp) + '&deg;C');
      let windDiv = createDiv("WIND " + windmag + " <small>MPH</small>");
  
// Make a vector

      wind = p5.Vector.fromAngle(angle);
    }



### Drawing

Generative painting program.

![image](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/9ace2fbc-0f75-4109-8766-183a12755990)


// All the paths

    let paths = [];

// Are we painting?

    let painting = false;

// How long until the next circle

    let next = 0;

// Where are we now and where were we?

    let current;
    let previous;

    function setup() {
      createCanvas(720, 400);
      current = createVector(0,0);
      previous = createVector(0,0);
    };

    function draw() {
      background(200);
  
// If it's time for a new point

      if (millis() > next && painting) {

// Grab mouse position      

        current.x = mouseX;
        current.y = mouseY;

// New particle's force is based on mouse movement

        let force = p5.Vector.sub(current, previous);
        force.mult(0.05);

// Add new particle

        paths[paths.length - 1].add(current, force);
    
// Schedule next circle

        next = millis() + random(100);

// Store mouse values

        previous.x = current.x;
        previous.y = current.y;
      }

// Draw all paths

      for( let i = 0; i < paths.length; i++) {
        paths[i].update();
        paths[i].display();
      }
    }

// Start it up

    function mousePressed() {
      next = 0;
      painting = true;
      previous.x = mouseX;
      previous.y = mouseY;
      paths.push(new Path());
    }

// Stop

    function mouseReleased() {
      painting = false;
    }

// A Path is a list of particles

    class Path {
      constructor() {
        this.particles = [];
        this.hue = random(100);
      }
      add(position, force) {

// Add a new particle with a position, force, and hue

        this.particles.push(new Particle(position, force, this.hue));
      }
  
// Display plath
 
      update() {  
        for (let i = 0; i < this.particles.length; i++) {
          this.particles[i].update();
        }
      }  
  
// Display plath

      display() {    

// Loop through backwards
    
        for (let i = this.particles.length - 1; i >= 0; i--) {

// If we shold remove it

          if (this.particles[i].lifespan <= 0) {
            this.particles.splice(i, 1);
      
// Otherwise, display it

          } else {
            this.particles[i].display(this.particles[i+1]);
          }
        }  
      }  
    }

// Particles along the path

    class Particle {
      constructor(position, force, hue) {
        this.position = createVector(position.x, position.y);
        this.velocity = createVector(force.x, force.y);
        this.drag = 0.95;
        this.lifespan = 255;
      }
      update() {

// Move it

        this.position.add(this.velocity);

// Slow it down

        this.velocity.mult(this.drag);

// Fade it out

        this.lifespan--;
      }

// Draw particle and connect it with a line
// Draw a line to another
  
      display(other) {
        stroke(0, this.lifespan);
        fill(0, this.lifespan/2);    
        ellipse(this.position.x,this.position.y, 8, 8);    

// If we need to draw a line

        if (other) {
          line(this.position.x, this.position.y, other.position.x, other.position.y);
        }
      }
    }


### Song

Play a song. You will need to include the p5.sound library for this example to work in your own project.

![image](https://github.com/SC36-11-1/SC36-11-1/assets/133059820/9317ec9d-b5ff-48f6-b763-f8135fe8d4d5)

// The midi notes of a scale

    let notes = [ 60, 62, 64, 65, 67, 69, 71];

// For automatically playing the song

    let index = 0;
    let song = [
      { note: 4, duration: 400, display: "D" },
      { note: 0, duration: 200, display: "G" },
      { note: 1, duration: 200, display: "A" },
      { note: 2, duration: 200, display: "B" },
      { note: 3, duration: 200, display: "C" },
      { note: 4, duration: 400, display: "D" },
      { note: 0, duration: 400, display: "G" },
      { note: 0, duration: 400, display: "G" }
    ];
    let trigger = 0;
    let autoplay = false;
    let osc;

    function setup() {
      createCanvas(720, 400);
      let div = createDiv("Click to play notes or ")
      div.id("instructions");
      let button = createButton("play song automatically.");
      button.parent("instructions");

// Trigger automatically playing

      button.mousePressed(function() {
        if (!autoplay) {
          index = 0;
          autoplay = true;
        }
      });

// A triangle oscillator

      osc = new p5.TriOsc();
  
// Start silent

      osc.start();
      osc.amp(0);
    }

// A function to play a note

    function playNote(note, duration) {
      osc.freq(midiToFreq(note));

// Fade it in

      osc.fade(0.5,0.2);

// If we sest a duration, fade it out

      if (duration) {
        setTimeout(function() {
          osc.fade(0,0.2);
        }, duration-50);
      }
    }
    function draw() {

// If we are autoplaying and it's time for the next note
  
      if (autoplay && millis() > trigger){
        playNote(notes[song[index].note], song[index].duration);
        trigger = millis() + song[index].duration;

// Move to the next note

        index ++;

// We're at the end, stop autoplaying.

      } else if (index >= song.length) {
        autoplay = false;
      }


// Draw a keyboard
// The width for each key

      let w = width / notes.length;
      for (let i = 0; i < notes.length; i++) {
        let x = i * w;

// If the mouse is over the key

        if (mouseX > x && mouseX < x + w && mouseY < height) {

// If we're clicking

          if (mouseIsPressed) {
            fill(100,255,200);
      
// Or just rolling over

          } else {
            fill(127);
          }
        } else {
          fill(200);
        }

// Or if we're playing the song, let's highlight it too
       
        if (autoplay && i === song[index-1].note) {
          fill(100,255,200);
        }

// Draw the key
        rect(x, 0, w-1, height-1);
      }
    }

// When we click

    function mousePressed(event) {
      if(event.button == 0 && event.clientX < width && event.clientY < height) {

// Map mouse to the key index
   
        let key = floor(map(mouseX, 0, width, 0, notes.length));
        playNote(notes[key]);
      }
    }

// Fade it out when we release

    function mouseReleased() {
      osc.fade(0,0.5);
    }















