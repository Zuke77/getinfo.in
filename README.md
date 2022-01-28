<html>
<head>

	<style type="text/css">
		@import url("https://fonts.googleapis.com/css?family=Ubuntu");

* {
  margin: 0;
  padding: 0;
}

body {
  font-family: "Ubuntu", sans-serif;
}

.wrapper {
  background: url("https://1.bp.blogspot.com/-grwQQFTZtLw/YTL_7cZ4UMI/AAAAAAAAAGo/pKR4Jcs4y949yYONNrui88N74fgSDCD-QCLcBGAsYHQ/s0/hack-813290_1280.jpg") no-repeat center;
  background-size: cover;
  width: 100%;
  height: 100vh;
}

.nav-bar {
  list-style: none;
  width: 300px;
  height: 45px;
  padding: 10px;
}

.nav-bar li {
  width: 30%;
  margin: 0 2px;
  float: left;
  text-align: center;
  height: 100%;
  line-height: 45px;
  color: #fff;
  font-weight: bold;
  font-size: 14px;
  letter-spacing: 1px;
  cursor: pointer;
  border-radius: 20px;
  transition: all 0.5s ease;
}

.nav-bar li:hover {
  color: #fff;
  background:  #3333ff
;
}

.nav-bar li.active {
  color: #fff;
  background: #3333ff;
}

.content{
  text-align: center;
  position: relative;
  top: 40%;
  transform: translateY(-50%);
  text-transform: uppercase;
  color: #fff;
  letter-spacing: 2px;
}

.share{
  position: absolute;
  right: 10px;
  bottom: 10px;
  list-style: none;
}

.share li{
  padding: 15px;
  text-align: center;
  margin: 5px 0;
  border-radius: 50%;
  color: #fff;
  font-size: 18px;
  cursor: pointer;
  background:  #6666ff
;
}

.share li:before{
  content: attr(data-text);
  position: absolute;
  right: 65px;
  text-transform: uppercase;
  font-size: 14px;
  opacity: 0;
  transition: all 0.5s ease;
}

.share li:hover:before{
  opacity: 1;
}



/* youtube link */
.youtube{
  position: fixed;
  bottom: 10px;
  left: 10px;
  width: 160px;
  text-align: center;
  padding: 15px 10px;
  background: ;
  border-radius: 5px;
}

.youtube a{
  text-decoration: none;
  color: #fff;
  text-transform: capitalize;
  letter-spacing: 1px;
}


@import url('https://fonts.googleapis.com/css?family=Raleway:900&display=swap');

body {
  margin: 0px;
}

#container {
  /* Center the text in the viewport. */
  position: absolute;
  margin: auto;
  width: 100vw;
  height: 80pt;
  top: 0;
  bottom: 0;
  
  /* This filter is a lot of the magic, try commenting it out to see how the morphing works! */
  filter: url(#threshold) blur(0.6px);
}

/* Your average text styling */
#text1, #text2 {
  position: absolute;
  width: 100%;
  display: inline-block;
  color: #fff;
  font-family: 'Raleway', sans-serif;
  font-size: 80pt;
  
  text-align: center;
  
  user-select: none;
}
	</style>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<title></title>
</head>
<body>
 <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css">

<div class="wrapper">
    <ul class="nav-bar">
      <li class="active">GoGetInfo</li>
      <li class="hide">Blog</li>
      <li>About</li>
    </ul>
    


<div id="container">
  <span id="text1"></span>
  <span id="text2"></span>
</div>

<svg id="filters">
  <defs>
    <filter id="threshold">
      
      <feColorMatrix in="SourceGraphic"
          type="matrix"
          values="1 0 0 0 0
                  0 1 0 0 0
                  0 0 1 0 0
                  0 0 0 255 -140" />
    </filter>
  </defs>
</svg>








    <ul class="share">
      <li data-text="instagram"><i class="fa fa-instagram" aria-hidden="true"></i></li>
      <li data-text="youtube"><i class="fa fa-youtube" aria-hidden="true"></i></li>
      <li data-text="codepen"><i class="fa fa-codepen" aria-hidden="true"></i></li>
    </ul>
  
</div>

<!-- By Nitesh -->
<div class="youtube">
  <a href="#" target="_blank">By Nitesh</a>
</div>


<script type="text/javascript">
	  

const elts = {
  text1: document.getElementById("text1"),
  text2: document.getElementById("text2")
};

const texts = [
  "All",
  "Technology",
  "Info",
  "In",
  "One",
  "Place" 
];


const morphTime = 1;
const cooldownTime = 0.25;

let textIndex = texts.length - 1;
let time = new Date();
let morph = 0;
let cooldown = cooldownTime;

elts.text1.textContent = texts[textIndex % texts.length];
elts.text2.textContent = texts[(textIndex + 1) % texts.length];

function doMorph() {
  morph -= cooldown;
  cooldown = 0;
  
  let fraction = morph / morphTime;
  
  if (fraction > 1) {
    cooldown = cooldownTime;
    fraction = 1;
  }
  
  setMorph(fraction);
}


function setMorph(fraction) {
  // fraction = Math.cos(fraction * Math.PI) / -2 + .5;
  
  elts.text2.style.filter = `blur(${Math.min(8 / fraction - 8, 100)}px)`;
  elts.text2.style.opacity = `${Math.pow(fraction, 0.4) * 100}%`;
  
  fraction = 1 - fraction;
  elts.text1.style.filter = `blur(${Math.min(8 / fraction - 8, 100)}px)`;
  elts.text1.style.opacity = `${Math.pow(fraction, 0.4) * 100}%`;
  
  elts.text1.textContent = texts[textIndex % texts.length];
  elts.text2.textContent = texts[(textIndex + 1) % texts.length];
}

function doCooldown() {
  morph = 0;
  
  elts.text2.style.filter = "";
  elts.text2.style.opacity = "100%";
  
  elts.text1.style.filter = "";
  elts.text1.style.opacity = "0%";
}


function animate() {
  requestAnimationFrame(animate);
  
  let newTime = new Date();
  let shouldIncrementIndex = cooldown > 0;
  let dt = (newTime - time) / 1000;
  time = newTime;
  
  cooldown -= dt;
  
  if (cooldown <= 0) {
    if (shouldIncrementIndex) {
      textIndex++;
    }
    
    doMorph();
  } else {
    doCooldown();
  }
}


animate();

</script>
</body>
</html>
