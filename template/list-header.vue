<template lang="html">
    <div class="list-header clearfix">
                <label class="col-xs-5 text-left title" >ToDoList</label>
                <input class="input_box col-xs-7" type="text" name="" :value="addToDo" placeholder="添加ToDo" v-model="addToDo" @keydown="confirm">
            </div>
        </template>

        <script>
            import {Bus} from "../bus.js"
            export default {
                data(){
                    return{
                        addToDo:""
                    }
                },
                methods:{
                    confirm(e){
                        if(e.keyCode===13 && this.addToDo!=""){
                            Bus.$emit("pushTxt",this.addToDo);
//                           初始化
                            this.addToDo="";
                        }


                    }
                }
            }
        </script>

        <style lang="css">
            .list-header{
                height: 50px;
                line-height: 50px;
                background-color: #3c3c3c;
                padding-right: 15px;
                position: relative;
            }
            .title{
                font-size: 24px;
                color:white;
                cursor: pointer;
            }
            .input_box{
                height: 24px;
                border-radius: 5px;
                margin-top: 13px;
                text-indent: 10px;
                box-shadow: 0 1px 0 rgba(255,255,255,0.24), 0 1px 6px rgba(0,0,0,0.45) inset;
                border: none;
                padding-left: 0;
                outline: none;
            }
        </style>
