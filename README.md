# Ex06 BMI Calculator
## Date:

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
App.jsx
```
import React, { useState } from "react";
import { BrowserRouter, Routes, Route, Link } from "react-router-dom";

function Home() {
    return (
        <>
            <h1>BMI Calculator</h1>
            <p>Welcome to the BMI Calculator</p>
            <Link to="/calculator">
                <button>Go to Calculator</button>
            </Link>
        </>
    );
}
function Calculator() {
    const [weight, setWeight] = useState("");
    const [height, setHeight] = useState("");
    const [bmi, setBmi] = useState("");
    const [category, setCategory] = useState("");

    const calculateBMI = () => {
        if (weight > 0 && height > 0) {
            const heightInMeters = height / 100;
            const result = weight / (heightInMeters * heightInMeters);

            setBmi(result.toFixed(2));

            if (result < 18.5) {
                setCategory("Underweight");
            } else if (result < 25) {
                setCategory("Normal weight");
            } else if (result < 30) {
                setCategory("Overweight");
            } else {
                setCategory("Obesity");
            }
        } else {
            setBmi("");
            setCategory("Please enter valid values");
        }
    };

    return (
        <>
            <h1>BMI Calculator</h1>

            <label>Weight (kg): </label>
            <input
                type="number"
                value={weight}
                onChange={(e) => setWeight(e.target.value)}
            />

            <br /><br />

            <label>Height (cm): </label>
            <input
                type="number"
                value={height}
                onChange={(e) => setHeight(e.target.value)}
            />

            <br /><br />

            <button onClick={calculateBMI}>Calculate BMI</button>

            {bmi && (
                <>
                    <h2>BMI: {bmi}</h2>
                    <h2>Category: {category}</h2>
                </>
            )}

            <br />

            <Link to="/">
                <button>Home</button>
            </Link>
        </>
    );
}

function App() {
    return (
        <BrowserRouter>
            <Routes>
                <Route path="/" element={<Home />} />
                <Route path="/calculator" element={<Calculator />} />
            </Routes>
        </BrowserRouter>
    );
}

export default App;
```
Main.jsx
```
import { StrictMode } from "react";
import { createRoot } from "react-dom/client";
import "./index.css";
import App from "./App.jsx";

createRoot(document.getElementById("root")).render(
    <StrictMode>
        <App />
    </StrictMode>
);
```
index.html
```
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>BMI Calculator</title>
</head>
<body>
    <div id="root"></div>

    <script type="module" src="/src/main.jsx"></script>
</body>
</html>
```
## OUTPUT
<img width="1917" height="974" alt="image" src="https://github.com/user-attachments/assets/9ca7bbfd-9371-4837-ae04-d08449a908fa" />



## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
