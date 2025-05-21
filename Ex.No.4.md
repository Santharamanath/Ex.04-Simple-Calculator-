# Ex04 Simple Calculator - React Project
## Date:

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
### App.jsx
```
import React, { useState, useEffect } from 'react';
import './App.css';
import Button from './Button'; // <-- new import

function App() {
  const [input, setInput] = useState('');
  const [result, setResult] = useState('');

  const handleClick = (value) => {
    if (value === '=') {
      calculateResult();
    } else if (value === 'C') {
      clearInput();
    } else if (value === '⌫') {
      setInput((prevInput) => prevInput.slice(0, -1));
    } else {
      setInput((prevInput) => prevInput + value);
    }
  };

  const calculateResult = () => {
    try {
      if (input.includes('/0')) {
        setResult('Error: Division by zero');
      } else {
        setResult(eval(input).toString());
      }
    } catch (error) {
      setResult('Error');
    }
  };

  const clearInput = () => {
    setInput('');
    setResult('');
  };

  useEffect(() => {
    const handleKeyDown = (event) => {
      const key = event.key;
      if (/[0-9+\-*/.=C]|Backspace|Enter|Escape/.test(key)) {
        event.preventDefault();
        if (key === 'Enter' || key === '=') {
          calculateResult();
        } else if (key === 'Backspace') {
          setInput((prevInput) => prevInput.slice(0, -1));
        } else if (key === 'Escape' || key === 'C') {
          clearInput();
        } else {
          setInput((prevInput) => prevInput + key);
        }
      }
    };

    window.addEventListener('keydown', handleKeyDown);
    return () => window.removeEventListener('keydown', handleKeyDown);
  }, [input]);

  return (
    <div className="calculator">
      <h1>Calculator</h1>
      <div className="display">
        <input type="text" value={input} readOnly />
        <div className="result">{result}</div>
      </div>
      <div className="buttons">
        {['C', '%', '⌫', '/', '7', '8', '9', '*', '4', '5', '6', '-', '1', '2', '3', '+', '0', '.', '='].map((button) => (
          <Button
            key={button}
            label={button}
            onClick={handleClick}
            className={
              button === '=' ? 'equals' : 
              button === 'C' ? 'clear' : 
              button === '⌫' ? 'backspace' : ''
            }
          />
        ))}
      </div>
      <footer className="footer">
        <p>&copy; Developed by: NITHISH S</p>
        <p>Register Number: 21222322070</p>
      </footer>
    </div>
  );
}

export default App;
```

### App.css
```
body {
  margin: 0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background: linear-gradient(135deg, #6a5acd, #9370db);
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.calculator {
  background: #2e1e4d;
  padding: 20px;
  border-radius: 15px;
  box-shadow: 0px 10px 25px rgba(0, 0, 0, 0.3);
  width: 320px;
}

h1 {
  color: #dda0dd;
  text-align: center;
  margin-bottom: 20px;
  font-size: 24px;
  animation: blink 1.5s infinite;
}

@keyframes blink {
  0% { opacity: 1; }
  50% { opacity: 0.6; }
  100% { opacity: 1; }
}

.display {
  background: #f8f0ff;
  padding: 15px;
  border-radius: 10px;
  margin-bottom: 20px;
}

.display input {
  width: 100%;
  height: 40px;
  font-size: 50px;
  text-align: right;
  padding: 5px;
  box-sizing: border-box;
  border: none;
  background: transparent;
  color: #4b0082;
}

.result {
  font-size: 30px;
  text-align: right;
  padding: 5px;
  color: #4b0082;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
}

button {
  width: 100%;
  height: 60px;
  font-size: 20px;
  cursor: pointer;
  border: none;
  background: #6a5acd;
  color: #fff;
  border-radius: 10px;
  transition: background 0.3s ease;
}

button:hover {
  background: #836fff;
}

button:active {
  background: #483d8b;
}

.equals {
  grid-column: span 2;
  background: #9370db;
}

.equals:hover {
  background: #b19cd9;
}

.clear {
  background: #ba55d3;
}

.clear:hover {
  background: #9932cc;
}

.backspace {
  background: #7b68ee;
}

.backspace:hover {
  background: #6a5acd;
}

.footer {
  margin-top: 20px;
  padding: 10px;
  text-align: center;
  font-size: 14px;
  color: #ddd;
  border-top: 1px solid #aaa;
}

.footer p {
  margin: 5px 0;
}

```
### Button.jsx
```
import React from 'react';

function Button({ label, onClick, className }) {
  return (
    <button onClick={() => onClick(label)} className={className}>
      {label}
    </button>
  );
}

export default Button;
```


## OUTPUT
![image](https://github.com/user-attachments/assets/be3a6419-c68d-4071-bb5e-57af28af5f01)


## RESULT
The program for developing a simple calculator in React.js is executed successfully.
