
<template>
<div id="mylist">
<tableheader>

</tableheader>
<el-table  v-loading.lock="fullscreenLoading" target="#mylist" :data="tableData" :show-header="true" border
    style="width: 100%;height:800px;">
    <el-table-column 
fixed
      prop="name"
      label="项目名称"
       align="center">
    </el-table-column>
    <el-table-column
      prop="attrbute"
      label="项目属性"
     align="center">
    </el-table-column>
    <el-table-column
      prop="type"
      label="项目类型"
       align="center">
    </el-table-column>
    <el-table-column
      prop="field"
      label="行业领域"
     align="center">
    </el-table-column>
    <el-table-column
      prop="time"
      label="立项时间"
      align="center">
    </el-table-column>
    <el-table-column
      prop="bz1"
      label="立项时间"
      align="center">
    </el-table-column>
    <el-table-column
      prop="bz2"
      label="bz2"
      align="center">
    </el-table-column>





    <el-table-column
      label="项目图片"
      align="center">
      <template slot-scope="scope">
<el-button type="text" size="small">查看</el-button>
</template>
    </el-table-column>

  </el-table>

  <el-row id="fenye">
  <el-col>
<el-pagination
  background
  layout="prev, pager, next"
  :total="listData.length" @current-change="handleCurrentChange">
</el-pagination>
  </el-col>
  </el-row>

</div>
  
</template>
<script>
  import tableheader from "./table_header.vue";
   export default {
    
    methods: {
      handleClick(row) {
        console.log(row);
      },
      openFullScreen() {
        this.fullscreenLoading = true;
        setTimeout(() => {
          this.fullscreenLoading = false;
        }, 2000);
      },
       handleCurrentChange(val) {
        this.start=(`${val}`-1)*13;
        this.end=(`${val}`+1)*13;
         this.tableData=this.listData.slice(this.start,this.end); 
      
      }
    
    },

    created () {
        this.openFullScreen();
        this.tableData=this.listData.slice(this.start,this.end);
        this.$store.commit('changPagename',this.pagename);
        this.$store.commit('changTitle',this.titlenames) 
    },
   
        props:['pagename','titlenames','listData'],
 
    data() {
        
      return {
          tableData: [],
          
          start:0,
          end:13,
          fullscreenLoading: false,
          value8: '2017-07-01',
        value9: '2017-07-31',
       
      }
    },
    components: {
      tableheader,
    }
  }

</script>
<style scoped>

    #fenye{
        width:100%;
        background:#fff;
        text-align:center;
        line-height: 34px;
        padding-top:40px;
    }
</style>
