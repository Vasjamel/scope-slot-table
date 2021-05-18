<template>
  <div class="table-wrapper">
    <h1>Here will be the slot-scoped table</h1>
    <table>
      <thead>
        <tr>
          <th
            v-for="(column, index) in columns"
            :key="index"
            :style="{
              'min-width': column.minWidth + 'px',
              width: column.width + 'px',
            }"
          >
            <slot :name="column.prop + '_column'" :column="column" x />
          </th>
        </tr>
      </thead>

      <tr v-for="(eachRow, index) in dataArray" :key="index">
        <td v-for="column in columns" :key="column">
          <slot :name="column.prop + '_row'" :row="eachRow" />
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  props: ['dataArray', 'columns'],
}
</script>

<style scoped>
table {
  border-collapse: separate;
  border-spacing: 0 4px;
  table-layout: auto;
  width: 100%;
  color: rgb(39, 37, 37);
}

th {
  color: gray;
}

td {
  border: solid 1px gray;
  border-style: solid none;
  background-color: whitesmoke;
}
td:first-child {
  border-left-style: solid;
  border-top-left-radius: 10px;
  border-bottom-left-radius: 10px;
}

td:last-child {
  border-right-style: solid;
  border-bottom-right-radius: 10px;
  border-top-right-radius: 10px;
}
</style>
