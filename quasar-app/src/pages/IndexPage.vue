<template>
  <q-page class="flex flex-center">
    <!-- <img
      alt="Quasar logo"
      src="~assets/quasar-logo-vertical.svg"
      style="width: 200px; height: 200px"
    > -->

    <q-card dark bordered class="bg-grey-9 my-card">
      <q-card-section>
        <div class="text-h6">My list name</div>
      </q-card-section>

      <q-separator dark inset />

      <q-card-section>
        <div>
          <q-input outlined v-model="myTask" label="Add row to list">
            <template v-slot:append>
              <q-btn round dense flat icon="add" @click="addItem" />
            </template>
          </q-input>
        </div>
      </q-card-section>

      <q-card-section v-if="myList.length > 0">
        <div v-for="(item, index) in myList" :key="index">
          {{ item.value }}
          <q-btn round dense flat icon="close" @click="removeItem(index)" />
        </div>
      </q-card-section>

      <q-card-section v-else>
        <div>The list is empty.</div>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "IndexPage",
  data() {
    return {
      myTask: "",
      myList: [{ value: "text 1" }, { value: "text 2" }, { value: "text 3" }],
    };
  },
  methods: {
    addItem() {
      this.myList.push({ value: this.myTask });
    },
    removeItem(index) {
      this.myList.splice(index, 1);
    },
  },
});
</script>
