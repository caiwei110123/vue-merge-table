<template>
  <div>
    <merge-table v-if="tableData.length > 0" :table-data="tableData" :col-configs="colConfigs" :merge-columns="mergeColumns" />
        <el-button  @click.native="onSubmit">submit</el-button>
  </div>
</template>

<script>
import MergeTable from '@/components/MergeTable'
export default {
  name: 'MergeTableDemo',
  components: { MergeTable },
  data() {
    return {
      tableData: [],
      colConfigs: [
        {
          label: '项目',
          align: 'center',
          prop: 'project',
          width: '40px',
          type: 'label',
        },
        { prop: 'standard', label: '评价标准', align: 'center', type: 'label' },
        { prop: 'results', label: '评价结果' , radioList:[{id:1,val:"优"},{id:2,val:"良"},{id:3,val:"中"},{id:4,val:"差"}], align: 'center', type: 'radio' }
      ],
       mergeColumns: [
        { index: 2, name: 'project' },
      ]
    }
  },
  mounted() {
    // 获取数据
    this.fetchData()
  },
  methods: {
      onSubmit(){
          console.log(this.tableData);
      },
    fetchData() {
      // 使用Axios调用数据 此处为模拟数据
      this.tableData = [
        { project: '教师授课情况', standard: '有教案，备课充足',results:'' },
        { project: '教师授课情况', standard: '教学内容充实，信息量大', results:'' },
        { project: '教师授课情况', standard: '教学富有启发性，能给学生启迪' ,results:''},
        { project: '教师授课情况', standard: '板书工整，设计合理', results:''},
        { project: '教师授课情况', standard: '教师着装得体，教态大方，精神饱满' ,results:''},
        { project: '教师授课情况', standard: '课堂教学和适应能力',results:'' },
        { project: '学生听课听课', standard: '到课情况',results:'' },
        { project: '学生听课听课', standard: '课堂记录',results:'' },
        { project: '学生听课听课', standard: '课堂气氛', results:'' },


      ]
    }
  }
}
</script>