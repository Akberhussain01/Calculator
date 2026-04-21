let display = document.getElementById("display");
let history = document.getElementById("history");

function press(val) {
  display.value += val;
}

function clearDisplay() {
  display.value = "";
}

function del() {
  display.value = display.value.slice(0, -1);
}

function calculate() {
  try {
    let result = eval(display.value);
    
    let li = document.createElement("li");
    li.innerText = display.value + " = " + result;
    history.appendChild(li);

    display.value = result;
  } catch {
    display.value = "Error";
  }
}

// 🔥 Keyboard support (unique)
document.addEventListener("keydown", function(e) {
  if (!isNaN(e.key) || "+-*/.".includes(e.key)) {
    press(e.key);
  } else if (e.key === "Enter") {
    calculate();
  } else if (e.key === "Backspace") {
    del();
  }
});
