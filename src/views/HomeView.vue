<script>
import { nanoid } from "nanoid";
import draggable from "vuedraggable";

export default {
  data: () => ({
    tasks: [
      {
        name: "col1",
        id: nanoid(),
        content: [
          { id: nanoid(), label: "name1", description: "desc1" },
          { id: nanoid(), label: "name12", description: "desc12" },
          { id: nanoid(), label: "name12", description: "desc12" },
        ],
      },
      {
        name: "col2",
        id: nanoid(),
        content: [
          { id: nanoid(), label: "name1", description: "desc1" },
          { id: nanoid(), label: "name12", description: "desc12" },
          { id: nanoid(), label: "name12", description: "desc12" },
        ],
      },
      {
        name: "col3",
        id: nanoid(),
        content: [
          { id: nanoid(), label: "name1", description: "desc1" },
          { id: nanoid(), label: "name12", description: "desc12" },
          { id: nanoid(), label: "name12", description: "desc12" },
        ],
      },
    ],
  }),
  components: {
    draggable,
  },
};
</script>

<template>
  <div class="main-content">
    <div v-for="col in tasks" :key="col.id" class="task-col">
      <div class="col-name">{{ col.name }}</div>
      <draggable
        itemKey="id"
        :list="col.content"
        tag="div"
        group="tasks"
        handle=".drag-handle"
      >
        <template #item="{ element }">
          <div class="task-element">
            <div class="drag-handle">::</div>
            <div class="task-name">{{ element.label }}</div>
            <div class="task-desc">{{ element.description }}</div>
          </div>
        </template>
      </draggable>
    </div>
  </div>
</template>

<style lang="scss">
.main-content {
  display: flex;
  padding: 24px;
  .task-col {
    padding: 8px;
    border: 1px solid gray;
    border-radius: 4px;
    width: 300px;
    max-width: 300px;
    &:not(:last-child) {
      margin-right: 12px;
    }
    .col-name {
      margin-bottom: 8px;
    }
    .task-element {
      position: relative;
      padding: 8px;
      border: 1px solid black;
      border-radius: 4px;
      &:not(:last-child) {
        margin-bottom: 4px;
      }
      .drag-handle {
        cursor: pointer;
        position: absolute;
        right: 0;
        top: 0;
        width: 24px;
        height: 24px;
        display: flex;
        justify-content: center;
        align-items: center;
      }
    }
  }
}
</style>
