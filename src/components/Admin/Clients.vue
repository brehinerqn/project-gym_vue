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
            <td>{{ c.age }}</td>
            <td>{{ c.weight }}</td>
            <td>{{ c.nivel }}</td>
            <td>{{ c.email }}</td>
            <td>{{ c.injures }}</td>
            <td>{{ c.start_date }}</td>
            <td>{{ c.finish_date }}</td>
            <td>{{ c.rates }}</td>
            <td>{{ c.price }}</td>
            <td>{{ c.companies_id }}</td>

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
          <h5 class="modal-title" id="staticBackdropLabel" style="color:white; "> New client</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">


          <form>
            <div id="izq">
              <div class="form-floating mb-3">
                <input type="text" name="name" v-model="form.name" class="form-control" id="floatingInput1">
                <label for="floatingInput1">name</label>
                <span style="color:aliceblue" v-if="errors.name"> {{ errors.name }}</span>
              </div>
              <div class="form-floating mb-3">
                <input type="email" name="email" v-model="form.email" class="form-control" id="floatingInput2"
                  placeholder="name@example.com">
                <label for="floatingInput2"> email</label>
                <span style="color:aliceblue" v-if="errors.email"> {{ errors.email }}</span>
              </div>
              <div class="form-floating mb-3">
                <input type="password" name="password" v-model="form.password" class="form-control" id="floatingInput3"
                  placeholder="password">
                <label for="floatingInput3"> password</label>
                <span style="color:aliceblue" v-if="errors.password"> {{ errors.password }}</span>
              </div>
              <div class="form-floating mb-3">
                <input type="password" name="password" v-model="form.password_confirmation" class="form-control"
                  id="floatingInput4" placeholder="password_confirmation">
                <label for="floatingInput4">password confirmation</label>
                <span style="color:aliceblue" v-if="errors.password_confirmation">
                  {{ errors.password_confirmation }}</span>
              </div>
              <div class="form-floating mb-3">
                <input type="number" name="age" v-model="form.age" class="form-control" id="floatingInput5"
                  placeholder="">
                <label for="floatingInput5">age</label>
                <span style="color:aliceblue" v-if="errors.age"> {{ errors.age }}</span>
              </div>
              <div class="form-floating mb-3">
                <input type="number" name="weight" v-model="form.weight" class="form-control" id="floatingInput6"
                  placeholder="">
                <label for="floatingInput6"> weight</label>
                <span style="color:aliceblue" v-if="errors.weight"> {{ errors.weight }}</span>
              </div>


            </div>


            <div id="dere">
              <div class="form-floating mb-3">
                <input type="text" name="nivel" v-model="form.nivel" class="form-control" id="floatingInput7"
                  placeholder="">
                <label for="floatingInput7"> nivel</label>
                <span style="color:aliceblue" v-if="errors.nivel"> {{ errors.nivel }}</span>
              </div>

              <div class="form-floating mb-3">
                <input type="text" name="injures" v-model="form.injures" class="form-control" id="floatingInput8"
                  placeholder="">
                <label for="floatingInput8"> injures</label>
                <span style="color:aliceblue" v-if="errors.injures"> {{ errors.injures }}</span>
              </div>
              <div class="form-floating mb-3">
                <input type="date" name="injures" v-model="form.start_date" class="form-control" id="floatingInput9"
                  placeholder="">
                <label for="floatingInput9"> start date</label>
                <span style="color:aliceblue" v-if="errors.start_date"> {{ errors.start_date }}</span>
              </div>
              <div class="form-floating mb-3">
                <input type="date" name="injures" v-model="form.finish_date" class="form-control" id="floatingInput0"
                  placeholder="">
                <label for="floatingInput0"> finish date</label>
                <span style="color:aliceblue" v-if="errors.finish_date"> {{ errors.finish_date }}</span>
              </div>
            </div>

          </form>



        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" data-bs-dismiss="modal" data-bs-toggle="modal"
            data-bs-target="#staticBackdrop3">select pago</button>
          <!-- <button type="button" class="btn btn-primary " @click="store()" data-bs-dismiss="modal"> created</button> -->
        </div>
      </div>
    </div>
  </div>


  <!-- Modal  rates -->
  <div class="modal fade" id="staticBackdrop3" data-bs-backdrop="static" data-bs-keyboard="false" tabindex="-1"
    aria-labelledby="staticBackdropLabel" aria-hidden="true">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="staticBackdropLabel">Modal title</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">
          <form>
            <article id="article" v-for="t in rates_list" :key="'rates_list' + t.id" @click="select_rate(t.id)">
              <p>
                {{ t.name }}
              </p>
              <p>
                {{ t.price }}
              </p>

            </article>


          </form>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" @click="store()">crear</button>

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

    if (localStorage.user) {
      this.user = JSON.parse(localStorage.user);
      this.form.user_id = this.user.id;
    }
    else {
      //se va para el login
    }

    this.get_rates();
    this.get_clients();
    console.log(this.form)
  },
  data() {
    return {
      user: null,
      clients: [],
      rates_list: [],
      modal_create: null,
      modal_rates: null,
      errors: {},
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
        rates_id: "",
        password: "",
        password_confirmation: "",
        companies_id: "",
        user_id: null,

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
    error_message(e) {
      this.errors = {};
      if (e.response.data.errors) this.errors = e.response.data.errors;
      else if (e.response.data.message == "Unauthenticated.") {
        this.$router.push({
          name: "Admin",
          params: {
            message: "datos incorrestos vuelve a intentarlo"
          },
        });
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
      const modal1 = document.getElementById("staticBackdrop2");
      const modal2 = document.getElementById("staticBackdrop3");
      this.modal_create = bootstrap.Modal.getInstance(modal1);
      this.modal_rates = bootstrap.Modal.getInstance(modal2);

      this.form.companies_id = JSON.parse(localStorage.user).companies_id;
      console.log(this.form.companies_id)
      console.log(this.form)



      try {
        let response = await this.axios.post('/api/clients', this.form);
        this.get_clients();
        this.reset_form();
        this.modal_create.hide();
        this.modal_rates.hide();
      }
      catch (e) {

        console.log(e)
        this.error_message(e);
        this.modal_rates.hide();
        this.modal_create.show();

      }
    },
    //tarifa

    async get_rates() {
      const companies_id = this.user.companies_id;
      try {
        const rs = await this.axios.get(`api/companies/rates/${companies_id}`);
        this.rates_list = rs.data.rates_list;
        console.log(rs.data)

      } catch (e) {
        console.log(e)
      }
    },

    select_rate(id) {
      this.form.rates_id = id
      alert(this.form.rates_id)
    },

    //final tarifa


    edit_clients(c) {
      this.clients_edit = c;
    },

    async updated(payment_id) {
      await this.axios.put(`/api/clients/${payment_id}`, this.clients_edit);
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
