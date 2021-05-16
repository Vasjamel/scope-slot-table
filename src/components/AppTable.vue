<template>
  <div class="table-wrapper">
    <h1>Here will be the table</h1>
    <table>
      <thead>
        <tr>
          <th v-for="column in columns" :key="column.prop" :class="column.prop">
            {{ column.label }}
          </th>
        </tr>
      </thead>

      <tr v-for="each in dataArray" :key="each.personas">
        <td><slot name="dataCheckbox" /></td>
        <td><slot name="dataPreview" :preview="each.preview" /></td>
        <td><slot name="dataTags" :tags="each.tags" /></td>
        <td><slot name="dataTriggers" :triggers="each.triggers" /></td>
        <td><slot name="dataPersonas" :personas="each.personas" /></td>
        <td><slot name="dataLogic" :logicSets="each.logicSets" /></td>
        <td><slot name="dataCreated" :createdAt="each.createdAt" /></td>
        <td><slot name="dataUpdated" :updatedAt="each.updatedAt" /></td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      dataArray: [
        {
          preview:
            'Some dummy sasdas dsdfjdf sjkdf ksjdhf kjlszdhfkjl sdhfjkjdsjfj hdfkjghskhf usedhf kusdjhfj sdhfj   sdfhs dftring',
          tags: ['tag1', 'tag2', 'jk'],
          triggers: ['trigger1'],
          personas: ['persona1', 'persona8', 'persona16'],
          logicSets: ['logicSet1', 'logiclohi'],
          createdAt: new Date(2010, 9, 8),
          updatedAt: new Date(2015, 9, 7),
        },
        {
          preview: 'Some dummy string',
          tags: ['tag1', 'tag2'],
          triggers: ['trigger2', 'trig5'],
          personas: ['persona2'],
          logicSets: ['logicSet1'],
          createdAt: new Date(2017, 5, 5),
          updatedAt: new Date(2018, 5, 7),
        },
        {
          preview: 'Some dummy string',
          tags: ['tag1', 'tag2'],
          triggers: ['trigger3'],
          personas: ['persona3'],
          logicSets: ['logicSet1'],
          createdAt: new Date(2020, 4, 4),
          updatedAt: new Date(2021, 5, 5),
        },
        {
          preview: 'Some dummy string',
          tags: ['tag1', 'tag2'],
          triggers: ['trigger4'],
          personas: ['persona4'],
          logicSets: ['logicSet1'],
          createdAt: new Date(2020, 6, 12),
          updatedAt: new Date(2020, 11, 28),
        },
        {
          preview: 'Some dummy string',
          tags: ['tag1', 'tag2'],
          triggers: ['trigger5'],
          personas: ['persona5', 'persona99', 'persona77', 'personaaaaaa'],
          logicSets: ['logicSet1'],
          createdAt: new Date(2021, 1, 1),
          updatedAt: new Date(2021, 3, 8),
        },
        {
          preview: 'Some dummy string',
          tags: ['tag1', 'tag2'],
          triggers: ['trigger6'],
          personas: ['persona6'],
          logicSets: ['logicSet1'],
          createdAt: new Date(2021, 5, 1),
          updatedAt: new Date(2021, 5, 9),
        },
      ],
      columns: [
        { prop: 'select', label: '', width: 55 },
        { prop: 'preview', label: 'Preview', minWidth: 240 },
        { prop: 'tags', label: 'Tags', minWidth: 170 },
        { prop: 'triggers', label: 'Triggers', minWidth: 170 },
        { prop: 'personas', label: 'Personas', minWidth: 170 },
        { prop: 'logicSets', label: 'Logic sets', minWidth: 170 },
        { prop: 'createdAt', label: 'Created date', minWidth: 150 },
        { prop: 'updatedAt', label: 'Last modified', minWidth: 150 },
      ],
    }
  },
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
  border-radius: ;
  padding: 10px;
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

.preview {
  min-width: 240px;
}

.tags,
.triggers,
.personas,
.logicSets {
  min-width: 170px;
}

.createdAt,
.updatedAt {
  min-width: 150px;
}
</style>
