<script setup>
import HelloWorld from './components/HelloWorld.vue';
</script>

<template>
  <div class="row">
    <div class="md-col-12">
      <div id="table" class="p-3">
        <table class="table text-center text-middle">
          <tr>
            <td rowspan="3" class="table-success align-middle">0</td>
            <td class="table-danger">3</td>
            <td class="table-secondary">6</td>
            <td class="table-danger">9</td>
            <td class="table-danger">12</td>
            <td class="table-secondary">15</td>
            <td class="table-danger">18</td>
            <td class="table-danger">21</td>
            <td class="table-secondary">24</td>
            <td class="table-danger">27</td>
            <td class="table-danger">30</td>
            <td class="table-secondary">33</td>
            <td class="table-danger">36</td>
          </tr>
          <tr>
            <td class="table-secondary">2</td>
            <td class="table-danger">5</td>
            <td class="table-secondary">8</td>
            <td class="table-secondary">11</td>
            <td class="table-danger">14</td>
            <td class="table-secondary">17</td>
            <td class="table-secondary">20</td>
            <td class="table-danger">23</td>
            <td class="table-secondary">26</td>
            <td class="table-secondary">29</td>
            <td class="table-danger">32</td>
            <td class="table-secondary">35</td>
          </tr>
          <tr>
            <td class="table-danger">1</td>
            <td class="table-secondary">4</td>
            <td class="table-danger">7</td>
            <td class="table-secondary">10</td>
            <td class="table-secondary">13</td>
            <td class="table-danger">16</td>
            <td class="table-danger">19</td>
            <td class="table-secondary">22</td>
            <td class="table-danger">25</td>
            <td class="table-secondary">28</td>
            <td class="table-secondary">31</td>
            <td class="table-danger">34</td>
          </tr>
        </table>
      </div>
    </div>
  </div>

  <div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>
  <HelloWorld msg="Vite + Vue" />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
