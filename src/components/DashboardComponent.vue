<template>
  <MessageComponent :message="message" v-show="message" />
  <div id="burger-table">
    <div>
      <div id="burger-table-heading">
        <div class="order-id">
          <div>Cliente:</div>
          <div>Pão:</div>
          <div>Carne:</div>
          <div>Opcionais:</div>
          <div>Ações:</div>
        </div>
      </div>
      <div id="burger-table-rows">
        <div
          class="burger-table-row"
          v-for="burger in burgers"
          :key="burger.id"
        >
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
            <select name="status" class="status" @change="updateBurger($event, burger.id)">
              <option value="">Selecione</option>
              <option
                v-for="s in status"
                :key="s.id"
                :value="s.tipo"
                :selected="burger.status == s.tipo"
              >
                {{ s.tipo }}
              </option>
            </select>
            <button class="delete-btn" @click="deleteBurger(burger.id)">Cancelar</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import MessageComponent from './MessageComponent.vue'

export default {
  name: 'DashboardComponent',
  data() {
    return {
      burgers: null,
      burger_id: null,
      status: [],
      message: null,
    }
  },
  components: {
    MessageComponent
  },
  methods: {
    async getPedidos() {
      const req = await fetch('http://localhost:3000/burgers')
      const data = await req.json()
      this.burgers = data

      this.getStatus()
    },
    async getStatus() {
      const reqStatus = await fetch('http://localhost:3000/status')
      const dataStatus = await reqStatus.json()
      this.status = dataStatus
    },
    async deleteBurger(id) {
      let w = window.confirm("Você realmente deseja cancelar o pedido?");
        if (w) {
      const req = await fetch(`http://localhost:3000/burgers/${id}`, {
        method: 'DELETE'
      });
      const res = await req.json()

      this.message = `Pedido ${id} cancelado com sucesso!`;
      setTimeout(() => {
        this.message = "";
      }, 3000);
      this.getPedidos()
    }
    },

    async updateBurger(event, id) {
      const option = event.target.value;
    
      const dataJSON = JSON.stringify({
        status: option
      }); 
      const req = await fetch(`http://localhost:3000/burgers/${id}`, {
        method: 'PATCH',
        headers: {
          'Content-Type': 'application/json'
        },
        body: dataJSON,
      });
      const res = await req.json()

      this.message = `Pedido ${id} atualizado para ${res.status}!`;
      setTimeout(() => {
        this.message = "";
      }, 3000);

      this.getPedidos()
    }
  },
  mounted() {
    this.getPedidos();
  }
}
</script>

<style scoped>
#buger-table {
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
  border-bottom: 3px solid #333;
}

#burger-table-heading div,
.burger-table-row div {
  width: 20%;
}

.burger-table-row {
  width: 100%;
  padding: 12px;
  border-bottom: 1px solid #ccc;
}

#buger-table-heading .order-id,
.burger-table-row .order-number {
  width: 5%;
}

select {
  padding: 12px 6px;
  margin-right: 12px;
}

.delete-btn {
  background-color: #222;
  color: #fcba03;
  font-weight: bold;
  border: 2px solid #222;
  padding: 10px;
  font-size: 16px;
  margin: 0 auto;
  cursor: pointer;
  transition: 0.5s;
}

.delete-btn:hover {
  background-color: transparent;
  color: #222;
}
</style>
