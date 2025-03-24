
# **Digital Clock ⏰**  

A simple **digital clock** component built using React. It updates every second and displays the current time in a 12-hour format with an AM/PM indicator.

## **Features**  
✅ Displays the current time in **hh:mm:ss AM/PM** format  
✅ Updates every second using `setInterval`  
✅ Handles **zero-padding** for single-digit hours, minutes, and seconds  
✅ **Optimized cleanup** with `useEffect` to prevent memory leaks  

---

## **Installation & Usage**  

### **1. Install Dependencies**  
Ensure you have a React project set up. If not, create one using:  

```sh
npx create-react-app my-app
cd my-app
npm install
```

### **2. Add the Digital Clock Component**  
Create a new file **`DigitalClock.js`** inside `src/` and paste the following code:  

```jsx
import { useState, useEffect } from "react";

function DigitalClock() {
  const [time, setTime] = useState(new Date());

  useEffect(() => {
    const intervalId = setInterval(() => {
      setTime(new Date());
    }, 1000);
    return () => clearInterval(intervalId);
  }, []);

  function formatTime() {
    let hours = time.getHours();
    const minutes = time.getMinutes();
    const seconds = time.getSeconds();
    const meridiem = hours >= 12 ? "PM" : "AM";
    hours = hours % 12 || 12;
    return `${padZero(hours)}:${padZero(minutes)}:${padZero(seconds)} ${meridiem}`;
  }

  function padZero(number) {
    return number < 10 ? `0${number}` : number;
  }

  return (
    <div className="clock-container">
      <div className="clock">
        <span>{formatTime()}</span>
      </div>
    </div>
  );
}

export default DigitalClock;
```

### **3. Import & Use in Your App**  
Open `App.js` and import the component:  

```jsx
import DigitalClock from "./DigitalClock";

function App() {
  return (
    <div className="App">
      <h1>My Digital Clock</h1>
      <DigitalClock />
    </div>
  );
}

export default App;
```

---

## **Styling (Optional) 🎨**  
You can add the following CSS in **`App.css`** for better styling:  

```css
.clock-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #282c34;
}

.clock {
  font-size: 3rem;
  font-family: 'Courier New', monospace;
  color: white;
  background: black;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0px 4px 10px rgba(255, 255, 255, 0.2);
}
```

---

## **License**  
This project is **open-source** and free to use! 🚀  

---

Now, your **Digital Clock** component is ready to use! 🎉