<template>
  <div id="app">
    <b-container>
      <b-row class="justify-content-md-center pb-4">
        <b-col cols="8" class="bg-info">
          <h1 class="text-center">Bazar List</h1>
          <div>
            <form @submit.prevent="addItem" action="" class="mb-4">
              <label for="">Enter Your List:</label>
              <input type="text" v-model="newItem">
              <label for="">Price:</label>
              <input type="number" v-model="newPrice">
             <input type="submit" value="Submit"> 
            </form>
            <div>
              <ul class="list-group">
                <div class="col-md-6"></div>
                <li class="list-group-item">List-Item 
                  <span class="spn">Price</span>
                  <span class="remove">Remove</span> 
                  </li>
                <li class="list-group-item" v-for="(item,index) in items" :key="index">
                  {{ item.ListItem}} 
                  <span class="spn">
                    {{ item.Price}}
                  </span>
                  <span><button class="btn btn-danger" @click="removeItem(index)">X</button></span>
                </li>
                <li class="list-group-item">Total: {{ total }}</li>
              </ul>
          </div>
          </div>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      items: [
          { ListItem: 'Rice', Price: 50 },
        ],
        newItem:'',
        newPrice:''
    }
  },
  methods:{
    addItem(){
      this.items.push({
        ListItem:this.newItem,
        Price:this.newPrice
      })
    },
    removeItem(index){
      this.items.splice(index,1)
    }
  },
  computed:{
    total(){
      var total = 0;
      this.items.forEach(item =>{
        total +=parseFloat(item.Price) 
      });
      return total
    }
  }

}
</script>

<style>
.spn{
    display: inline-block;
    margin-left: 250px;
}
button{
  float:right
}
input{
  padding: 5px;
  border-radius: 5px;
  border: none;
}
.remove{
  float: right;
}
</style>
