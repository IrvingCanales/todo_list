<template>
  <div class="container">
      <h1>TO-DO list</h1>
      <div class="row">
          <div class="col-sm">
            <input
                v-model="newTodo"
                type="text"
                class="form-control"
                placeholder="Create a new to-do..."
                @keyup.enter="addTodo()"
                />            
          </div>
      </div>
      <br>
        <div class="row">
            <div class="col-sm">
                <ul id="example-1" v-if="list.length>0">
                    <li v-for="(item,index) in list" :key="index" >
                        <button
                        class="btn border-0 flex-grow-1 text-left shadow-none"
                        @click="underLine(index)"
                        :class="{'completed':item.done }"
                        >
                        <span>{{ item.description }}</span>
                        </button>
                        <button 
                        class="btn btn-outline-danger border-0"
                        @click="deletelist(index)"
                        >
                            <span class="fa fa-trash"></span>
                        </button>
                    </li>
                </ul>
            </div>
        </div>
  </div>
</template>

<script>
export default {
    data(){
        return{
            newTodo:'',            
            list: [
                
            ]
            
        }
    },
    methods:{
        addTodo(){                        
            this.list.push( {description: this.newTodo, done: false} )
            this.newTodo = ''
        },
        underLine(index){            
            this.list[index].done = true
        },
        deletelist(index){
            this.list.splice(index, 1)
        }
    }

}
</script>

<style>
.completed {
  text-decoration: line-through;
}
</style>