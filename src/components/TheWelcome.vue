<script>
export default {
  data() {
    return {
      message: 'Hello Employees',
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
  <div class="container">
    <input
      style="height: 50px; width: 300px"
      type="text"
      id="inputBox"
      class="input-box"
      placeholder="ENTER HRMS ID or EMP ID"
    />
    <br />
    <button class="button" type="submit" @click="callApi">Get Your Booth</button>
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
          <td>
            <a href="javascript(0);">{{ employee.name }}</a>
          </td>
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
</template>
