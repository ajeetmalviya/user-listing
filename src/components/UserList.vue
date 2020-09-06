<!--user interafce section-->
<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <p class="display-4">Lex Dock User List</p>
      </div>
    </div>

    <div class="row">
      <div class="col-md-12">
        <label for="search" id="lblSearch">Search by any keyword :</label>
        <input type="text" id="txtSearch" v-model="search" placeholder="Filter users" />
      </div>
    </div>
    <div class="row">
      <div class="col-12">
        <table
          id="dtBasicExample"
          class="table table-striped table-bordered table-sm"
          cellspacing="0"
          width="100%"
        >
          <thead>
            <tr>
              <th class="th-sm" v-for="(column, index) in this.columns" :key="index">{{column.name}}</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(user, index) in sortedUsers" :key="index">
              <td>{{user.name}}</td>
              <td>{{user.email}}</td>
              <td>{{user.phoneNumber}}</td>
              <td>{{user.companyName}}</td>
              <td>{{user.createdDate}}</td>
            </tr>
          </tbody>
          <tfoot>
            <tr>
              <th class="th-sm" v-for="(column, index) in this.columns" :key="index">{{column.name}}</th>
            </tr>
          </tfoot>
        </table>
      </div>
    </div>
  </div>
</template>

<!--script section-->
<script>
export default {
  data() {
    return {
      search: "",
      fromdate: "",
      todate: "",

      columns: [
        { name: "Name", sortkey: "name" },
        { name: "Email Address", sortkey: "email" },
        { name: "Phone Number", sortkey: "phone" },
        { name: "Company Name", sortkey: "company" },
        { name: "Created Date", sortkey: "date" },
      ],

      users: [
        {
          name: "Abeer",
          email: "abeer@lexdock.com",
          phoneNumber: "8787989876",
          companyName: "LexDock legal",
          createdDate: "01-01-1990",
        },
        {
          name: "Smita",
          email: "smita@cisco.com",
          phoneNumber: "9878906754",
          companyName: "Cisco",
          createdDate: "01-01-1991",
        },
        {
          name: "Dan",
          email: "dan@metagami.com",
          phoneNumber: "3457658769",
          companyName: "MetaGami",
          createdDate: "01-01-1992",
        },
        {
          name: "Tim",
          email: "tim@siemens.com",
          phoneNumber: "2345436789",
          companyName: "siemens ltd",
          createdDate: "01-01-1993",
        },
        {
          name: "Alex",
          email: "alex@brazil.com",
          phoneNumber: "5645678798",
          companyName: "brazil",
          createdDate: "01-01-1994",
        },
        {
          name: "Cristian",
          email: "cristain@Cognizant.com",
          phoneNumber: "9878674523",
          companyName: "Cognizant",
          createdDate: "01-01-1995",
        },
        {
          name: "Jesper",
          email: "jesper@Accenture.com",
          phoneNumber: "9878657678",
          companyName: "Accenture",
          createdDate: "01-01-1996",
        },
        {
          name: "Rashmi",
          email: "rashmi@sgre.com",
          phoneNumber: "1234654327",
          companyName: "SGRE",
          createdDate: "01-01-1997",
        },
        {
          name: "Ritu",
          email: "ritu@moodies.com",
          phoneNumber: "9878965734",
          companyName: "moodies",
          createdDate: "01-01-1998",
        },
      ],
    };
  },

  computed: {
    sortedUsers() {
      return this.users.filter((rows) => {
        for (var row in rows) {
          if (String(rows[row]).indexOf(this.search) !== -1) {
            return true;
          }
        }
        return false;
      });
    },
  },

  methods: {
    getUsers() {
      return this.users;
    },
  },
};
</script>

<!--style section-->
<style>
#txtSearch,
#lblSearch {
  float: left;
}
</style>