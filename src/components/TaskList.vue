<template>
  <div class="list" v-if="list.length">
    <div v-for="todo in list" :key="todo.id" class="todo">
      <label class="pointer" @click="$emit('changeCompl', todo.id)">
        <img :src="checkOn" alt="on" class="checkbox" v-if="todo.completed" />
        <img :src="checkOff" alt="off" class="checkbox" v-if="!todo.completed" />
        <span :class="{ line_through: todo.completed }">{{ todo.text }}</span>
      </label>
      <div class="todo__btns" v-if="!todo.completed">
        <button class="grey">
          <fa icon="gears" />
        </button>
        <button class="red" @click="$emit('deleter', todo.id)">
          <fa icon="trash" />
        </button>
      </div>
    </div>
  </div>
  <div v-else>У вас ещё нет задач данной категории.</div>
</template>

<script lang="js">
import checkOn from "@/assets/check_on.svg"
import checkOff from "@/assets/check_off.svg"
export default {
  data() {
    return {};
  },
  props: {
    list: {
      type: Array,
      required: true,
    },
  },
  components: {

  },
  setup() {
    return {
      checkOn, checkOff
    }
  },
  methods: {

  }
};
</script>

<style scoped>
.list {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.todo {
  border: 1px solid rgba(40, 40, 70, 0.1);
  background: rgba(41, 161, 156, 0.02);
  padding: 15px;
  border-radius: 10px;
  position: relative;

  display: flex;
  justify-content: space-between;
  align-items: center;
}

.todo span {
  position: relative;
}

.checkbox {
  display: none;
  position: absolute;
  left: 10px;
  top: 13px;
}

.todo__btns {
  display: none;
}

.todo:hover label {
  padding-left: 20px;
}

.todo:hover .checkbox,
.todo:hover .todo__btns {
  display: flex;
  gap: 10px;
}

.line_through {
  text-decoration: line-through;
}

.todo__btns button {
  border: none;
  background-color: transparent;
  cursor: pointer;
}


.grey {
  color: #282846;
}

.grey:hover {
 color: #414177;
}
.red {
  color: #F05454;
}

.red:hover {
  color: #d34b4b;
}
</style>