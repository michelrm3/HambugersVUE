<template>
  <div id="burger-table">
    <Message :msg="msg" v-show="msg"></Message>
    
    <div>
      <div id="burger-table-heading">
        <div class="order-id">#:</div>
        <div>Cliente:</div>
        <div>Pão:</div>
        <div>Carne:</div>
        <div>Opcionais:</div>
        <div>Ações:</div>
      </div>
    </div>
    <div id="burger-table-rows">
      <div class="burger-table-row" v-for="burger in burgers" :key="burger.id">
        <div class="order-number">{{ burger.id }}</div>
        <div>{{ burger.nome }}</div>
        <div>{{ burger.pao }}</div>
        <div>{{ burger.carne }}</div>
        <div>
          <ul>
            <li v-for="(opcional, index) in burger.opcionais" :key="index">
              {{ opcional }}
            </li>
          </ul>
        </div>
        <div>
          <select name="status" class="status" @change="updatedBurger($event, burger.id)">
            <option value="" disabled>Status:</option>
            <option
              v-for="s in status"
              :key="s.id"
              :value="s.tipo"
              :selected="burger.status == s.tipo"
            >
              {{ s.tipo }}
            </option>
          </select>
          <button class="delete-btn" @click="deleteBurger(burger.id)">
            Cancelar
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import Message from './Message.vue';
export default {
  components: { Message },
  name: "Dashboard",
  data() {
    return {
      burgers: null,
      burger_id: null,
      status: [],
      msg: null
    };
  },
  methods: {
    async getPedidos() {
      const req = await fetch("http://localhost:3000/burgers");

      const data = await req.json();

      this.burgers = data;

      //console.log(this.burgers);
      //resgatar status

      this.getStatus();
    },
    async getStatus() {
      const req = await fetch("http://localhost:3000/status");
      const data = await req.json();

      this.status = data;

      //console.log(data);
    },
    async deleteBurger(id) {
      //console.log(id)
      const req = await fetch(`http://localhost:3000/burgers/${id}`, {
        method: "DELETE",
      });

      const res = await req.json();

      //msg
      
      this.msg = `Pedido ${id} deletado com sucesso!`
      setTimeout(() => this.msg = "", 3000)

      this.getPedidos();
    },
    async updatedBurger(event, id) {
      const option = event.target.value;

      const dataJson = JSON.stringify({ status: option });
      const req = await fetch(`http://localhost:3000/burgers/${id}`, {
        method: "PATCH",
        headers: { "Content-Type": "application/json"},
        body: dataJson
      });
      const res = await req.json();

      this.msg = `O Pedido ${id} foi atualizado para "${res.status}"!`
      setTimeout(() => this.msg = "", 4000)
      
    },
  },
  mounted() {
    this.getPedidos();
  },
};
</script>

<style scoped>
#burger-table {
  max-width: 1200px;
  margin: 0 auto;
}

#burger-table-heading,
#burger-table-rows,
.burger-table-row {
  display: flex;
  flex-wrap: wrap;
}
#burger-table-heading {
  font-weight: bold;
  padding: 12px;
  border-bottom: 3px solid #0d0d0d;
}

#burger-table-heading div,
.burger-table-row div {
  width: 19%;
}
.burger-table-row {
  width: 100%;
  padding: 12px;
  border-bottom: 1px solid #383838;
}
#burger-table-heading .order-id,
.burger-table-row .order-number {
  width: 5%;
}

select {
  padding: 6px 3px;
  margin-right: 6px;
}
.delete-btn {
  background-color: #0d0d0d;
  color: #f2a74b;
  font-weight: bold;
  border: 2px solid #0d0d0d;
  padding: 8px;
  font-size: 12px;
  margin: 0 auto;
  cursor: pointer;
  transition: 0.5s;
}

.delete-btn:hover {
  background-color: transparent;
  color: #0d0d0d;
}
</style>
