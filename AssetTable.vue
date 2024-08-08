<template>
  <div>
    <h1>Asset Management</h1>
    <table>
      <thead>
        <tr>
          <th>Asset Name</th>
          <th>Department</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="asset in assets" :key="asset.name">
          <td>{{ asset.name }}</td>
          <td>{{ asset.department }}</td>
        </tr>
      </tbody>
    </table>
    <button @click="downloadCSV">Download CSV</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      assets: [
        { name: "Printer", department: "HR" },
        { name: "Monitor", department: "IT" },
        { name: "Barcode Scanner", department: "ACCOUNT" },
      ],
    };
  },
  methods: {
    downloadCSV() {
      const rows = [
        ["Asset Name", "Department"],
        ...this.assets.map(asset => [asset.name, asset.department]),
      ];
      let csvContent = "data:text/csv;charset=utf-8,"
        + rows.map(e => e.join(",")).join("\n");
      const encodedUri = encodeURI(csvContent);
      const link = document.createElement("a");
      link.setAttribute("href", encodedUri);
      link.setAttribute("download", "assets.csv");
      document.body.appendChild(link);
      link.click();
      document.body.removeChild(link);
    },
  },
};
</script>

<style>
table {
  width: 100%;
  border-collapse: collapse;
}

th, td {
  border: 1px solid black;
  padding: 8px;
  text-align: left;
}

th {
  background-color: #f2f2f2;
}
</style>

