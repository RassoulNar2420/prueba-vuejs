<script setup>
</script>

<template>
  <section>
    <div id="myDIV" class="header">
      <h2>Mi Lista</h2>
      <input type="text" id="myInput" placeholder="Title...">
      <span onclick="newElement()" class="addBtn">Add</span>
    </div>
    
    <div id="divUl">
      <ul id="">
        <li> <input type="checkbox" id="itemChek"  checked />Hit the gym</li>
      </ul>
    </div>
  </section>
</template>

<style scoped>
  /* Include the padding and border in an element's total width and height */
* {
  box-sizing: border-box;
}

section {
  width: 400px;
}

#divUl {
  text-align: left;
}
/* Style the list items */
ul li {
  
}

/* Set all odd list items to a different color (zebra-stripes) */
ul li:nth-child(odd) {
  background: #f9f9f9;
}

/* Darker background-color on hover */
ul li:hover {
  background: #ddd;
}


/* Style the header */
.header {
  background-color: #f44336;
  padding: 30px 40px;
  color: white;
  text-align: center;
}

/* Clear floats after the header */
.header:after {
  content: "";
  display: table;
  clear: both;
}

/* Style the input */
input {
  margin: 0;
  border: none;
  border-radius: 0;
  width: 75%;
  padding: 10px;
  float: left;
  font-size: 16px;
}

/* Style the "Add" button */
.addBtn {
  padding: 10px;
  width: 25%;
  background: #d9d9d9;
  color: #555;
  float: left;
  text-align: center;
  font-size: 16px;
  cursor: pointer;
  transition: 0.3s;
  border-radius: 0;
}

.addBtn:hover {
  background-color: #bbb;
}
</style>
