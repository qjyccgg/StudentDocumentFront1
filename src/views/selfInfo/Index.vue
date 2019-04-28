<template>
    <div style="display: flex;flex-direction: column;align-items: center;width: 100%;">
        <div style="margin: 40px 0"><h1>个人信息</h1></div>
        <el-card style="width: 80%">
            <div style="width: 100%;display: flex;align-items: center;flex-direction: column">
                <el-form :model="userData" ref="userData" label-width="32%" style="width: 90%;margin-top: 40px" label-position="left">

                    <el-row>
                        <el-col :span="18">
                            <el-row>
                                <el-col :span="8">
                                    <el-form-item label="学号" prop="stuNo">
                                        <el-input :disabled="disable" v-model="userData.stuNo" autocomplete="off"></el-input>
                                    </el-form-item>
                                </el-col>
                                <el-col :span="8">
                                    <el-form-item label="姓名" prop="name">
                                        <el-input v-model="userData.name" :disabled="disable" autocomplete="off"></el-input>
                                    </el-form-item>
                                </el-col>
                                <el-col :span="8">
                                    <el-form-item label="性别" prop="sex">
                                        <el-radio :disabled="disable" label="男" v-model="userData.sex"></el-radio>
                                        <el-radio :disabled="disable" label="女" v-model="userData.sex"></el-radio>
                                    </el-form-item>
                                </el-col>
                            </el-row>
                            <el-row>
                                <el-col :span="8">
                                    <el-form-item label="学院" prop="college">
                                        <el-input :disabled="disable" v-model="userData.college" autocomplete="off"></el-input>
                                    </el-form-item>
                                </el-col>
                                <el-col :span="8">
                                    <el-form-item label="专业" prop="major">
                                        <el-input :disabled="disable" v-model="userData.major" autocomplete="off"></el-input>
                                    </el-form-item>
                                </el-col>
                                <el-col :span="8">
                                    <el-form-item label="班级" prop="grade">
                                        <el-input :disabled="disable" v-model="userData.grade" autocomplete="off"></el-input>
                                    </el-form-item>
                                </el-col>
                            </el-row>
                            <el-row>
                                <el-col :span="8">
                                    <el-form-item label="出生" prop="birth">
                                        <el-date-picker v-model="userData.birth" :disabled="disable"></el-date-picker>
                                    </el-form-item>
                                </el-col>
                                <el-col :span="8">
                                    <el-form-item label="实际年龄" prop="realAge">
                                        <el-input type="number" v-model="userData.realAge" :disabled="disable"></el-input>
                                    </el-form-item>
                                </el-col>
                                <el-col :span="8">
                                    <el-form-item label="文化程度" prop="cultureLevel">
                                        <el-input v-model="userData.cultureLevel" :disabled="disable"></el-input>
                                    </el-form-item>
                                </el-col>
                            </el-row>
                            <el-row>
                                <el-col :span="8">
                                    <el-form-item label="名族" prop="nation">
                                        <el-input v-model="userData.nation" :disabled="disable"></el-input>
                                    </el-form-item>
                                </el-col>
                                <el-col :span="8">
                                    <el-form-item label="职业" prop="occupation">
                                        <el-input v-model="userData.occupation" :disabled="disable"></el-input>
                                    </el-form-item>
                                </el-col>
                                <el-col :span="8">
                                    <el-form-item label="籍贯" prop="nativePlace">
                                        <el-input v-model="userData.nativePlace" :disabled="disable"></el-input>
                                    </el-form-item>
                                </el-col>
                            </el-row>
                        </el-col>
                        <el-col :span="6">
                            <el-form-item label-width="5%">
                                <image-input v-model="userData.photo"></image-input>
                            </el-form-item>
                        </el-col>
                    </el-row>
                    <el-form-item label="现家庭住址" label-width="10%" >
                        <el-input type="textarea" :disabled="disable" v-model="userData.presentAddress"></el-input>
                    </el-form-item>
                    <el-form-item label="毕业学校或工作单位" label-width="10%" >
                        <el-input type="textarea" :disabled="disable" :rows="4" v-model="userData.workPlace"></el-input>
                    </el-form-item>
                    <template>
                        <el-form-item align="right">
                            <el-button :disabled="disable" type="primary" @click="saveData">保存</el-button>
                        </el-form-item>
                    </template>
                </el-form>
            </div>
        </el-card>
    </div>
</template>

<script>
    import Message from '../../components/messages/index'
    import ImageInput from '../../components/upload/UploadBase64.vue'
    export default {
        name: "index",
        components: {ImageInput},
        data(){
            return{
                userData:{},
                disable:false
            }
        },
        methods:{
            initData(){
                let user = JSON.parse(localStorage.getItem("user"));
                this.$http.get("/user/get/"+user.id).then(res=>{
                    if (res.status===200){
                        this.userData = res.data
                    }
                })
            },
            saveData(){
                this.$http.post("/user/update",this.userData).then(res=>{
                    if (res.status===200){
                        Message.success("操作成功");
                        this.initData();
                    }
                })
            }
        },
        mounted(){
            this.initData();
        }
    }
</script>

<style scoped>
</style>