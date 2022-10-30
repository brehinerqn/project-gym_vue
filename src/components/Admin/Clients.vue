<template>
  <div class="contenedor">

    <article>


      <button id="btn" type="button" class="btn btn-secondary" data-bs-toggle="modal" data-bs-target="#staticBackdrop2">
        <img id="btns" src="../../assets/img/edit.png" />
      </button>

      <h1>Reguistro de clientes</h1>
      <table id="table">
        <thead>
          <tr>
            <th>Nombre</th>
            <th>age</th>
            <th>weight</th>
            <th>nivel</th>
            <th>email</th>
            <th>injuries</th>
            <th>start date</th>
            <th>finish date</th>
            <th>payment period</th>
            <th>price</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="c in clients" :key="'clients' + c.id">
            <td>{{ c.name }}</td>
            <td>{{ c.age}}</td>
            <td>{{ c.weight}}</td>
            <td>{{ c.nivel }}</td>
            <td>{{ c.email }}</td>
            <td>{{ c.injures }}</td>
            <td>{{ c.start_date}}</td>
            <td>{{ c.finish_date}}</td>
            <td>{{ c.rates}}</td>
            <td>{{ c.price}}</td>
            <td>{{ c.companies_id}}</td>

            <td>
              <button type="button" class="btn btn" data-bs-toggle="modal" data-bs-target="#staticBackdrop"
                @click="edit_clients(c)">
                <img id="btns" src="../../assets/img/edit.png" />
              </button>
            </td>
            <td>
              <!-- <button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#staticBackdrop1" >
                <img id="btns" src="../../assets/img/delete.png" />
              </button> -->
              <button type="button" class="btn" @click="borrar(c.id)">
                <img id="btns" src="../../assets/img/delete.png" />
              </button>
            </td>
          </tr>
        </tbody>
      </table>




    </article>





  </div>
  <!-- Modal  crear-->
  <div class="modal fade" id="staticBackdrop2" data-bs-backdrop="static" data-bs-keyboard="false" tabindex="-1"
    aria-labelledby="staticBackdropLabel" aria-hidden="true">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="staticBackdropLabel">Modal title</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">


          <form>
            <div>
              <label for="">name</label>
              <input type="text" name="name" v-model="form.name" />
            </div>
            <br>

            <div>
              <label for="">age</label>
              <input type="number" name="age" v-model="form.age" />
            </div>
            <br>
            <div>
              <label for="">weight</label>
              <input type="number" name="weight" v-model="form.weight" />
            </div>
            <br>
            <div>
              <label for="">nivel</label>
              <input type="text" name="nivel" v-model="form.nivel" />
            </div>
            <br>
            <div>
              <label for="">email</label>
              <input type="email" name="email" v-model="form.email" />
            </div>
            <br>
            <div>
              <label for="">injures</label>
              <input type="text" name="injures" v-model="form.injures" />
            </div>
            <br>
            <div>
              <label for="">injures</label>
              <input type="text" name="injures" v-model="form.injures" />
            </div>
            <br>
            <div>
              <label for="">start date</label>
              <input type="date" name="injures" v-model="form.start_date" />
            </div>
            <br>
            <div>
              <label for=""> finish date</label>
              <input type="date" name="injures" v-model="form.finish_date" />
            </div>
            <br>
            <div>
              <label for=""> payment period</label>
              <input type="text" name="injures" v-model="form.rates" />
            </div>
            <br>

            <article>
              <select class="form-select" aria-label="Default select example" aria-placeholder="seleciona tu periodo de pago"
              name="rates"
             >
                
                <option v-for=" t in rates_list" 
                :value="t.id"
                :key="'rates' + t.id"
                :selected="true"><p>{{t.name}}</p><p>{{t.price}}</p></option>
                
              </select>
            </article>
           




          </form>



        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
          <button type="button" class="btn btn-primary " @click="store()" data-bs-dismiss="modal"> created</button>
        </div>
      </div>
    </div>
  </div>
  <!-- Modal  editar-->
  <div class="modal fade" id="staticBackdrop" data-bs-backdrop="static" data-bs-keyboard="false" tabindex="-1"
    aria-labelledby="staticBackdropLabel" aria-hidden="true">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="staticBackdropLabel">Modal title</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">
          <form>
            <div>
              <label for="">name</label>
              <input type="text" name="name" v-model="clients_edit.name" />
            </div>
            <br>

            <div>
              <label for="">age</label>
              <input type="number" name="age" v-model="clients_edit.age" />
            </div>
            <br>
            <div>
              <label for="">weight</label>
              <input type="number" name="weight" v-model="clients_edit.weight" />
            </div>
            <br>
            <div>
              <label for="">nivel</label>
              <input type="text" name="nivel" v-model="clients_edit.nivel" />
            </div>
            <br>
            <div>
              <label for="">email</label>
              <input type="email" name="email" v-model="clients_edit.email" />
            </div>
            <br>
            <div>
              <label for="">injures</label>
              <input type="text" name="injures" v-model="clients_edit.injures" />
            </div>
            <br>
            <div>
              <label for="">start date</label>
              <input type="date" name="injures" v-model="clients_edit.start_date" />
            </div>
            <br>
            <div>
              <label for=""> finish date</label>
              <input type="date" name="injures" v-model="clients_edit.finish_date" />
            </div>
            <br>
            <div>
              <label for=""> payment period</label>
              <input type="text" name="injures" v-model="clients_edit.rates" />
            </div>
            <br>
            
              
            <br>


          </form>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" data-bs-dismiss="modal" @click="updated()">edit</button>

        </div>
      </div>
    </div>
  </div>



</template>
<style scoped>
@import "../../assets/css/clients.css";
</style>


<script>
export default {

  mounted() {

    this.get_rates();
    this.get_clients();
  },
  data() {
    return {
      clients: [],
      rates_list:[],
      clients_edit: {},
      form: {
        name: "",
        age: "",
        weight: "",
        nivel: "",
        email: "",
        injures: "",
        start_date: "",
        finish_date: "",
        rates: "",
        
        companies_id: ""

      },

    };

  },



  methods: {
    reset_form() {
      this.form = {
        name: "",
        age: "",
        weight: "",
        nivel: "",
        email: "",
        injures: "",
        start_date: "",
        finish_date: "",
        rates: "",
        companies_id: ""
      }
    },

    async get_clients() {
      try {
        let rs = await this.axios.get("/api/clients"
          // {
          //   headers: { Authorization: "Bearer " + this.token },
          // }
        );
        this.clients = rs.data.clients_list;
      } catch (e) {
        // console.log(e);
      }
    },

    async store() {

      this.form.companies_id = JSON.parse(localStorage.user).companies_id;
      console.log(this.form.companies_id)

      try {
        let response = await this.axios.post('/api/clients', this.form);
        this.get_clients();
        this.reset_form();

      }
      catch (e) {
        console.log(e)
      }
    },

    async get_rates(){
      this.user = JSON.parse(localStorage.user);
      const companies_id = this.user.companies_id;
      try{
        const rs = await this.axios.post(`api/companies/rates/${companies_id}`);
        this.rates_list = rs.data.rates_list;
        
      }catch(e){
console.log(e)
      }
    },

    edit_clients(c) {
      this.clients_edit = c;
    },

    async updated() {
      let id = this.clients_edit.id;
      console.log(id)
      await this.axios.put('/api/clients/' + id, this.clients_edit);
      this.get_clients();

    },

    async borrar(id) {

      console.log('rol :' + id);
      if (confirm('Seguro de eliminar?')) {
        await this.axios.delete("api/clients/" + id);
        this.get_clients();
      }

    }
  },
};
</script>
