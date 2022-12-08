<script setup>
import { ref } from 'vue';

defineProps({
  msg: String,
});

let id = 0;

let draws = ref([]);
function draw(number) {
  draws.value.push({
    id: id++,
    number: number,
    created_at: new Date().toLocaleTimeString(),
  });
}
function removeDraw(number) {
  draws.value = draws.value.filter((t) => t !== number);
}

function clearDraw() {
  if (!confirm('are you sure?')) {
    return;
  }
  draws.value = [];
}

function dozen(number) {
  if (1 <= number && number <= 12) {
    return 1;
  } else if (13 <= number && number <= 26) {
    return 2;
  } else if (27 <= number && number <= 36) {
    return 3;
  }
}

const columns = {
  1: [1, 4, 7, 10, 13, 16, 19, 22, 25, 28, 31, 34],
  2: [2, 5, 8, 11, 14, 17, 20, 23, 26, 29, 32, 35],
  3: [3, 6, 9, 12, 15, 18, 21, 24, 27, 30, 33, 36],
};
function column(number) {
  if (columns[1].includes(number)) {
    return 1;
  } else if (columns[2].includes(number)) {
    return 2;
  } else if (columns[3].includes(number)) {
    return 3;
  }
}

const color = {
  red: [1, 3, 5, 7, 9, 12, 14, 16, 18, 19, 21, 23, 25, 27, 30, 32, 34, 36],
  black: [2, 4, 6, 8, 10, 11, 13, 15, 17, 20, 22, 24, 26, 28, 29, 31, 33, 35],
  green: [0],
};

const area_half = {
  right: [2, 4, 6, 8, 10, 11, 13, 15, 17, 19, 21, 23, 25, 27, 30, 32, 34, 36],
  left: [1, 3, 5, 7, 9, 12, 14, 16, 18, 20, 22, 24, 26, 28, 29, 31, 33, 35],
};

const area_quater = {
  1: [2, 4, 6, 8, 10, 11, 13, 15, 17, 19, 21, 23, 25, 27, 30, 32, 34, 36],
  2: [1, 3, 5, 7, 9, 12, 14, 16, 18, 20, 22, 24, 26, 28, 29, 31, 33, 35],
};

function badgeColor(number) {
  if (color['red'].includes(number)) {
    return 'bg-danger';
  } else if (color['black'].includes(number)) {
    return 'bg-dark';
  } else if (color['green'].includes(number)) {
    return 'bg-success';
  }
}
</script>

<template>
  TODO: 過去50件、100件、200件の偏りを見たい。 ベットのアラート表示 スタイル調整
  <div class="row">
    <div class="md-col-12">
      <div id="table" class="p-3">
        <table class="table text-center text-middle">
          <tr>
            <td rowspan="3" class="table-success align-middle">
              <a @click="draw(0)">0</a>
            </td>
            <td class="table-danger"><a @click="draw(3)">3</a></td>
            <td class="table-secondary"><a @click="draw(6)">6</a></td>
            <td class="table-danger"><a @click="draw(9)">9</a></td>
            <td class="table-danger"><a @click="draw(12)">12</a></td>
            <td class="table-secondary"><a @click="draw(15)">15</a></td>
            <td class="table-danger"><a @click="draw(18)">18</a></td>
            <td class="table-danger"><a @click="draw(21)">21</a></td>
            <td class="table-secondary"><a @click="draw(24)">24</a></td>
            <td class="table-danger"><a @click="draw(27)">27</a></td>
            <td class="table-danger"><a @click="draw(30)">30</a></td>
            <td class="table-secondary"><a @click="draw(33)">33</a></td>
            <td class="table-danger"><a @click="draw(36)">36</a></td>
          </tr>
          <tr>
            <td class="table-secondary"><a @click="draw(2)">2</a></td>
            <td class="table-danger"><a @click="draw(5)">5</a></td>
            <td class="table-secondary"><a @click="draw(8)">8</a></td>
            <td class="table-secondary"><a @click="draw(11)">11</a></td>
            <td class="table-danger"><a @click="draw(14)">14</a></td>
            <td class="table-secondary"><a @click="draw(17)">17</a></td>
            <td class="table-secondary"><a @click="draw(20)">20</a></td>
            <td class="table-danger"><a @click="draw(23)">23</a></td>
            <td class="table-secondary"><a @click="draw(26)">26</a></td>
            <td class="table-secondary"><a @click="draw(29)">29</a></td>
            <td class="table-danger"><a @click="draw(32)">32</a></td>
            <td class="table-secondary"><a @click="draw(35)">35</a></td>
          </tr>
          <tr>
            <td class="table-danger"><a @click="draw(1)">1</a></td>
            <td class="table-secondary"><a @click="draw(4)">4</a></td>
            <td class="table-danger"><a @click="draw(7)">7</a></td>
            <td class="table-secondary"><a @click="draw(10)">10</a></td>
            <td class="table-secondary"><a @click="draw(13)">13</a></td>
            <td class="table-danger"><a @click="draw(16)">16</a></td>
            <td class="table-danger"><a @click="draw(19)">19</a></td>
            <td class="table-secondary"><a @click="draw(22)">22</a></td>
            <td class="table-danger"><a @click="draw(25)">25</a></td>
            <td class="table-secondary"><a @click="draw(28)">28</a></td>
            <td class="table-secondary"><a @click="draw(31)">31</a></td>
            <td class="table-danger"><a @click="draw(34)">34</a></td>
          </tr>
        </table>
      </div>
    </div>
  </div>

  <h2>History</h2>
  <div class="card">
    <table class="table table-compact">
      <tr>
        <td>Draw</td>
        <td>Dozen</td>
        <td>Column</td>
        <td>Area</td>
        <td>Area(Quater)</td>
        <td>Area(Half)</td>
        <td>Time</td>
        <td>&nbsp;</td>
      </tr>
      <tr v-for="draw in draws.reverse()" :key="draw.id">
        <td>
          <span class="badge" :class="badgeColor(draw.number)">
            {{ draw.number }}
          </span>
        </td>
        <td>
          {{ dozen(draw.number) }}
        </td>
        <td>
          {{ column(draw.number) }}
        </td>
        <td>
          {{ draw.number }}
        </td>
        <td>
          {{ draw.number }}
        </td>
        <td>
          {{ draw.number }}
        </td>
        <td>
          <span class="fs-6">
            {{ draw.created_at }}
          </span>
        </td>
        <td>
          <button @click="removeDraw(draw)" class="btn btn-danger btn-sm">
            Remove
          </button>
        </td>
      </tr>
    </table>
  </div>

  <button @click="clearDraw()" class="btn btn-danger">Clear history</button>
</template>

<style scoped></style>
