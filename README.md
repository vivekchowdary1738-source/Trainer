<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Interactive Number System & Addressing Mode Trainer</title>
  <style>
    body { font-family: Arial, sans-serif; background: #f3f3f3; padding: 20px; }
    .box { background: white; padding: 20px; border-radius: 10px; margin-bottom: 20px; }
    button { padding: 10px 15px; background: #007bff; color: white; border: none; border-radius: 5px; cursor: pointer; }
    button:hover { background: #0056b3; }
    input { padding: 8px; width: 200px; }
  </style>
</head>
<body>
  <h1>Interactive Trainer</h1>

  <!-- NUMBER SYSTEM QUIZ -->
  <div class="box">
    <h2>Number System Converter</h2>
    <input id="numInput" placeholder="Enter Decimal Number">
    <button onclick="convert()">Convert</button>
    <p id="output"></p>
  </div>

  <!-- ADDRESSING MODE QUIZ -->
  <div class="box">
    <h2>Addressing Mode Quiz</h2>
    <p id="question"></p>
    <button onclick="check('Immediate')">Immediate</button>
    <button onclick="check('Direct')">Direct</button>
    <button onclick="check('Indirect')">Indirect</button>
    <button onclick="check('Indexed')">Indexed</button>
    <p id="result"></p>
  </div>

  <!-- MEMORY MAP DISPLAY -->
  <div class="box">
    <h2>Virtual Memory Map</h2>
    <button onclick="generateMap()">Generate Sample Map</button>
    <pre id="memory"></pre>
  </div>

<script>
// NUMBER SYSTEM
function convert(){
  let num = document.getElementById('numInput').value;
  if(num === '') return;
  document.getElementById('output').innerHTML = 
    "Binary: " + parseInt(num).toString(2) + "<br>" +
    "Octal: " + parseInt(num).toString(8) + "<br>" +
    "Hex: " + parseInt(num).toString(16).toUpperCase();
}

// ADDRESSING MODE QUIZ
let ques = {
  text: "MOV R1, #45",
  ans: "Immediate"
};
document.getElementById('question').innerHTML = "Identify the addressing mode: " + ques.text;

function check(choice){
  if(choice === ques.ans){
    document.getElementById('result').innerHTML = "Correct!";
  } else {
    document.getElementById('result').innerHTML = "Wrong! Correct Answer: " + ques.ans;
  }
}

// MEMORY MAP
function generateMap(){
  let map = "Virtual Memory Map\n" +
            "-------------------------\n" +
            "0x0000 - 0x0FFF : Code\n" +
            "0x1000 - 0x1FFF : Data\n" +
            "0x2000 - 0x2FFF : Stack\n" +
            "0x3000 - 0x3FFF : Heap";
  document.getElementById('memory').innerText = map;
}
</script>

</body>
</html>
