<template>
  <AppTable :columns="columns" :dataArray="dataArray">
    <!-- column slots -->

    <template #select_column="{column}">
      {{ column.label }}
      <input type="checkbox" />
    </template>

    <template #preview_column="{column}">
      {{ column.label }}
    </template>

    <template #tags_column="{column}">
      {{ column.label }}
    </template>

    <template #triggers_column="{column}">
      {{ column.label }}
    </template>

    <template #personas_column="{column}">
      {{ column.label }}
    </template>

    <template #logicSets_column="{column}">
      {{ column.label }}
    </template>

    <template #createdAt_column="{column}">
      {{ column.label }}
    </template>

    <template #updatedAt_column="{column}">
      {{ column.label }}
    </template>

    <!-- below are row slots -->

    <template #select_row>
      <div class="inputField">
        <input type="checkbox" />
      </div>
      <div>...</div>
    </template>

    <template #preview_row="{row}">
      <div v-if="row.preview">{{ row.preview }}</div>
    </template>

    <template #tags_row="{row}">
      <div v-if="row.tags">
        <div v-for="tag in row.tags" :key="tag" class="tags">
          <div>
            {{ tag }}
          </div>
        </div>
      </div>
    </template>

    <template #triggers_row="{row}">
      <div v-if="row.triggers">
        <div v-if="row.triggers.length > 1 && !row.triggers.show">
          <div>{{ row.triggers[0] }}</div>
          <div @click.prevent="showAll(row.triggers)">
            <a href=""> + {{ row.triggers.length - 1 }} more </a>
          </div>
        </div>

        <div v-else>
          <div v-for="trigger in row.triggers" :key="trigger">
            {{ trigger }}
          </div>
        </div>
      </div>
    </template>

    <template #personas_row="{row}">
      <div v-if="row.personas">
        <div v-if="row.personas.length > 1 && !row.personas.show">
          <div>{{ row.personas[0] }}</div>
          <div @click.prevent="showAll(row.personas)">
            <a href=""> + {{ row.personas.length - 1 }} more </a>
          </div>
        </div>
        <div v-else v-for="each in row.personas" :key="each">
          {{ each }}
        </div>
      </div>
    </template>

    <template #logicSets_row="{row}">
      <div v-if="row.logicSets">
        <div v-if="row.logicSets.length > 1 && !row.logicSets.show">
          <div>{{ row.logicSets[0] }}</div>
          <div @click.prevent="showAll(row.logicSets)">
            <a href=""> + {{ row.logicSets.length - 1 }} more </a>
          </div>
        </div>

        <div v-else v-for="each in row.logicSets" :key="each">
          {{ each }}
        </div>
      </div>
    </template>

    <template #createdAt_row="{row}">
      {{
        row.createdAt.toLocaleDateString('en-US', {
          month: 'short',
          day: '2-digit',
          year: 'numeric',
        })
      }}
    </template>

    <template #updatedAt_row="{row}">
      <div>
        {{
          row.updatedAt.toLocaleDateString('en-US', {
            month: 'short',
            day: '2-digit',
            year: 'numeric',
          })
        }}
      </div>
    </template>
  </AppTable>
</template>

<script>
import AppTable from './components/AppTable'
export default {
  components: {
    AppTable,
  },
  methods: {
    showAll(data) {
      data.show = true
    },
  },
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

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #22486e;
  margin-top: 60px;
}

.tags div {
  margin: 4px 40px;
  border-radius: 8px;
  background-color: rgb(191, 207, 236);
  color: blue;
  border: 1px solid blue;
}

.inputField {
  display: block;
  width: 55px;
}

a,
a:active,
a:visited {
  color: blue;
  text-decoration: none;
  font-size: small;
  text-align: left;
}
</style>
