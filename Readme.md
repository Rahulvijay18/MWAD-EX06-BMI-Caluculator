# Ex06 BMI Calculator
## Date: 11/11/25

## AIM
To create a BMI calculator using React Router 

## ALGORITHM
### STEP 1 State Initialization
Manage the current page (Home or Calculator) using React Router.

### STEP 2 User Input
Accept weight and height inputs from the user.

### STEP 3 BMI Calculation
Calculate the BMI based on user input.

### STEP 4 Categorization
Classify the BMI result into categories (Underweight, Normal weight, Overweight, Obesity).

### STEP 5 Navigation
Navigate between pages using React Router.

## PROGRAM

## Bmi.jsx

```
import { useState } from "react";
import "./Style.css";

export default function Bmi() {
  const [weight, setWeight] = useState("");
  const [height, setHeight] = useState("");
  const [bmi, setBmi] = useState(null);
  const [category, setCategory] = useState("");

  const calculateBMI = (e) => {
    e.preventDefault();
    const h = height / 100;
    const bmiValue = (weight / (h * h)).toFixed(2);
    setBmi(bmiValue);

    if (bmiValue < 18.5) setCategory("Underweight");
    else if (bmiValue < 25) setCategory("Normal weight");
    else if (bmiValue < 30) setCategory("Overweight");
    else setCategory("Obesity");
  };

  return (
    <div className="bmi-container">
      <h2>BMI CALCULATOR</h2>

      <form onSubmit={calculateBMI} className="bmi-form">
        <input
          type="number"
          placeholder="Weight (kg)"
          value={weight}
          onChange={(e) => setWeight(e.target.value)}
          required
        />

        <input
          type="number"
          placeholder="Height (cm)"
          value={height}
          onChange={(e) => setHeight(e.target.value)}
          required
        />

        <button type="submit">Calculate</button>
      </form>

      {bmi && (
        <div className="result-box">
          <p>Your BMI: {bmi}</p>
          <p>Category: {category}</p>
        </div>
      )}
    </div>
  );
}

```


## Style.css

```

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html, body, #root {
  height: 100%;
  width: 100%;
  background: linear-gradient(120deg, #79c2ff, #a98bff);
  font-family: Arial, Helvetica, sans-serif;
}

.navbar {
  background: #182a3a;
  padding: 14px;
  display: flex;
  justify-content: center;
  gap: 30px;
}

.nav-link {
  text-decoration: none;
  color: white;
  font-weight: bold;
  font-size: 18px;
}

.page-container {
  height: calc(100vh - 60px);
  display: flex;
  justify-content: center;
  align-items: center;
}

.bmi-container {
  background: rgb(19, 17, 17);
  width: 380px;
  padding: 30px;
  border-radius: 12px;
  text-align: center;
  box-shadow: 0px 8px 30px rgba(0, 0, 0, 0.35);
}

.bmi-form input {
  width: 100%;
  padding: 12px;
  margin: 8px 0;
  border-radius: 6px;
  border: 1px solid #555;
  font-size: 16px;
}

.bmi-form button {
  width: 100%;
  padding: 12px;
  background: #ff6b6b;
  color: white;
  border: none;
  border-radius: 6px;
  font-size: 17px;
  font-weight: bold;
  cursor: pointer;
}

.result-box {
  margin-top: 20px;
  background: #fff3c4;
  padding: 15px;
  border-radius: 6px;
  border: 2px solid #ffd85d;
}

.result-box p {
  color: violet;
  font-weight: bold;
}


```

## App.jsx

```

import { BrowserRouter as Router, Routes, Route, Link } from "react-router-dom";
import Bmi from "./Bmi";
import "./Style.css";

export default function App() {
  return (
    <Router>
      <nav className="navbar">
        <Link className="nav-link" to="/">Home</Link>
        <Link className="nav-link" to="/bmi">BMI Calculator</Link>
      </nav>

      <div className="page-container">
        <Routes>
          <Route path="/" element={<h1 className="home-title">Welcome to BMI Calculator</h1>} />
          <Route path="/bmi" element={<Bmi />} />
        </Routes>
      </div>
    </Router>
  );
}


```

## OUTPUT

<img width="1920" height="900" alt="Screenshot (23)" src="https://github.com/user-attachments/assets/95473136-3f2c-4c60-9eb3-8601fc14cd6f" />


<img width="1920" height="898" alt="Screenshot (24)" src="https://github.com/user-attachments/assets/08b4aad4-74bf-4876-b6c0-a5b1b03c51f4" />

<img width="1920" height="897" alt="Screenshot (25)" src="https://github.com/user-attachments/assets/c95759ac-4826-42a2-810d-dfda1daad964" />



## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
