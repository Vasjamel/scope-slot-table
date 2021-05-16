<template>
  <AppTable>
    <template #dataCheckbox>
      <div class="inputField">
        <input type="checkbox" />
      </div>
      <div>...</div>
    </template>

    <template #dataPreview="{preview}">
      <div v-if="preview">{{ preview }}</div>
    </template>

    <template #dataTags="tags">
      <div v-if="tags">
        <div v-for="tag in tags" :key="tag" class="tags">
          <div v-for="everyTag in tag" :key="everyTag">
            {{ everyTag }}
          </div>
        </div>
      </div>
    </template>

    <template #dataTriggers="{triggers}">
      <div v-if="triggers">
        <div v-if="triggers.length > 1 && !triggers.show">
          <div>{{ triggers[0] }}</div>
          <div @click.prevent="showAll(triggers)">
            <a href=""> + {{ triggers.length - 1 }} more </a>
          </div>
        </div>
        <div v-else>
          <div v-for="trigger in triggers" :key="trigger">
            {{ trigger }}
          </div>
        </div>
      </div>
    </template>

    <template #dataPersonas="personas">
      <div v-if="personas.personas">
        <div v-if="personas.personas.length > 1 && !personas.personas.show">
          <div>{{ personas.personas[0] }}</div>
          <div @click.prevent="showAll(personas.personas)">
            <a href=""> + {{ personas.personas.length - 1 }} more </a>
          </div>
        </div>
        <div v-else v-for="each in personas.personas" :key="each">
          {{ each }}
        </div>
      </div>
    </template>

    <template #dataLogic="{logicSets}">
      <div v-if="logicSets">
        <div v-if="logicSets.length > 1 && !logicSets.show">
          <div>{{ logicSets[0] }}</div>
          <div @click.prevent="showAll(logicSets)">
            <a href=""> + {{ logicSets.length - 1 }} more </a>
          </div>
        </div>

        <div v-else v-for="each in logicSets" :key="each">
          {{ each }}
        </div>
      </div>
    </template>

    <template #dataCreated="createdAt">
      <div v-for="each in createdAt" :key="each">
        {{ createdAt.createdAt.toLocaleDateString() }}
      </div>
    </template>

    <template #dataUpdated="updatedAt">
      <div>{{ updatedAt.updatedAt.toLocaleDateString() }}</div>
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
