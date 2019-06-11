<template>
  <div>
    <md-table v-model="users" :table-header-color="tableHeaderColor">
      <md-table-row slot="md-table-row" slot-scope="{ item }">
        <md-table-cell md-label="项目编号">{{ item.pnum }}</md-table-cell>
        <md-table-cell md-label="项目名称">{{ item.pname }}</md-table-cell>
        <md-table-cell md-label="项目负责人">{{ item.preser }}</md-table-cell>
      </md-table-row>
    </md-table>
  </div>
</template>

<script>
export default {
  name: "ordered-table",
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
      ]
    };
  }
};
</script>
