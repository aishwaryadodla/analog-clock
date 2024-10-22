# analog-clock
index.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta http-equiv="X-UA-Compatible" content="IE=edge" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <link rel="stylesheet" href="style.css" />
  <title>Analog and Digital Clock</title>
</head>
<body>
  <div class="container">
    <div class="clock">
      <div style="--clr: #ff3d58; --h: 74px" id="hour" class="hand">
        <i></i>
      </div>
      <div style="--clr: #00a6ff; --h: 84px" id="min" class="hand">
        <i></i>
      </div>
      <div style="--clr: #ffffff; --h: 90px" id="sec" class="hand">
        <i></i>
      </div>
        <!-- <span style="--i: 1"><b>1</b></span>
        <span style="--i: 2"><b>2</b></span> -->
      <span style="--i: 3"><b>3</b></span>
      <!-- <span style="--i: 4"><b>4</b></span>
      <span style="--i: 5"><b>5</b></span> -->
      <span style="--i: 6"><b>6</b></span>
      <!-- <span style="--i: 7"><b>7</b></span>
      <span style="--i: 8"><b>8</b></span> -->
      <span style="--i: 9"><b>9</b></span>
      <!-- <span style="--i: 10"><b>10</b></span>
      <span style="--i: 11"><b>11</b></span> -->
      <span style="--i: 12"><b>12</b></span>
    </div>
    <div class="digital-clock">
        <span id="digital-hour">00</span>:
        <span id="digital-minute">00</span>:
        <span id="digital-second">00</span>
      </div>
    
  </div>
  <script src="script.js"></script>
</body>
</html>

#styles.css
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: sans-serif;
  color: #ffffff;
}

body{
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background-color: #212121;
}

.container{
  position: relative;
}

.clock{
  width: 300px;
  height: 300px;
  border-radius: 50%;
  background-color: rgba(255, 255, 255, 0.1);
  border: 2px solid rgba(255, 255, 255, 0.25);
  box-shadow: 0px 0px 30px rgba(0, 0, 0, 0.9);
  display: flex;
  justify-content: center;
  align-items: center;
}

.clock span{
  position: absolute;
  transform: rotate(calc(30deg * var(--i))); 
  inset: 12px;
  text-align: center;
}

.clock span b{
  transform: rotate(calc(-30deg * var(--i)));
  display: inline-block;
  font-size: 20px;
}

.clock::before{
  content: '';
  position: absolute;
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background-color: #fff;
  z-index: 2;
}

.hand{
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: flex-end;
}
.hand i{
  position: absolute;
  background-color: var(--clr);
  width: 4px;
  height: var(--h);
  border-radius: 8px;
}

.digital-clock {
  font-size: 10px;
  margin-top: auto; /* Moves the digital clock to the bottom */
  text-align:center;

}

#script.js
let hr = document.getElementById('hour');
let min = document.getElementById('min');
let sec = document.getElementById('sec');
let digitalHour = document.getElementById('digital-hour');
let digitalMinute = document.getElementById('digital-minute');
let digitalSecond = document.getElementById('digital-second');

function displayTime(){
    let date = new Date();

    // Getting hour, mins, secs from date
    let hh = date.getHours();
    let mm = date.getMinutes();
    let ss = date.getSeconds();

    let hRotation = 30*hh + mm/2;
    let mRotation = 6*mm;
    let sRotation = 6*ss;

    hr.style.transform = `rotate(${hRotation}deg)`;
    min.style.transform = `rotate(${mRotation}deg)`;
    sec.style.transform = `rotate(${sRotation}deg)`;
    
    // Digital clock display
  digitalHour.textContent = (hh < 10) ? `0${hh}` : hh;
  digitalMinute.textContent = (mm < 10) ? `0${mm}` : mm;
  digitalSecond.textContent = (ss < 10) ? `0${ss}` : ss;
}

setInterval(displayTime, 1000);



