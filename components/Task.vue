<template>
<div 
  class="flex items-center justify-between p-4 rounded-lg mb-4 bg-[#342F4E]"
>
  <!-- Apply opacity-70 and line-through only to the task content -->
  <div 
    @click="toggleDone(task)" 
    class="text-white cursor-pointer"
    :class="{ 'opacity-70 line-through': task.done }"
  >
    {{ task.content }}
  </div>
  
  <div class="flex space-x-2 buttons">
    <button 
      class="px-4 py-2 text-sm font-bold uppercase rounded-lg bg-green-400 text-black hover:bg-green-500 transition-all"
      @click="toggleDone(task)"
    >
      {{ task.done ? 'Undo' : 'Done' }}
    </button>
    <button 
      class="px-4 py-2 text-sm font-bold uppercase rounded-lg bg-red-500 text-white hover:bg-red-600 transition-all delete" 
      @click="removeTask(task)"
    >
      Delete
    </button>
  </div>
</div>

</template>

<script>
export default {
    props:['task'],
    methods:{
        toggleDone(){
            this.$store.commit('TOGGLE_TASK', this.task);
        },
        removeTask(){
            this.$store.commit('REMOVE_TASK',this.task);
        }
    }

}
</script>

<style>

</style>