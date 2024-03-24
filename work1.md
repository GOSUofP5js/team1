# 캐릭터 만들기 및 크기변경 및 회전

## 코드

```

// 국립안동대학교 컴퓨터공학과 20210817 신현진

let angle = 0;
let t1 = 0;
let handDirection = 1; // 오른팔의 초기 흔들림 방향 (1: 오른쪽으로 흔들림, -1: 왼쪽으로 흔들림)
let characterX1 = 550; // 캐릭터의 x 좌표
let characterY1 = 400; // 캐릭터의 y 좌표

let characterX = 100;
let characterY = 532;
let angleA = 0; // 오른팔의 각도
let angleB = 0; // 왼팔의도각도
let eyeSize = 30; //
let pupilSize = 10;


function setup() {
  createCanvas(1000,1000);
  

  
  
}

function draw(){
  background('#8E98F0');

  push();
    textSize(100);
    text('zㅣ존 1팀',350,200);
  pop();
  
  push()
    textSize(30)
    text('zㅣ존 1팀 조장 20171111 캡틴 김종준', 450, 300);
  pop()
  
  push()
    textSize(30)
    text('zㅣ존 1팀 20210818 포대장 안현수', 450, 350);
  pop()
  
  push()
    textSize(30)
    text('zㅣ존 1팀 20210817 보병사수 신현진', 450, 400);
  pop()
  
  
  // 캐릭터를 특정 위치에 그리기
  push();
    angleMode(RADIANS);
    drawCharacter(characterX1, characterY1);
  pop();
  
  push();
    angleMode(DEGREES);
    translate(500,500)
    pikachudraw();
  pop();
  
  push();
    angleMode(RADIANS);
    translate(0, -100);
    drawSpongeBob(characterX,characterY);
  pop();
}

function drawCharacter(x, y) {
  push();
    fill('#F0CCB9');    // 얼굴
    rect(x + 170, y + 90, 50, 50)

    fill(0,0,0);         // 눈
    rect(x + 177, y + 100, 10, 10)
    rect(x + 202, y + 100, 10, 10)

    fill('white');      // 눈동자
    rect(x + 179, y + 101, 5, 5)
    rect(x + 204, y + 101, 5, 5)

    push();             // 모자
    fill('black');
    rect(x + 165, y + 80, 60, 10);
    rect(x + 175, y + 50, 40, 30);
    pop();

    push();
    fill('white');      //몸통
    rect(x + 170, y + 140, 50, 80); 
    pop();

    line(x + 200, y + 150, x + 200, y + 220) // 상의선 겹쳐서 라인이 생기는 것을 표현

    line(x + 170, y + 140, x + 190, y + 150) //상의 카라 표현
    line(x + 190, y + 150, x + 195, y + 140)

    line(x + 220, y + 140, x + 200, y + 150)
    line(x + 200, y + 150, x + 195, y + 140) 

    circle(x + 195, y + 150, 5); // 단추들
    circle(x + 195, y + 170, 5);
    circle(x + 195, y + 190, 5);
    circle(x + 195, y + 210, 5);

    push();                // 정장상의
    fill('black');
    rect(x + 170, y + 140, 15, 80);  
    rect(x + 205, y + 140, 15, 80);  
    pop();

    push();                // 왼팔
    fill('black')
    rect(x + 145, y + 140, 25, 80); 
    pop();

    push();
    fill('black')
    translate(x + 220, y + 140); // 오른팔 시작점으로 이동
    scale(1, -1); // y축 방향으로 반전
    rotate(radians(angle)); // 오른팔을 좌우로 흔들기 위한 회전
    rect(0, 0, 25, 80); // 오른팔
    pop();

    angle += handDirection * 0.5; // 오른팔의 회전 각도 조절

    // 흔들리는 각도 범위 설정
    if (angle > 30 || angle < -30) {
      handDirection *= -1;
    }

    push();
    fill('black');
    rect(x + 170, y + 220, 25, 80); // 왼다리
    rect(x + 195, y + 220, 25, 80); // 오른다리
    pop();

    push();
    translate(x + 100, y + 50); // quad를 원래 위치로 이동
    scale(sin(t1=t1+0.05)+0.5); // 크기변환 scale
    fill('yellow');
    noStroke();    // 선 없애기
    quad(0, -15, 15, 0, 0, 15, -15, 0); //노란색 반짝이
    pop(); 


    push();
    translate(x + 280, y + 200); // quad를 원래 위치로 이동
    scale(sin(t1=t1+0.05)+0.5); // 크기변환 scale
    fill('yellow');
    noStroke();
    quad(0, -15, 15, 0, 0, 15, -15, 0);
    pop(); 
  push();
}


// 국립안동대학교 컴퓨터공학과 20171111 김종준

function pikachudraw() {
  push();
    ellipseMode(CENTER);

    // 피카츄의 머리
    fill(255, 217, 36);
    noStroke();
    // 머리 윗부분
    ellipse(250, 250, 220, 180);
    // 머리 아랫부분
    ellipse(250, 300, 230, 170);

    push();
    stroke(0);
    // 오른쪽 뺨
    fill(240, 60, 35);
    translate(340, 315);
    rotate(20);
    ellipse(0, 0, 45, 60);
    pop();

    push();
    stroke(0);
    //왼쪽 뺨
    fill(240, 60, 35);
    translate(160, 315);
    rotate(-20);
    ellipse(0, 0, 45, 60);

    pop();


    //눈 검은부분
    //오른쪽 검은 눈
    fill(0);
    ellipse(310, 250, 40, 40);
    //왼쪽 검은 눈
    ellipse(190, 250, 40, 40);

    //눈 하얀부분
    fill(255);
    stroke(0);
    //오른쪽 하얀 눈
    ellipse(305, 245, 20, 20);
    //왼쪽 하얀 눈
    ellipse(195, 245, 20, 20);

    // 코
    fill(0);
    ellipse(250, 270, 10, 5);

    // 입
    stroke(0,0,0);
    strokeWeight(3);
    noFill();
    //오른쪽 부분
    bezier(250, 300, 270, 310, 280, 315, 290, 300);
    //왼쪽 부분 
    bezier(250, 300, 230, 310, 220, 315, 210, 300);



    push();
    //왼쪽 귀
    fill(255, 217, 36);
    noStroke();
    translate(170, 110);
    rotate(-35);
    ellipse(-40, 0, 50, 150);
    //오른쪽 귀 
    translate(-170, -110);
    translate(330, 110);
    rotate(35);
    rotate(35);
    ellipse(110, 60, 50, 150);
    pop();

    push();
     //귀 검은부분

    //귀 검은부분 왼쪽
    fill('black')
    noStroke();
    translate(170, 110);
    rotate(-35);
    ellipse(-40,-55,30,40);
    //귀 검은부분 오른쪽
    fill('black')
    translate(-170, -110);
    translate(330, 110);
    rotate(35);
    rotate(35);
    ellipse(110,5,30,40);
    pop();

    push();
    //몸통
    fill(255, 217, 36);
    noStroke();
    ellipse(250, 480, 200, 250);
    pop();

    push();
    //팔
    fill(255, 217, 36);
    noStroke();
    rect(120, 380, 50, 90, 20);
    rect(330, 380, 50, 90, 20);
    pop(); 
  pop();
  
}



// 국립안동대학교 컴퓨터공학과 20210818 안현수

function drawSpongeBob(x,y) {

  scale(1.2);

 

  fill(255,255,0);// 오른팔

  push();

  translate(x + 285, y + 195); // 팔 기준점을 오른쪽 어깨에 맞춤

  rotate(radians(sin(angleA) * 30)); // 각도를 sin 함수를 통해 변화시킴

  rect(0,0,50,10); //

  ellipse(40,-5,10,30); // 오른팔 손가락

  ellipse(55,0,30,10);

  ellipse(55,7,30,10);

  ellipse(55,14,30,10);

  noStroke();

  ellipse(40,6,20,15);

  pop();

 

  fill(255,255,255);//오른팔 토시

  rect(x+250,y+180,40,30);

 

  fill(255,255,0);// 왼팔

  push();fill(255, 255, 0);// 왼팔

  push();

  scale(-1,1);

  translate(-(x + 20), y + 195); // 팔 기준점을 왼쪽 어깨에 맞춤

  rotate(radians(sin(angleB) * -30)); // 오른손과 반대 방향으로 각도 변화

  rect(0, 0, 50, 10); // 팔

  ellipse(40,-5,10,30); // 손가락

  ellipse(55,0,30,10);

  ellipse(55,7,30,10);

  ellipse(55,14,30,10);

  noStroke();

  ellipse(40,6,20,15);

  pop();

 

  fill(255,255,255); //왼팔 토시

  rect(x+10,y+180,40,30);

 

  fill(255, 255, 0); //머리 외곽

  ellipse(x+65,y+55,30,30);

  ellipse(x+95,y+55,30,30);

  ellipse(x+125,y+55,30,30);

  ellipse(x+155,y+55,30,30);

  ellipse(x+185,y+55,30,30);

  ellipse(x+215,y+55,30,30);

  ellipse(x+240,y+55,20,20);

  ellipse(x+55,y+65,30,30);

  ellipse(x+55,y+95,30,30);

  ellipse(x+55,y+125,30,30);

  ellipse(x+55,y+155,30,30);

  ellipse(x+55,y+185,30,30);

  ellipse(x+55,y+215,30,30);

  ellipse(x+245,y+65,30,30);

  ellipse(x+245,y+95,30,30);

  ellipse(x+245,y+125,30,30);

  ellipse(x+245,y+155,30,30);  

  ellipse(x+245,y+185,30,30);

  ellipse(x+245,y+215,30,30);

 

  push();

  noStroke();

  fill(255, 255, 0); //머리

  rect(x+50,y + 50,200,200);

  pop();

 

  push();

  noStroke();

  fill(0); // 스펀지 구멍

  ellipse(x+65,y+70,30,30);

  ellipse(x+240,y+70,20,20);

  ellipse(x+100,y+90,30,30);

  ellipse(x+65,y+200,10,10);

  ellipse(x+130,y+220,30,30);

  ellipse(x+200,y+190,30,30);

  ellipse(x+220,y+120,30,30);

  ellipse(x+80,y+120,20,20);

  pop();

 

 

  fill(255,255,255); // 눈매

  ellipse(x+180,y+120,60,60);

  ellipse(x+120,y+120,60,60);

 

  stroke(0);

  strokeWeight(3);

  line(x+170,y+90,x+160,y+70); // 오른쪽 눈썹

  line(x+180,y+90,x+180,y+70);

  line(x+190,y+90,x+200,y+70);

  line(x+110,y+90,x+100,y+70); // 왼쪽 눈썹

  line(x+120,y+90,x+120,y+70);

  line(x+130,y+90,x+140,y+70);  

   

  push();

  fill(0,0,255); // 눈

  ellipse(x+170,y+120,eyeSize,eyeSize);

  ellipse(x+130,y+120,eyeSize,eyeSize);

  pop();

 

  fill(0); // 눈알

  ellipse(x+170,y+120,pupilSize,pupilSize);

  ellipse(x+130,y+120,pupilSize,pupilSize);

 

  fill(255,255,0); //코

  ellipse(x+150,y+150,30,30)

 

  fill(255,255,0) // 보조개

  ellipse(x+80,y+160,20,20);

  ellipse(x+220,y+160,20,20);

 

  push();

  fill(255,0,0) // 입

  arc(x+150,y+160,150,60,0,PI);

  pop();

 

  push();

  noStroke(); // 입

  fill(255,255,0);

  ellipse(x+150,y+160,150,15);

  pop();

 

  push();

  strokeWeight(2);

  fill(255,255,255); //이빨

  rect(x+130,y+167,18,30);

  rect(x+148,y+167,18,30);

  pop();

 

  fill(255,255,255); // 상의

  rect(x+50,y + 230,200,50)

  // 카라

  triangle(x+100,y+230,x+140,y+230,x+130,y+260)

  triangle(x+160,y+230,x+200,y+230,x+170,y+260)

 

  fill(255,0,0); // 넥타이

  ellipse(x+150,y+240,30,30)

 

  fill(255,255,0); // 왼쪽 다리

  rect(x+90, y+330,20,40)

 

  fill(0); // 왼쪽 신발

  rect(x+70, y+ 370, 40,13)

  ellipse(x+70, y+373, 20,20)

 

  fill(255,255,255); // 왼쪽 양말

  rect(x+90, y+350,20,20)

 

  fill('brown'); // 왼쪽 바지

  rect(x+80, y+300,40,35)

 

  fill(255,255,0); // 오른쪽 다리

  rect(x+190, y+330,20,40)

 

  fill(0); // 오른쪽 신발

  rect(x+190, y+ 370, 40,13)

  ellipse(x+230, y+373, 20,20)

 

  fill(255,255,255); // 오른쪽 양말

  rect(x+190, y+350,20,20)

 

  fill('brown'); // 오른쪽 바지

  rect(x+180, y+300,40,35)

 

  fill('brown');

  rect(x+50,y + 270,200,30) // 바지

 

  fill('black'); //

  rect(x+55,y + 280,30,15)

  rect(x+95,y + 280,30,15)

  rect(x+135,y + 280,30,15)

  rect(x+175,y + 280,30,15)

  rect(x+215,y + 280,30,15)

 

  // 오른팔 각도 변화

  angleA += 0.1;

  angleB += 0.1;

 

  eyeSize = sin(frameCount * 0.05) * 10 + 20; // 눈의 크기가 20에서 40 사이로 커졌다 작아집니다

pupilSize = sin(frameCount * 0.05) * 6 + 10; // 눈알의 크기가 4에서 16 사이로 커졌다



}


```

----------

## 소감

**20171111 김종준 (귀여운 피카츄) :** p5.js를 사용하여 피카츄를 그리기 위해서 Chatgpt나 뤼튼등의 GPT모델의 도움을 좀 받았습니다. 코드를 통해 그림을 그리고 수정하는 과정에서 문제 해결 능력이 향상되었고, 원하는 결과물을 얻기 위해 여러 기술을 시도해보는 과정에서 성취감을 느낄 수 있었습니다. 또한, 코드로 그림을 만드는것은 포토샵 등으로 작품을 평소에 만들던 저에게는 새로운 예술 형태에 도전하는 기회가 되었습니다. p5.js의 여러 소스와 Example이 존재하고 그것을 참고하는것 또한 너무 즐거운 일이었습니다.

**20210817 신현진 (정장의 사나이) :** 이번과제 2D 캐릭터 만들면서 많은것들을 추가하고 싶은 욕심이 많이 생겼습니다. 그래서 이것저것 추가하다 보니 원인을 알수없는 오류로 인한 스트레스를 받기도했고 코드를 만드는데 거의 하루를 사용한거 같았습니다. 하지만 이러한 원인들을 스스로 해결하면서 쾌감을 느꼈고 자신이 성장하고 있음을 다시한번 느끼게된 계기가 된거같습니다. 지금은 비록 이러한 간단한 캐릭터를 만드는데도 하루를 사용했지만 p5.js에 있는 쇼케이스 탭에서의 여러 작품처럼 훌륭한 작품하나를 만들수 있을때까지 열심히 하겠습니다. 감사합니다.

**20210818 안현수 (네모바지 스폰지밥) :** 이번에 복학하여 처음 팀 프로젝트를 진행하게 되었습니다. 처음에는 걱정이 앞섰습니다. 주변에서 팀 프로젝트는 혼자만 하면 되는 것이 아닌 팀원들과 함께 작업을 마무리해야하기 때문에 본인만 잘하면 되는게 아니라고 들었기 때문입니다. 하지만 그 또한 사회에서 필요한 능력이라고 생각합니다. 학교에 오기 전 회사생활을 해본 경험에 의하면 회사에서 또한 혼자 일 하는 것이 아닌 팀원들과의 협업으로 일 하는 경우가 많기 때문에 서로 맞춰서 일 하는 것이 개인의 능력보다 중요한 능력이 된다고 생각합니다. 때문에 좋은 경험을 하게 해주셔서 감사하게 생각합니다.  




