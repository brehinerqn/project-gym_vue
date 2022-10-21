<template>
  <article id="tab6">
    <form class="form">
    <h1 style="color: aliceblue">new register client</h1>
    <div class="row">
      <form style="color: aliceblue">
        <div>
          <label for="">name</label><br />
          <input class="form-control" type="text" name="name" v-model="form.name" /><br />
        </div>
        <div>
          <label for="">edad</label><br />
          <input class="form-control" type="number" name="edad" v-model="form.edad" /><br />
        </div>
        <div>
          <label for="">peso</label><br />
          <input class="form-control" type="number" name="peso" v-model="form.peso" /><br />
        </div>
        <div>
          <label for="">nivel</label><br />
          <select class="form-control" name="nivel" v-model="form.nivel">
            <option value="Principiante">Principiante</option>
            <option value="Amateur" :selected="true">Amateur</option>
            <option value="Experto">Experto</option>
          </select>
        </div>
        <div>
          <label for="">tarifa</label><br />
          <select class="form-control"
            placeholder="seleciona tu tarifa"
            
            name="tarifa"
            v-model="form.tarifas_id"
          >
            <!-- LISTA TARIFAS   -->
            <option
              v-for="t in tarifa_list"
              :value="t.id"
              :key="'tarifa' + t.id"
              :selected="true"
            >
              {{ t.name }}
            </option>
            <!-- LISTA TARIFAS   -->
          </select>
        </div>
        <div>
          <label for="">email</label><br />
          <input class="form-control" type="email" name="email" v-model="form.email" /><br />
        </div>
        <div>
          <label for="">Password</label><br />
          <input class="form-control"
            type="password"
            name="password"
            v-model="form.password"
          /><br />
        </div>
        <div>
          <label for="">rol</label><br />
          <input class="form-control" type="number" name="roles_id" v-model="form.roles_id" /><br />
        </div>

        <button type="button" @click="registro()">register</button>
        <br />
      </form>
    </div>
  </form>
  </article>
</template>

<style scoped>
@import "../../assets/css/New_client.css";
</style>

<script>
export default {
  mounted() {
    this.get_tarifas();
  },
  data() {
    return {
      tarifa_list: [],
      user: {
        campanies_id: null,
        roles_id: null,
      },
      form: {
        name: null,
        edad: null,
        peso: null,
        nivel: null,
        email: null,
        roles_id: null,
        tarifas_id: null,
        campanies_id: null,
        password: null,
      },
    };
  },

  methods: {
    // obtener la lista de tarifas
    async get_tarifas() {
      this.user = JSON.parse(localStorage.user);
      const campanies_id = this.user.campanies_id;

      try {
        const rs = await this.axios.post(
          `api/company/tarifa/${campanies_id}`
          // {
          //   headers: { Authorization: "Bearer " + this.token },
          // }
          
        );
        this.tarifa_list = rs.data.tarifas_list;
        console.log(rs.data);
      } catch (e) {
        // console.log(e);
      }
    },

    async registro() {
      this.form.roles_id = this.user.roles_id;
      this.form.campanies_id = this.user.campanies_id;

      console.log(this.form);

      try {
        let response = await axios.post("/api/register/newClient", this.form);
        console.log(response);
      } catch (e) {
        console.log(e);
      }
    },
  },
};
</script>
