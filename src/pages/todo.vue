<script >
import CompleteTask from '../view/complete-task.vue'
import Newtodo from '../view/newtodo.vue'
import Todayview from '../view/todayview.vue'
import Wether from '../view/wether.vue'

export default{
  components: { Newtodo, Wether, Todayview, CompleteTask},

  data(){
  return{
    tab:"todo",
    active: true,
    bgTab:"light"
  }
   
  },


}



</script>

<template>
  <div class="p-10 pr-0 todos-content-wrapper">

    <nav class="navBar grid grid-cols-3  pl-5 pt-1 ">

      <div>
        <h1 class="font-bold text-2xl">Taskr.oi</h1>
      </div>

      <div class="  gap-10   flex pl-5">
        <div class="todo-nav  tab"  :class="{ active: tab === 'todo' }" @click="tab ='todo'" >Todo</div>
        <p class="complete-tasks  tab" :class="{ active: tab === 'Complete-Task' }" @click="tab ='Complete-Task'">Complete Task</p>
        
      </div>

      <div class=" float-right gap-4">

        <div class="float-right pr-2">
          <button  @click="bgTab='light'" >
            <i class='fas fa-circle' v-if="bgTab=== 'dark'"></i>
          </button>

          <button @click="bgTab='dark'" >
            <i class='far fa-circle'   v-if="bgTab=== 'light' "></i>
          </button>
          
      
        </div>
        
         
        <button class="float-right pr-7">
          <i class="fa fa-user-circle" style="font-size:24px"></i>
        </button>
 
      </div>
    </nav>

    <section class="content">
        <div class="grid grid-cols-6">
            <div class="p-5 pl-2 relative font-semibold col-start-1 col-end-3">
                <div class="side-nav tab" :class="{ active: tab == 'today' }" @click="tab = 'today'" >Today </div>
                <div class="side-nav tab" :class="{ active: tab == 'weather' }" @click="tab = 'weather'">weather </div>
                <p class="setting-button  "  v-if="tab ==='todo'">setting</p>
              
                <div class="nav-top" >
                  <div class="todo-nav  side-nav tab"  :class="{ active: tab === 'todo' }" @click="tab ='todo'" >Todo</div>
                  <p class=" side-nav  tab" :class="{ active: tab === 'Complete-Task' }" @click="tab ='Complete-Task'">Complete Task</p> 
                </div>



                
                
            </div>



               
            <div class="  condition-content col-start-3 col-end-7 ">
                
                <div v-if="tab ==='today'">
                    <Todayview/>
                </div>
                <div v-if="tab ==='todo'">
                    <Newtodo/>
                </div>
             
                <div  v-if="tab ==='weather'">
                    <Wether/>
                </div>

                <div v-if="tab === 'Complete-Task'">
                  <CompleteTask/>

                </div>

             
            </div>

        </div>
    </section>
  </div>

 
</template>


<style scoped>
.todos-content-wrapper{
    margin-top:2%;
}
.navBar {
  background: white;
  height: 45px;
    padding: 9px 11px;
  border-radius: 10px ;
  top:10%;
 
}
.tab.active {
    color: #9333ea;
    font:bold;
    font-size: 1.1em;
    border:5px soild #1d0930;
  
  }
  .tab{
    font:200p

  }

h1 {
  color: #9333ea;
}
p{
    color: rgb(105, 105, 105);
}

.side-nav{
    padding: 10px;
    border-radius:5px;
}
.complete-tasks{
  font-size: 0.9em;
  width: 20px;

}
.side-nav:hover{
    background: #ca92ff;;
    color: #f9f6fd;
}

.setting-button{
    position: absolute;
    bottom: 10px;
     margin-top: 5%;
    font: bold;
    padding-left: 5px;
}

@media only screen and (max-width: 600px) {
 
  .navBar {
 display: none;
}
.condition-content{
 width: 100px;
}
.nav-top{
display: block;
}
.content{
  margin-top: 15%;
  position: absolute;
  left: 0px;
}
.side-nav{
  font-size: 0.8em;

}
}
/* Small devices (portrait tablets and large phones, 600px and up) */
@media only screen and (min-width: 600px) {


  .heading{
    margin-top: 5%;
  }
  .navBar {
 display: none;
}
.side-nav{
  font-size: 0.9em;

}

}

/* Medium devices (landscape tablets, 768px and up) */
@media only screen and (min-width: 768px) {

  .navBar {
 display: grid;
 
}
.nav-top{
display: none;
}
.complete-tasks{
width: 250px;

}
}

/* Large devices (laptops/desktops, 992px and up) */
@media only screen and (min-width: 992px) {

  .heading{
    margin-top: 55%;
  }
}


</style>