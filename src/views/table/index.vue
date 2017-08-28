<template>
  <div class="app-container">
    <el-table :data="list" v-loading.body="listLoading" element-loading-text="拼命加载中" border fit highlight-current-row>
      <el-table-column align="center" label='ID' width="95">
        <template scope="scope">
          {{scope.$index}}
        </template>
      </el-table-column>

      <el-table-column label="user_id" width="120" align="center">
        <template scope="scope">
          {{scope.row.user_id}}
        </template>
      </el-table-column>
      <el-table-column label="性别" width="80">
        <template scope="scope">
          {{scope.row.sex}}
        </template>
      </el-table-column>
      <el-table-column label="关注人数" width="80" align="center">
        <template scope="scope">
          <span>{{scope.row.focus_count}}</span>
        </template>
      </el-table-column>
      <el-table-column label="昵称" width="80" align="center">
        <template scope="scope">
          {{scope.row.nick_name}}
        </template>
      </el-table-column>
      <el-table-column label="实名认证" width="80" align="center">
        <template scope="scope">
          {{scope.row.real_name_auth}}
        </template>
      </el-table-column>
      <el-table-column label="红牛认证" width="80" align="center">
        <template scope="scope">
          {{scope.row.red_bull_auth}}
        </template>
      </el-table-column>
      <el-table-column label="金牛认证" width="80" align="center">
        <template scope="scope">
          {{scope.row.gold_bull_auth}}
        </template>
      </el-table-column>

      <el-table-column label="头像" width="220" align="center">
        <template scope="scope">
          {{scope.row.head_image}}
        </template>
      </el-table-column>
      <!--<el-table-column align="center" prop="created_at" label="Display_time" width="200">-->
        <!--<template scope="scope">-->
          <!--<i class="el-icon-time"></i>-->
          <!--<span>{{scope.row.display_time}}</span>-->
        <!--</template>-->
      <!--</el-table-column>-->
    </el-table>
    <br>
    <el-pagination
      layout="total, prev, pager, next, jumper"
      @current-change="handleCurrentChange"
      :page-size=10
      :total=totals>
    </el-pagination>
  </div>
</template>

<script>
  import { getUserList } from '@/api/table';

  export default {
    data() {
      return {
        list: null,
        listLoading: true,
        totals: 0,
      }
    },
    created() {
      this.fetchData({
        page:1
      });
    },
    methods: {
      handleCurrentChange (val) {
        this.fetchData({
          page: val
        })
      },
      fetchData(params) {
        this.listLoading = true;
        getUserList(params).then(response => {
          this.list = response.detail.list;
          this.totals = response.detail.totals;
          this.listLoading = false;
        })
      }
    }
  };
</script>
