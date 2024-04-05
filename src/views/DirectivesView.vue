<script>
  export default {
    // Переменные
    data() {
      return {
        message: 'Приветствую вас на курсе по изучению фреймворка Vue 3!',
        login: null,
        seen: true,
        fruits: ["Яблоко", "Апельсин", "Банан", "Груша", "Папайя"],
        students: [{
          fio: 'Евсеев Дмитрий Витальевич',
          birth: '04.11.2005',
          sex: 'Мужской',
        },{
          fio: 'Буйкин Андрей Анатольевич',
          birth: '20.12.2005',
          sex: 'Мужской',
        },{
          fio: 'Шейкина Елизавета Викторовна',
          birth: '23.04.2005',
          sex: 'Женский',
        }],
        bind_img: "https://fanibani.ru/wp-content/uploads/2022/12/http-vestikavkaza-ru-upload-2019-01-02-154644941.jpeg",
        bind_value: "Милый енот полоскун",
      }
    },
    // Методы
    methods: {
      click_green() {
        alert("Вы нажали на первый батон");
      },
      click_red() {
        alert("Вы нажали на второй батон");
      }
    }
  }
</script>

<template>
  <section class="m-4">
    <h2 class="text-center">{{message}}</h2>
    <h3>Директива v-model</h3>
    <form action="#" method="post">
      <input v-model="login" class="p-1" type="text" name="login" value="" placeholder="Введите логин">
      <p>Ваш логин: {{login}}</p>
    </form>

    <h3>Директива v-if</h3>
    <div v-if="seen" >
      <p>Этот блок видно, так как переменная seen - истина</p>
      <p>А второй блок убран из DOM-дерева</p>
    </div>
    <div v-if="!seen" >
      <p>Этот блок не видно, так как переменная seen - ложь</p>
      <p>Он убран из DOM-дерева</p>
    </div>

    <h3>Директива v-show</h3>
    <div v-show="seen">
      <p>Этот блок видно, так как переменная seen - истина</p>
      <p>А второй блок скрыт с помощью свойства display</p>
    </div>
    <div v-show="!seen">
      <p>Этот блок не видно, так как переменная seen - ложь</p>
      <p>Он убран из DOM-дерева</p>
      <p>К нему добавлен атрибут style="display: none;"</p>
    </div>

    <h3>Директива v-for (массив)</h3>
    <div>
      <p>Список фруктов:</p>
      <ol>
        <li v-for="fruit in fruits">{{fruit}}</li>
      </ol>
    </div>

    <h3>Директива v-for (массив объектов)</h3>
    <div>
      <p>Список студентов:</p>
      <ol>
        <li v-for="student in students">
          ФИО: <b>{{student.fio}}</b><br/>
          Дата рождения: {{student.birth}}<br/>
          Пол: {{student.sex}}<br/>
        </li>
      </ol>
    </div>

    <h3>Директива v-bind</h3>
    <div>
      <img v-bind:src="bind_img" alt="Хуня:)" width="300">
      <br/>
      <input type="text" v-bind:value="bind_value" disabled>
    </div>

    <h3>Директива v-on</h3>
    <div>
      <button class="btn btn-success" v-on:click="click_green">Батон 1</button>
      <button class="btn btn-danger m-1" @click="click_red">Батон 2</button>
    </div>

  </section>
</template>

<style scoped>
  input {
    width: 300px;
  }
</style>