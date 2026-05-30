# Ex04 Simple Calculator - React Project
## Date:30-05-2026
## NAME:JANATHUL FIRDHOUS A
## REG NO:212224040129

## AIM
To  develop a Simple Calculator using React.js with clean and responsive design, ensuring a smooth user experience across different screen sizes.

## ALGORITHM
### STEP 1
Create a React App.

### STEP 2
Open a terminal and run:
  <ul><li>npx create-react-app simple-calculator</li>
  <li>cd simple-calculator</li>
  <li>npm start</li></ul>

### STEP 3
Inside the src/ folder, create a new file Calculator.js and define the basic structure.

### STEP 4
Plan the UI: Display screen, number buttons (0-9), operators (+, -, *, /), clear (C), and equal (=).

### STEP 5
Create a new file Calculator.css in src/ and add the styling.

### STEP 6
Open src/App.js and modify it.

### STEP 7
Start the development server.
  npm start

### STEP 8
Open http://localhost:3000/ in the browser.

### STEP 9
Test the calculator by entering numbers and operations.

### STEP 10
Fix styling issues and refine content placement.

### STEP 11
Deploy the website.

### STEP 12
Upload to GitHub Pages for free hosting.

## PROGRAM
## SimpleCalculator.jsx
```
import React, { useState } from "react";
import "./Calculator.css";

export default function SimpleCalculator() {
  const [input, setInput] = useState("");

  const handleClick = (value) => {
    setInput(input + value);
  };

  const handleClear = () => {
    setInput("");
  };

  const handleBackspace = () => {
    setInput(input.slice(0, -1));
  };

  const handleCalculate = () => {
    try {
      const expression = input
        .replace(/×/g, "*")
        .replace(/÷/g, "/");

      const result = Function(
        '"use strict"; return (' + expression + ')'
      )();

      setInput(result.toString());
    } catch {
      setInput("Error");
    }
  };

  return (
    <div className="calculator-container">
      <h1 className="title">Calculator</h1>

      <input
        type="text"
        value={input}
        readOnly
        className="display"
      />

      <div className="button-grid">
        {[7, 8, 9, "÷", 4, 5, 6, "×", 1, 2, 3, "-", 0, ".", "=", "+"].map(
          (btn) => (
            <button
              key={btn}
              onClick={() => {
                if (btn === "=") {
                  handleCalculate();
                } else {
                  handleClick(btn.toString());
                }
              }}
              className={
                btn === "="
                  ? "button equal"
                  : ["+", "-", "×", "÷"].includes(btn)
                  ? "button operator"
                  : "button"
              }
            >
              {btn}
            </button>
          )
        )}

        <button
          onClick={handleBackspace}
          className="button backspace span-two"
        >
          ⌫
        </button>

        <button
          onClick={handleClear}
          className="button clear span-two"
        >
          C
        </button>
      </div>
    </div>
  );
}
```
## Calculator.css
```
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: linear-gradient(to right, #141e30, #243b55);
}

.calculator-container {
  max-width: 340px;
  margin: 50px auto;
  padding: 25px;
  background: #1f2937;
  border-radius: 20px;
  box-shadow: 0 0 20px rgba(0,0,0,0.4);
  text-align: center;
}

.title {
  color: white;
  margin-bottom: 20px;
}

.display {
  width: 100%;
  height: 60px;
  margin-bottom: 20px;
  border: none;
  border-radius: 10px;
  font-size: 24px;
  text-align: right;
  padding: 10px;
  background: #f3f4f6;
  color: black;
  box-sizing: border-box;
}

.button-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 12px;
}

.button {
  padding: 18px;
  font-size: 20px;
  border: none;
  border-radius: 12px;
  cursor: pointer;
  background: #374151;
  color: white;
  transition: 0.2s;
}

.button:hover {
  transform: scale(1.05);
}

.operator {
  background: #f59e0b;
}

.equal {
  background: #10b981;
}

.clear {
  background: #ef4444;
}

.backspace {
  background: #6366f1;
}

.span-two {
  grid-column: span 2;
}
```
## App.jsx
```
import SimpleCalculator from "./SimpleCalculator";

function App() {
  return (
    <>
      <SimpleCalculator />
    </>
  );
}

export default App;
```


## OUTPUT

<img width="1919" height="878" alt="image" src="https://github.com/user-attachments/assets/36d50bed-70ae-4fda-89ab-6705712b6529" />

<img width="1919" height="858" alt="image" src="https://github.com/user-attachments/assets/74330d3a-9e13-4cee-b6d3-a72744cb4da9" />

<img width="1919" height="934" alt="image" src="https://github.com/user-attachments/assets/a011ac47-7867-4000-b9a5-1b7398cbf463" />



## RESULT
The program for developing a simple calculator in React.js is executed successfully.
