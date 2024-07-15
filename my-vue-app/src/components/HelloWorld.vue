<template>
  <el-table :data="tableData" style="width: 100%" stripe="true" fit="true">
    <!-- 定义表格列，label为列名，width为列宽 -->
    <el-table-column label="Date">
      <!-- 使用作用域插槽，scope为当前行的数据 -->
      <template #default="scope">
        <!-- 使用flex布局，图标和日期并排显示 -->
        <div style="display: flex; align-items: center">
          <!-- 使用element-plus的图标组件 -->
          <el-icon><timer /></el-icon>
          <!-- 显示日期 -->
          <span style="margin-left: 10px">{{ scope.row.date }}</span>
        </div>
      </template>
    </el-table-column>
    <el-table-column label="Name">
      <template #default="scope">
        <!-- 使用element-plus的数字输入框组件 -->
        <el-input-number
          v-model="scope.row.num"
          :min="1"
          :max="10"
          @change="handleChange"
        />
      </template>
    </el-table-column>
    <el-table-column label="Operations">
      <template #default="scope">
        <!-- 编辑按钮 -->
        <el-button size="small" @click="handleEdit(scope.$index, scope.row)"
          >Edit</el-button
        >
        <!-- 删除按钮 -->
        <el-button
          size="small"
          type="danger"
          @click="handleDelete(scope.$index, scope.row)"
          >Delete</el-button
        >
      </template>
    </el-table-column>
  </el-table>
</template>

<script lang="ts" setup>
// 引入element-plus的图标组件
import { Timer } from "@element-plus/icons-vue";
// 引入vue的ref函数
import { ref } from "vue";

// 定义用户接口
interface User {
  date: string;
  name: string;
  address: string;
  num: number;
}

// 定义编辑按钮的点击事件
const handleEdit = (index: number, row: User) => {
  console.log(index, row);
};
// 定义删除按钮的点击事件
const handleDelete = (index: number, row: User) => {
  console.log(index, row);
};

// 定义表格数据
let tableData: User[] = [
  {
    date: "2016-05-03",
    name: "Tom",
    num: 1,
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-03",
    name: "Tom",
    num: 1,
    address: "No. 189, Grove St, Los Angeles",
  },
];
// const num = ref();
// 定义数字输入框的change事件
const handleChange = (value: number) => {
  console.log(tableData);
};
</script>
