<template>
  <div class="content">
    <md-dialog :md-active.sync="showDialog">
      <div
              class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-100"
      >
        <md-card class="md-card-plain">
          <md-card-header data-background-color="blue">
            <h4 class="title">推荐项目</h4>
            <p class="category">请勾选需要推荐的项目</p>
          </md-card-header>
          <md-card-content>
            <md-table v-model="addprojects" :table-header-color="tableHeaderColor" @md-selected="onSelect">
              <md-table-row slot="md-table-row" slot-scope="{ item }" md-selectable="multiple" md-auto-select>
                <md-table-cell md-label="项目编号">{{ item.pnum }}</md-table-cell>
                <md-table-cell md-label="项目名称">{{ item.pname }}</md-table-cell>
                <md-table-cell md-label="项目负责人">{{ item.preser }}</md-table-cell>
              </md-table-row>
            </md-table>
          </md-card-content>
        </md-card>
      </div>

      <md-dialog-actions>
        <md-button  class="md-info"  @click="showDialog = false">关闭</md-button>
        <md-button  class="md-success"  @click="showDialog = false">推荐</md-button>
      </md-dialog-actions>
    </md-dialog>
    <div class="md-layout">
      <div
              class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-100"
      >
        <md-card>
          <md-card-header data-background-color="blue">
            <h4 class="title" style="display: inline-block" >简历列表</h4>
            <md-button  data-background-color="blue" style="position: relative;left: 500px;font-size: medium;font-weight: bold" href="/#/user">新增简历</md-button>
            <p class="category">可以选择简历推荐项目，选择单个简历可在下面的表查看其关联的项目信息</p>
          </md-card-header>
          <md-card-content>
            <md-table table-header-color="blue" @md-selected="onSelect1" v-model="users" >  <!--@md-selected="onSelect1"   v-model="users" -->
              <md-table-toolbar>
                <div class="md-autocomplete">
                  <md-card>
                    <md-card-content>
                      <div class="md-layout md-gutter md-small-size-100 md-size-50">
                        <div class="md-layout-item md-size-40">
                          <md-autocomplete
                                  class="search"
                                  v-model="selectedUser"
                                  :md-options="searchUsers"
                          >
                            <label>Search...</label>
                          </md-autocomplete>
                        </div>
                        <div class="md-layout-item md-size-40">
                          <md-field>
                            <md-select>
                              <md-option v-for="tfield in tablefield" :value="tfield.value" class="md-layout-item" >{{ tfield.field }}</md-option>
                            </md-select>
                          </md-field>
                        </div>
                        <div class="md-layout-item md-size-10">
                          <md-button data-background-color="blue" >查询</md-button>
                        </div>
                      </div>
                    </md-card-content>
                  </md-card>
                </div>
                <md-button  data-background-color="blue" style="float:left;position: relative;left: 110px;font-size: medium;font-weight: bold" @click="showDialog = true"  >推荐项目</md-button>
              </md-table-toolbar>

              <md-table-row slot="md-table-row" slot-scope="{ item }" md-selectable="multiple" md-auto-select >
                <md-table-cell  md-label="姓名" >{{ item.name }}</md-table-cell>
                <md-table-cell  md-label="基本信息">
                  <table>
                    <tr  v-for="i in item.basicMessage" >
                      <td>{{i.sex}}</td>
                      <td >{{i.education}}</td>
                      <td>{{i.birth}}</td>
                      <td>{{i.salary}}</td>
                      <td>{{i.phone}}</td>
                      <td>{{i.city}}</td>
                    </tr>
                  </table>
                </md-table-cell>
                <md-table-cell  md-label="项目">
                  <table>
                    <tr  v-for="i in item.basicMessage" >
                      <td>{{i.project}}</td>
                    </tr>
                  </table>
                </md-table-cell>
                <md-table-cell md-label="状态">
                  <table>
                    <tr  v-for="i in item.basicMessage" >
                      <td>{{i.status}}</td>
                    </tr>
                  </table>
                </md-table-cell>
                <md-table-cell md-label="时间">
                  <table>
                    <tr  v-for="i in item.basicMessage" >
                      <td>{{i.date}}</td>
                    </tr>
                  </table>
                </md-table-cell>
                <md-table-cell md-label="简历下载"><md-button data-background-color="blue" >下载</md-button></md-table-cell>
              </md-table-row>
            </md-table>
          </md-card-content>
        </md-card>
      </div>
    </div>
  </div>
</template>

<script>
    import { SimpleTable, OrderedTable } from "@/components";
    import MdTableRowGhost from "vue-material/src/components/MdTable/MdTableRowGhost";

    export default {
        components: {
            MdTableRowGhost,
            OrderedTable,
            SimpleTable
        },
        props: {
            tableHeaderColor: {
                type: String,
                default: ""
            }
        },
        data() {
            return {
                showDialog : false,
                selectedUser:null,
                searchUsers:[
                    "小健",
                    "苏菲",
                    "peter",
                    "木鱼",
                    "Arron",
                    "李非凡"
                ],
                selected: [],
                selected1:[],
                tablefield:[
                    {
                        field:"姓名",
                        value:"name"
                    },
                    {
                        field:"基本信息",
                        value:"basic"
                    },
                    {
                        field:"项目",
                        value:"project"
                    },
                    {
                        field:"状态",
                        value:"state"
                    },
                    {
                        field:"时间",
                        value:"time"
                    },
                ],
                addprojects: [
                    {
                        pnum:"T-ss-001",
                        pname:"xx1银行项目组",
                        preser:"张三"

                    },
                    {
                        pnum:"T-ss-002",
                        pname:"xx2项目组",
                        preser:"李四"
                    },
                    {
                        pnum:"T-ss-003",
                        pname:"xx3银行项目组",
                        preser:"王五"
                    },
                    {
                        pnum:"T-ss-004",
                        pname:"xx4银行项目组",
                        preser:"卢六"
                    }
                ],
                users: [
                    {
                        name:"小健",
                        basicMessage:[
                            {sex:"男",education:"本科",birth:"1994-2-2",salary:"8000",city:"北京",phone:"17293829931", email:"xiaojian@xx.com",project:"", status:"待推荐",date:"2019-3-1"}
                        ]
                    },
                    {
                        name:"苏菲",
                        basicMessage:[
                            {sex:"女",education:"本科",birth:"1991-4-2",salary:"120000",city:"上海",phone:"12323455632", email:"suf@zx.com",project:"xx2银行项目组",status:"待面试",date:"2019-5-13"}
                        ]
                    },
                    {
                        name:"peter",
                        basicMessage:[
                            {sex:"男",education:"本科",birth:"1991-4-2",salary:"9999",city:"上海",phone:"18218281283", email:"ppap@11.com",project:"xx3银行项目组",status:"不合适",date:"2019-4-15"},
                            {sex:"男",education:"本科",birth:"1991-4-2",salary:"9999",city:"上海",phone:"18218281283", email:"ppap@11.com",project:"xx1银行项目组",status:"不合适",date:"2019-4-16"},
                            {sex:"男",education:"本科",birth:"1991-4-2",salary:"9999",city:"上海",phone:"18218281283", email:"ppap@11.com",project:"xx2银行项目组",status:"不合适",date:"2019-4-17"}
                        ]
                    },
                    {
                        name:"木鱼",
                        basicMessage:[
                            {sex:"男",education:"本科",birth:"1985-3-2",salary:"150000",city:"北京",phone:"19338382755", email:"ark-tv@xx.com",project:"xx1银行项目组",status:"入职",date:"2019-3-27"}
                        ]
                    },
                    {
                        name:"Arron",
                        basicMessage:[
                            {sex:"男",education:"本科",birth:"1990-12-2",salary:"8000",city:"北京",phone:"安徽", email:"aa@qc.com",project:"", status:"没兴趣",date:"2019-3-2"}
                        ]
                    },
                    {
                        name:"李非凡",
                        basicMessage:[
                            {sex:"男",education:"本科",birth:"1995-12-2",salary:"6400",city:"江苏",phone:"18292932734", email:"ftime@11.com",project:"xx4银行项目组", status:"储备",date:"2019-3-22"}
                        ]
                    }
                ]
            };
        },
        methods: {
            onSelect (items) {
                console.log("onSelect")
                this.selected = items
            },
            onSelect1 (items) {
                console.log("onSelect1")
                this.selected1 = items
                console.log(items.length)
            }
        }

    };
</script>
