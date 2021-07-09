<template>
  <div @click="$emit('taskStateChanged', task)" class="task" :class="stateClass">
    <span @click.stop="$emit('taskDeleted', task)" class="close">x</span>
      <p>{{ task.name }}</p>
  </div>
</template>

<script>
export default {
    props: {
        task: { type: Object, required: true },
    },
    computed: {
        stateClass(){
            return {
                pending: this.task.pending,
                done: !this.task.pending
            }
        }
    }
}
</script>

<style>
    .task {
        position: relative;
        box-sizing: border-box;
        width: 200px;
        height: 80px;
        padding: 10px;
        border-radius: 8px;
        font-size: 2rem;
        font-weight: 300;
        cursor:pointer;
        user-select: none;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .pending {
        font-size: 20px;
        border-left: 12px solid #B73229;
        background-color: #F44336;
    }

    .pending .close {
        background-color: #B73229;
    }

    .done {
        font-size: 20px;
        color: #DDD;
        border-left: 12px solid #0A8F08;
        background-color: #4CAF50;
        text-decoration: line-through;
    }

    .done .close {
        background-color: #0A8F08;
    }

    .close{
        position: absolute;
        top: 5px;
        right: 5px;
        font-size:0.9rem;
        font-weight:600;
        width: 20px;
        height: 20px;
        border-radius: 50%;
        display: flex;
        justify-content:center;
        
    }

</style>