<template>
  <div class="container">
    <div class="tables-section">
      <div 
        v-for="table in tables" 
        :key="table.id" 
        class="table-wrapper"
        :class="{ 'single-index-table': table.indexes.length === 1 }"
      >
        <table>
          <thead>
            <tr>
              <th
                v-for="item in table.indexes"
                :key="'head-' + item.index"
                :style="{ backgroundColor: item.color }"
                @click="toggleColor(item)"
              >
                {{ item.index }}      
                [ {{ headerText(item.color) }} ]
              </th>
            </tr>
          </thead>
          <tbody>
            <!-- First Counter -->
            <tr>
              <td v-for="item in table.indexes" :key="'body-count1-' + item.index">
                <span>כמות טלויזיות</span><br> <!-- Label for the first button -->
                <button @click="decrementCount(item)" class="control-button">-</button>
                <span class="counter-display">{{ item.count }}</span>
                <button @click="incrementCount(item)" class="control-button">+</button>
              </td>
            </tr>

            <!-- Second Counter -->
            <tr>
              <td v-for="item in table.indexes" :key="'body-count2-' + item.index">
                <span>כמות מנויים</span><br> <!-- Label for the second button -->
                <div v-if="item.count2 !== undefined">
                  <button @click="decrementCount2(item)" class="control-button">-</button>
                  <span class="counter-display">{{ item.count2 }}</span>
                  <button @click="incrementCount2(item)" class="control-button">+</button>
                </div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>





<script>
export default {
  name: 'OrtopEdit',
  data() {
    return {
      tables: [
        {
          id: 1,
          indexes: Array(5).fill(null).map((_, i) => ({
            index: i + 1,
            color: 'transparent',
            count: 0,
            count2: 0,
          }))
        },
        {
          id: 2,
          indexes: Array(5).fill(null).map((_, i) => ({
            index: i + 6,
            color: 'transparent',
            count: 0,
            count2: 0,
          }))
        },
        {
          id: 3,
          indexes: Array(5).fill(null).map((_, i) => ({
            index: i + 11,
            color: 'transparent',
            count: 0,
            count2: 0,
          }))
        },
        {
          id: 4,
          indexes: Array(1).fill(null).map((_, i) => ({
            index: i + 16,
            color: 'transparent',
            count: 0,
            count2: 0,
            
          }))
        }
      ]
    };
  },
  methods: {
      toggleColor(item) {
    if (item.color === 'transparent') {
      item.color = 'green';
    } else if (item.color === 'green') {
      item.color = 'yellow';
    } else if (item.color === 'yellow') {
      item.color = 'red';
    } else if (item.color === 'red') {
      item.color = 'transparent';
    } else {
      item.color = 'transparent';  // This will be hit after red
    }
  },  

  incrementCount(item) {
      item.count = (item.count + 1) % 5;
    },
    decrementCount(item) {
      if (item.count === 0) {
        item.count = 4;
      } else {
        item.count -= 1;
      }
    },
    incrementCount2(item) {
      item.count2 = (item.count2 + 1) % 5;
    },
    decrementCount2(item) {
      if (item.count2 === 0) {
        item.count2 = 4;
      } else {
        item.count2 -= 1;
      }
    }

    },

  computed: {
    headerText() {
  return (color) => {
    switch(color) {
      case 'green': return 'מנוי';
      case 'yellow': return 'פנוי';
      case 'red': return 'ריק';
      case 'transparent': return 'אין'; // Added a label for 'none' color. Replace 'אין' with appropriate translation or desired text.
      default: return '';
    }
  };
}

}

};

</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 120vh;
  color: black;
}

table {
  width: 100%;
  border-collapse: collapse;
}

th, td {
  border: 1px solid #000;
  padding: 15px 20px;
  text-align: center;
  cursor: pointer;
  font-size: 18px;
  transition: background-color 0.3s, transform 0.2s;
}

th:active {
  transform: scale(0.95);
}

@media (max-width: 600px) {
  th, td {
    padding: 10px 15px;
    font-size: 16px;
  }
}

.counter-button {
  padding: 10px 20px;
  font-size: 18px;
  font-weight: bold;
  cursor: pointer;
  background-color: #f9f9f9;
  border: 2px solid black;
  border-radius: 8px;
  width: 100%;
  display: block;
  text-align: center;
  color: black;
  transition: background-color 0.3s, color 0.3s;
}

.counter-button:hover {
  background-color: black;
  color: #f9f9f9;
}

.counter-button:active {
  background-color: black;
  color: #f9f9f9;
  transform: scale(0.97);
  transition: transform 0.1s;
}

.tables-section {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.table-wrapper {
  margin-bottom: 20px;
}

.control-button {
  padding: 6px 12px;
  font-size: 16px;
  margin: 0 5px;
  cursor: pointer;
  border: 1px solid #000;
  background-color: #f9f9f9;
  box-shadow: 0 2px 5px rgba(0,0,0,0.1); /* subtle shadow for depth */
  border-radius: 50%; /* making them circular */
  transition: background-color 0.3s, transform 0.2s; /* added transform transition */
  width: 40px;    /* Fixed width */
  height: 40px;   /* Fixed height */
  
  
  
}

.control-button:hover {
  background-color: #57bdec;
  transform: translateY(-2px); /* subtle lift effect */
}

.control-button:active {
  background-color: #ccc;
  transform: translateY(1px); /* subtle press effect */
  box-shadow: 0 1px 3px rgba(0,0,0,0.1); /* reduced shadow on press */
}

.counter-display {
  font-size: 18px;
  margin: 0 10px;
}
</style>

