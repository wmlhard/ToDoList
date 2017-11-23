<template lang="html">
    <div class="list-section container-fluid">
                <h3>正在进行 <span class="mark text-center">{{getDoNum}}</span></h3>
                <ul class="container no-padding">
                    <li v-for="(item,index) in doArr">
                        <span class="change text-center" @click="change(index)"></span>
                        <input class="txt" type="text" :value="doArr[index]" v-model="doArr[index]">

                        <span class="del text-center" @click="del(index)">-</span>
                    </li>

                </ul>
                <h3>已经完成 <span class="mark text-center">{{getDoneNum}}</span></h3>
                <ul class="container no-padding">
                    <li class="done-li" v-for="(item,index) in DoneArr">
                        <span class="change text-center" @click="change1(index)">✔</span>
                        <input type="text" :value="DoneArr[index]" v-model="DoneArr[index]">

                        <span class="del text-center" @click="del1(index)">-</span>
                    </li>

                </ul>
            </div>
        </template>

        <script>
            import {Bus} from "../bus.js"
            export default {
                data(){
                    return{
                        doArr:[],
                        DoneArr:[],

                    }
                },
                computed:{
                    getDoNum(){
                        return this.doArr.length;
                    },
                    getDoneNum(){
                        return this.DoneArr.length;
                    }
                },
                methods:{

                    del(index){
                        this.doArr.splice(index,1);
                    },
                    del1(index){
                        this.DoneArr.splice(index,1);
                    },
                    change(index){
                        this.DoneArr.push(this.doArr[index]);
                        this.doArr.splice(index,1)
                    },
                    change1(index){
                        this.doArr.push(this.DoneArr[index]);
                        this.DoneArr.splice(index,1)
                    }
                },
                created:function(){
                    const _this = this;
                    Bus.$on("pushTxt",function(val){
                        _this.doArr.push(val);
                    })
                }
            }
        </script>

        <style lang="css">
            h3{
                font-weight: bold;
            }
            .mark{
                display: inline-block;
                font-size: 14px;
                color:#666;
                border-radius: 50%;
                width: 20px;
                height: 20px;
                line-height: 15px;
                float: right;
                background-color: #c7ddef;
            }
            ul{
                padding: 0;
            }
            ul li{
                list-style: none;
                padding: 0;
                background:white;
                border-radius: 3px;
                height: 33px;
                margin-top: 1px;
                border-left: 7px solid teal;
            }
            input{
                border: none;
                width: 75%;
            }
            .no-padding{
                padding: 0;
            }
            .list-section{
                width: 100vw;
                overflow: hidden;
            }

            .change{
                display: inline-block;
                width: 20px;
                height:20px;
                background: #cdcdcd;
                margin: 7px 0 0 5px;
            }
            .del{
                width: 18px;
                height:18px;
                background: #9d9d9d;
                box-shadow: 0 0 0 3px #e3e3e3;
                border: 3px solid #fff;
                display: inline;
                border-radius: 50%;
                font-weight: bold;
                float: right;
                color: #fff;
                line-height: 11px;
                margin: 7px 5px 0 0;

            }
            .txt{
                position: relative;
                bottom: 5px;

            }
            .done-li{
                opacity: 0.5;
                border-left: 7px solid #8c8c8c;

            }

        </style>


        </style>