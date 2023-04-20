<template>
  <div class="todo-list">
    <h1>Aplikasi Ekspedisi Fajar Andrean</h1>
    <form @submit.prevent="addTodo">
      <div>
        <label for="nama-paket">Nama Paket</label>
        <input type="text" id="nama-paket" v-model="newTodo" placeholder="Masukkan nama Paket..." />
      </div>
      <div>
        <label for="nama-pelanggan">Nama User Pengirim</label>
        <input type="text" id="nama-pelanggan" v-model="newPeminjam" placeholder="Masukkan nama User Pengirim..." />
      </div>
      <div>
        <label for="nama-penerima">Nama Penerima</label>
        <input type="text" id="nama-penerima" v-model="newPenerima" placeholder="Masukkan nama Penerima..." />
      </div>
      <div>
        <label for="tanggal-pengaduan">Tanggal Pengiriman</label>
        <input type="datetime-local" id="tanggal-pengaduan" v-model="newDate" />
      </div>
      <div>
        <label for="keterangan-pengaduan">Alamat Penerima</label>
        <textarea id="keterangan-pengaduan" v-model="newKeterangan" placeholder="Alamat"></textarea>
      </div>
      <div class="input-group">
        <button type="submit" class="tambahkan">Tambahkan</button>
      </div>
    </form>
    <h2>List Item</h2>
    <div class="tengah">
      <ul>
        <li v-for="(todo, index) in todos" :key="index">
          <input type="checkbox" v-model="todo.done" />
          <span>{{ todo.text }}</span>
          <span>{{ todo.date }}</span>
          <span :class="{ 'done': todo.done }">({{ todo.peminjam }})</span>
          <span :class="{ 'done': todo.done }">{{ todo.penerima }}</span>
          <span :class="{ 'done': todo.done }">{{ todo.keterangan }}</span>
          <button @click="removeTodo(index)">Remove</button>
        </li>
      </ul>
    </div>
    <footer>
      <p>&copy;Fajar Andrean Pratama.</p>
    </footer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: '',
      newPeminjam: '',
      newPenerima: '',
      newDate: '',
      newKeterangan: '',
      todos: []
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim().length === 0 || this.newPeminjam.trim().length === 0 || this.newPenerima.trim().length === 0 || !this.newDate || this.newKeterangan.trim().length === 0) {
        return;
      }
      this.todos.push({
        text: this.newTodo,
        peminjam: this.newPeminjam,
        penerima: this.newPenerima,
        done: false,
        date: new Date(this.newDate).toLocaleString(),
        keterangan: this.newKeterangan,
      });
      this.newTodo = '';
      this.newPeminjam = '';
      this.newPenerima = '';
      this.newDate = '';
      this.newKeterangan = '';
        },
      removeTodo (index) {
      this.todos.splice(index, 1);
    }
}
};
</script>
<style>
h1{
  color: #ffff;
}
h2{
  color: #ffff;
}
  .todo-list {
    font-family: sans-serif;
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
  }
  body {
    background-image: url(https://indonesialogistik.id/wp-content/uploads/2021/09/chuttersnap-9cCeS9Sg6nU-unsplash-1024x683-min.jpg);
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
  }
  .todo-list h1 {
    font-size: 36px;
    margin-bottom: 20px;
    text-align: center;
  }
  .todo-list form div {
  display: flex;
  flex-direction: column;
  margin-bottom: 10px;
}

.todo-list form div label {
  font-weight: bold;
  margin-bottom: 5px;
  color: #0B2447;
}

.todo-list form div input[type="text"], .todo-list form div textarea, .todo-list form div input[type="datetime-local"] {
  padding: 10px;
  font-size: 16px;
  border-radius: 5px;
  border: none;
  margin-right: 10px;
}

.todo-list form div textarea {
  height: 80px;
}

.todo-list form div button.tambahkan {
  margin-top: 10px;
  background-color: #00337C;
  color: #ffff;
  
}

.todo-list button.tambahkan:hover {
background-color: #3e8e41;
}
.todo-list ul {
list-style-type: none;
padding: 0;
}
.todo-list li {
display: flex;
align-items: center;
margin-bottom: 10px;
}
.todo-list li span {
margin-right: 10px;
color: #ffff;
}
.todo-list li .done {
text-decoration: line-through;
}
.tengah {
display: flex;
justify-content: center;
align-items: center;
}
.todo-list footer {
margin-top: 50px;
text-align: center;
}
.todo-list footer p {
font-size: 12px;
color: #ffff;
}

button{
  background-color:#EB455F;
  color: white;
}
button:hover {
background-color: #0B2447;
}
</style>