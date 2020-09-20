# Natalia Sheshko
### Contact information
**Tel**: +375291425326

**Email**: sharlottesometimes@yandex.by

**Address**: Belarus, Minsk, Yakubova st., 16-96

----
### Summary 
I have economic education with a specialization in finance and banking. After graduation from the university I have been working in a commercial bank, but soon realised that it was not my thing. I've got carried away with programming recently and studing now to become a front-end developer. I decided to learn javascript because it's very common and has wide range of use. My near-term goal is to complete "Java-script/Front-end" course. Then I hope to find a job at it-company as javascript developer and advance my skills further.  

----
### Skills  
- html
- css
- javascript
- git 
____
### Code examples  
```
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <title>Прыгающий мяч</title>
</head>

<body>
<canvas id="canvas" width="500" height="300"></canvas>
<script>

    let Ball = function () {
        this.x = 100;
        this.y = 100;
        this.xSpeed = Math.random() * 10 - 5;
        this.ySpeed = Math.random() * 10 - 5;
        this.color = pickRandomWord();
    };

    let pickRandomWord = function () {
        let colors = ["Red", "Orange", "Yellow", "Green", "Blue", "Purple"];
        let rn = Math.floor(Math.random() * colors.length);
        return colors[rn]
    }

    let circle = function (x, y, radius, fillCircle, color) {
        ctx.fillStyle = color;
        ctx.beginPath();
        ctx.arc(x, y, radius, 0, Math.PI * 2, false);
        if (fillCircle) {
            ctx.fill();
        } else {
            ctx.stroke();
        }
    };

    Ball.prototype.draw = function () {
        circle(this.x, this.y, 3, true, this.color);
    };

    Ball.prototype.move = function () {
        this.x += this.xSpeed;
        this.y += this.ySpeed;
    };

    Ball.prototype.checkCollision = function (width, height) {
        if (this.x < 0 || this.x > width) {
            this.xSpeed = -this.xSpeed;
        }
        if (this.y < 0 || this.y > height) {
            this.ySpeed = -this.ySpeed;
        }
    };

    let canvas = document.getElementById("canvas");
    let width = canvas.width;
    let height = canvas.height;
    let ctx = canvas.getContext("2d");


    let drawBall = function (ball) {
        ball.draw();
        ball.move();
        ball.checkCollision(width, height);
    }
    
    let balls = [];
    for (let i = 0; i < 12; i++) {
        balls.push(new Ball());
    }
    setInterval(function () {
        ctx.clearRect(0, 0, width, height);
        for (let i = 0; i < 12; i++) {
            drawBall(balls[i])
        }
        ctx.strokeRect(0, 0, width, height);
    }, 30);

</script>
</body>
</html>
```