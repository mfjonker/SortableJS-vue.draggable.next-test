<template>
  <div class="row">
    <div class="col-3">
      <h3>Draggable 1</h3>
      <draggable
        class="list-group"
        :list="list1"
        :data-section=0
        group="people"
        :move="onMove"
        itemKey="name"
      >
        <template #item="{ element, index }">
          <div class="list-group-item">{{ element.name }} {{ index }}</div>
        </template>
      </draggable>
    </div>

    <div class="col-3">
      <h3>Draggable 2</h3>
      <draggable
        class="list-group"
        :list="list2"
        :data-section=1
        group="people"
        :move="onMove"
        itemKey="name"
      >
        <template #item="{ element, index }">
          <div class="list-group-item">{{ element.name }} {{ index }}</div>
        </template>
      </draggable>
    </div>

    <rawDisplayer class="col-3" :value="list1" title="List 1" />
    <rawDisplayer class="col-3" :value="list2" title="List 2" />

  </div>
</template>
<script>

import draggable from "vuedraggable";
import rawDisplayer from "./raw-displayer";

export default {
  name: "two-lists",
  order: 1,
  components: {
    draggable,
    rawDisplayer
  },
  data() {
    return {
      list1: [
        { name: "John", id: 1 },
        { name: "Joao", id: 2 },
        { name: "Jean", id: 3 },
        { name: "Gerard", id: 4 }
      ],
      list2: [
        { name: "Juan", id: 5 },
        { name: "Edgard", id: 6 },
        { name: "Johnson", id: 7 }
      ]
    };
  },
  methods: {
    onMove: function(evt) {
      console.log('move from section: ' + evt.from.dataset.section + ' index: ' + evt.draggedContext.index + ' to section: ' + evt.to.dataset.section + ' index: ' + evt.draggedContext.futureIndex)
    },
    onChange: function(evt) {
      console.log(evt);
    }
  }
};
</script>