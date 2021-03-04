<template>
  <div class="container">
    <global-header :user="currentUser"></global-header>
    <ValidateForm @form-submit="onFormSubmit">
      <div class="mb-3">
        <label class="form-label">邮箱地址</label>
        <validate-input
          :rules="emailRules"
          v-model="emailVal"
          placeholder="请输入邮箱地址"
          type="text"
          ref="inputRef"
        ></validate-input>
      </div>
      <div class="mb-3">
        <label class="form-label">密码</label>
        <validate-input
          :rules="passwordRules"
          v-model="passwordVal"
          placeholder="请输入密码"
          type="password"
        ></validate-input>
      </div>
      <template #submit>
        <span class="btn btn-danger">Submit</span>
      </template>
    </ValidateForm>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref } from "vue";
import "bootstrap/dist/css/bootstrap.min.css";
import ColumnList, { ColumnProps } from "./components/ColumnList.vue";
import ValidateInput, { RulesProp } from "./components/ValidateInput.vue";
import ValidateForm from './components/ValidateForm.vue'
import GlobalHeader, { UserProps } from "./components/GlobalHeader.vue";
const currentUser: UserProps = {
  isLogin: true,
  name: "lastcode",
};
const testData: ColumnProps[] = [
  {
    id: 1,
    title: "lastcode的专栏",
    description:
      "这是test1专栏,有一段非常有趣的言论这是test1专栏,有一段非常有趣的言论这是test1专栏,有一段非常有趣的言论",
    avatar: "https://i03piccdn.sogoucdn.com/b0e20da1fef526f0",
  },
  {
    id: 2,
    title: "lastcode2的专栏",
    description:
      "这是test2专栏,有一段非常有趣的言论这是test2专栏,有一段非常有趣的言论这是test2专栏,有一段非常有趣的言论",
    avatar: "https://i03piccdn.sogoucdn.com/b0e20da1fef526f0",
  },
  {
    id: 3,
    title: "lastcode3的专栏",
    description:
      "这是test2专栏,有一段非常有趣的言论这是test2专栏,有一段非常有趣的言论这是test2专栏,有一段非常有趣的言论",
  },
  {
    id: 4,
    title: "lastcode4的专栏",
    description:
      "这是test4专栏,有一段非常有趣的言论这是test2专栏,有一段非常有趣的言论这是test2专栏,有一段非常有趣的言论",
    avatar: "https://i03piccdn.sogoucdn.com/b0e20da1fef526f0",
  },
];
const emailReg = /^\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*$/;
export default defineComponent({
  name: "App",
  setup() {
    const inputRef = ref<any>()
    const emailVal = ref('');
    const emailRules: RulesProp = [
      { type: "required", message: "电子邮箱不能为空" },
      { type: "email", message: "请输入正确的电子邮箱" },
    ];
    const passwordVal=ref('')
    const passwordRules:RulesProp =[
      { type:'required',message:'密码不能为空' }
    ]
    const onFormSubmit= (result:boolean) =>{
      console.log(inputRef.value.validateInput());
      
    }
    return {
      list: testData,
      currentUser,
      emailRules,
      emailVal,
      passwordVal,
      passwordRules,
      onFormSubmit,
      inputRef
    };
  },
  components: {
    ColumnList,
    GlobalHeader,
    ValidateInput,
    ValidateForm
  },
});
</script>

<style>
</style>
