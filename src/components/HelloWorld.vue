<script>
export default {
  data() {
    return {
      message: 'Hello Employees',
      employee: {},
    }
  },
  computed: {
    hasEmployee() {
      return this.isEmpty(this.employee) ? false : true
    },
  },
  methods: {
    isEmpty(obj) {
      return Object.keys(obj).length === 0
    },
    callApi() {
      const inputValue = document.getElementById('inputBox').value

      if (!inputValue) {
        alert('ENTER HRMS ID or EMP ID')
        return
      }

      fetch(
        'https://nwreu-backend.vercel.app/knowyourbooth/search?hrmsId=' +
          inputValue +
          '&empId=' +
          inputValue,
        {
          headers: {
            accept: 'application/json, text/plain, */*',
            'accept-language': 'en-GB,en-US;q=0.9,en;q=0.8',
            priority: 'u=1, i',
            'sec-ch-ua': '"Google Chrome";v="131", "Chromium";v="131", "Not_A Brand";v="24"',
            'sec-ch-ua-mobile': '?0',
            'sec-ch-ua-platform': '"macOS"',
            'sec-fetch-dest': 'empty',
            'sec-fetch-mode': 'cors',
            'sec-fetch-site': 'cross-site',
            Referer: 'https://www.nwreu.org/',
            'Referrer-Policy': 'strict-origin-when-cross-origin',
          },
          body: null,
          method: 'GET',
        },
      )
        .then((response) => response.json())
        .then((data) => {
          alert(data)
          this.employee = data
        })
        .catch((error) => {
          alert('API call failed! Error: ' + error)
        })
    },
  },
}
</script>

<template>
  <div>
    <div class="container">
      <input
        style="height: 50px; width: 300px"
        type="text"
        id="inputBox"
        class="input-box"
        placeholder="ENTER HRMS ID or EMP ID"
      />
      <br />
      <button class="button" type="submit" style="width: 300px" @click="callApi">
        Get Your Booth
      </button>
    </div>
    <div v-if="hasEmployee">
      <table>
        <thead>
          <tr>
            <th>Employee Name</th>
            <th>Designation</th>
            <th>Emp Id</th>
            <th>Station</th>
            <th>Working Under</th>
            <th>HRMS ID</th>
            <th>Booth Name</th>
            <th>Booth Number</th>
          </tr>
        </thead>
        <tbody>
          <tr :key="employee.id">
            <td>{{ employee.name }}</td>
            <td>{{ employee.designation }}</td>
            <td>{{ employee.empId }}</td>
            <td>{{ employee.station }}</td>
            <td>{{ employee.workingUnder }}</td>
            <td>{{ employee.hrmsId }}</td>
            <td>{{ employee.boothName }}</td>
            <td>{{ employee.boothNumber }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
.logo {
  width: 100px;
  height: auto;
  margin-bottom: 20px;
}
.container {
  text-align: center;
}
.input-box {
  padding: 10px;
  width: 250px;
  margin-bottom: 20px;
  border-radius: 5px;
  border: 1px solid #ccc;
}
.button {
  padding: 10px 20px;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
.button:hover {
  background-color: #45a049;
}
table {
  border-collapse: collapse;
  width: 100%;
}

th {
  text-align: left;
  padding: 15px;
  border-bottom: 1px solid #ddd;
  text-align: left;
  font-weight: bold;
  color: black;
}
td {
  text-align: left;
  padding: 15px;
  border-bottom: 1px solid #ddd;
  text-align: left;
  color: black;
}
</style>
