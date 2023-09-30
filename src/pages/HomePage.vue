<template>
    <div class="container">
      <div v-for="letter in letters" :key="letter" class="button-group">
        <button
          :class="['button', `button-${letter.toLowerCase()}`]"
          @click="showDropdownFor = showDropdownFor === letter ? null : letter"
        >
          {{ letter }}
        </button>
        
        <div v-if="showDropdownFor === letter" class="dropdown">
          <button 
            v-for="num in 5" 
            :key="num" 
            class="dropdown-item"
            @click="openNewWindow(num)"
          >
            {{ num }}
          </button>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        letters: ['A', 'B', 'C', 'D', 'E', 'F'],
        showDropdownFor: null,
      };
    },
    methods: {
      openNewWindow(num) {
        window.open(`https://example.com/${num}`, '_blank');
      }
    }
  };
  </script>
  
  <style scoped>
  /* Your styles here... */
  
  .button-group {
    position: relative;
    display: inline-block;
  }
  
  </style>
  
  
  <style scoped>
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh; /* full viewport height */
    flex-wrap: wrap;
    height: 70vh; /* decrease from 100vh to 80vh or adjust as needed */
  }
  
  .button {
    margin: 10px;
    padding: 15px 30px;
    font-size: 1.5rem;
    border: none;
    cursor: pointer;
    transition: background-color 0.3s;
  }
  
  .button-a {
    background-color: red;
  }
  
  .button-b {
    background-color: orange;
  }
  
  .button-c {
    background-color: yellow;
  }
  
  .button-d {
    background-color: green;
  }
  
  .button-e {
    background-color: blue;
  }
  
  .button-f {
    background-color: purple;
  }
  
  .button:hover {
    background-color: #000; /* Black background on hover */
    color: #fff; /* White text on hover */
  }
  .button {
  margin: 10px;
  padding: 15px 30px;
  font-size: 1.5rem;
  border: none;
  cursor: pointer;
  transition: background-color 0.3s;
  border-radius: 25px; /* Increased border-radius for rounded corners */
  padding: 15px 50px; /* Increase the horizontal padding */
  min-width: 150px;  /* Set a minimum width */
}


.button-group {
  position: relative;
  display: inline-block;
}

.dropdown {
  position: absolute;
  bottom: 100%; /* Makes the dropdown appear above the button */
  left: 0; /* Aligns left of the dropdown with the left of the button */
  border: 1px solid #ccc;
  background-color: #f9f9f9;
  width: auto; /* Adjust width as needed */
  z-index: 1;
  border-radius: 8px;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  background: linear-gradient(to bottom, #f9f9f9, #e0e0e0); /* gradient background */
    box-shadow: 0px 8px 20px 0px rgba(0,0,0,0.25); /* enhanced shadow */
    width: 100px;  /* make it wider */
}

.dropdown-item {
    padding: 15px 25px; /* increased padding for larger touch area */
    font-size: 18px;  /* increased font size for clarity */
  padding: 8px 16px;
  background-color: #f9f9f9;
  border-top: 1px solid #e0e0e0; /* Adjusted to 'border-top' for upwards dropdown */
  cursor: pointer;
  width: 150px; /* Increased width for dropdown items */
  padding: 10px 20px; /* more horizontal padding for wider appearance */
    /* ... existing styles ... */
    transition: background-color 0.3s, transform 0.3s; /* transition effect */
    font-weight: 500; /* bolder font */
}

.dropdown-item:first-child {
  border-top: none; /* Adjusted to ':first-child' for upwards dropdown */
}
.dropdown-item + .dropdown-item {
   
    border-top: 1px solid #771111; /* separator */
}

.dropdown-item:hover {
    background-color: #c7c7c7;
    transform: scale(1.05); 
}
.dropdown-item:active {
    color: #ffffff;
    background-color: #a7a7a7;
    transform: scale(0.95); /* slight push effect */
}

  </style>
  