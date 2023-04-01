# -let points = [[-14, -14], [-14, 14], [14,14],[14,-14],[-12, -12], [-12, 12], [12,12],[12,-12],[-11, -11], [-11, 11], [11,11],[11,-11],[-10, -10], [-10, 10], [10,10],[10,-10],[-9, -9], [-9, 9], [9,9],[9,-9]]; //list資料，
let ctx;
function setup() {
	//基礎設定
	background(100);
	ctx = canvas.getContext('2d');
	ctx.lineWidth = 1000;
	ctx.lineCap = 'round'

createCanvas(windowWidth, windowHeight); //設定一個畫布，寬為整個視窗的寬度windowWidth，高度為整個視窗的高度windowHeight
//把points 內的值都*50

for (let i = 0; i < points.length; i++) {
for (let j = 0; j < points[i].length; j++) {
points[i][j] = points[i][j] * 20;
}
}
}

function draw() {

	gradientLine(ctx, 400, 20, 200, 400, 'brown', 'orange')

background(255);


// scale(50)
//translate(width/2, height/2); //原本原點在左上角，利用這指令把原點放到視窗的中心
	 textSize(35)  //文字大小
  fill(0, 102, 153);  //設定顏色
  text("教科系",-50+mouseX,0+mouseY)  //顯示文字

for (let i = 0; i < points.length-1; i++) {
line(mouseX-points[i][0], mouseY-points[i][1], mouseX-points[i+1][0], mouseY-points[i+1][1]);
  }
  line(mouseX-points[points.length-1][0], mouseY-points[points.length-1][1], mouseX-points[0][0], mouseY-points[0][1]); //把最後一點與第一點的連線
}
function gradientLine(ctx, x1, y1, x2, y2, c1, c2) {
  const gradient = ctx.createLinearGradient(x1, y1, x2, y2);
  gradient.addColorStop(0, c1);
  gradient.addColorStop(1, c2);
  ctx.strokeStyle = gradient;

  ctx.beginPath();
  ctx.moveTo(x1, y1);
  ctx.lineTo(x2, y2);
  ctx.stroke();
	}
