<template>
  <div>
    <md-table v-model="users" :table-header-color="tableHeaderColor" @md-selected="onSelect">
      <md-table-row slot="md-table-row" slot-scope="{ item }" md-selectable="multiple" md-auto-select >
        <md-table-cell md-label="姓名">{{ item.name }}</md-table-cell>
        <md-table-cell  md-label="性别">{{ item.sex }}</md-table-cell>
        <md-table-cell md-label="学历">{{ item.education }}</md-table-cell>
        <md-table-cell md-label="薪资">{{ item.salary }}</md-table-cell>
        <md-table-cell md-label="户籍">{{ item.city }}</md-table-cell>
        <md-table-cell md-label="电话">{{ item.phone }}</md-table-cell>
        <md-table-cell md-label="邮箱">{{ item.email }}</md-table-cell>
        <md-table-cell md-label="状态">{{ item.status }}</md-table-cell>
        <md-table-cell md-label="简历下载"><md-button data-background-color="blue" >下载</md-button></md-table-cell>
      </md-table-row>
    </md-table>
  </div>
</template>
<script>
export default {
  name: "simple-table",
  props: {
    tableHeaderColor: {
      type: String,
      default: ""
    }
  },
  data() {
    return {
      selected: [],
      users: [
        {
            name:"小健",
            sex:"男",
            education:"本科",
            salary:"8000",
            city:"北京",
            phone:"17293829931",
            email:"xiaojian@xx.com",
            status:"待推荐"
        },
        {
            name:"苏菲",
            sex:"女",
            education:"本科",
            salary:"120000",
            city:"上海",
            phone:"12323455632",
            email:"suf@zx.com",
            status:"待面试"
        },
        {
            name:"peter",
            sex:"男",
            education:"本科",
            salary:"9999",
            city:"上海",
            phone:"18218281283",
            email:"ppap@11.com",
            status:"不合适"
        },
        {
            name:"木鱼",
            sex:"男",
            education:"本科",
            salary:"150000",
            city:"北京",
            phone:"19338382755",
            email:"ark-tv@xx.com",
            status:"入职"
        },
        {
            name:"Arron",
            sex:"男",
            education:"本科",
            salary:"8000",
            city:"安徽",
            phone:"18892931928",
            email:"aa@qc.com",
            status:"没兴趣"
        },
        {
            name:"李非凡",
            sex:"男",
            education:"本科",
            salary:"6400",
            city:"江苏",
            phone:"18292932734",
            email:"ftime@11.com",
            status:"储备"
        }
      ]
    };
  },
    methods: {
        onSelect(items) {
            this.selected = items
        }
    }

};
</script>
