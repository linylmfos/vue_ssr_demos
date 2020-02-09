<template>
  <div>
    nowplaying
    <ul>
      <li v-for="data in datalist" :key="data.filmId" @click="handleClick(data.filmId)">
        <img :src="data.poster"/>
        <p>{{data.name}}</p>
      </li>
    </ul>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      datalist: ["111", "222", "333"]
    };
  },
  asyncData(data) {
    console.log(data);
    return axios({
      url:
        "https://m.maizuo.com/gateway?cityId=110100&pageNum=1&pageSize=10&type=1&k=6341699",
      headers: {
        "X-Client-Info":
          '{"a":"3000","ch":"1002","v":"5.0.4","e":"15610855429195524981146"}',
        "X-Host": "mall.film-ticket.film.list"
      }
    }).then(res => {
      console.log(res.data);
      return {
        datalist: res.data.data.films
      }; // 状态
    });
  },
  methods: {
    handleClick(id) {
      // this.$router.push(`/cinema`)
      this.$router.push(`/detail/${id}`);
    }
  }
};
</script>