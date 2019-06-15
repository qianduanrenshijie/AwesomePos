<template>
    <div>
        <el-row>
            <el-col :span="7" id="order-list">
                <el-tabs>
                    <el-tab-pane label="点餐">
                        <el-table :data="tableData" border>
                            <el-table-column prop="goodsName" label="商品名称">
                            </el-table-column>
                            <el-table-column prop="count" label="数量">
                            </el-table-column>
                            <el-table-column prop="price" label="金额">
                            </el-table-column>
                            <el-table-column label="操作" width="100" fixed="right">
                                <template slot-scope="scope">
                                    <el-button type="text" size="small" @click="deleteBtn(scope.row.goodsId)">删除
                                    </el-button>
                                    <el-button type="text" size="small" @click="addBtn(scope.row.goodsId)">增加
                                    </el-button>
                                </template>
                            </el-table-column>
                        </el-table>
                        <div class="sum">
                            <ul>
                                <li>
                                    <span>数量：</span>
                                    <span>{{productSum}}</span>
                                </li>
                                <li>
                                    <span>总额：</span>
                                    <span>{{priceSum}}</span>
                                </li>
                            </ul>
                        </div>
                        <div class="btn">
                            <el-button type="warning">挂单</el-button>
                            <el-button @click="delAll" type="danger">删除</el-button>
                            <el-button type="primary">结账</el-button>
                        </div>
                    </el-tab-pane>
                    <el-tab-pane label="挂单">挂单</el-tab-pane>
                    <el-tab-pane label="外卖">外卖</el-tab-pane>
                </el-tabs>
            </el-col>
            <el-col :span="17">
                <div class="often-goods">
                    <div class="title">常用商品</div>
                    <div class="often-goods-list">
                        <ul>
                            <li v-for="(item,index) in oftenGoods" :key="index" @click="oftenGoodsClick(item)">
                                <span>{{item.goodsName}}</span>
                                <span class="o-price">{{item.price}}</span>
                            </li>
                        </ul>
                    </div>
                </div>
                <div class="goods-type">
                    <el-tabs>
                        <el-tab-pane label="汉堡">
                            <ul class='cookList'>
                                <li v-for="(goods,index) in type0Goods" :key="index" @click="oftenGoodsClick(goods)">
                                    <span class="foodImg"><img :src="goods.goodsImg" width="100%"></span>
                                    <span class="foodName">{{goods.goodsName}}</span>
                                    <span class="foodPrice">￥{{goods.price}}元</span>
                                </li>
                            </ul>
                        </el-tab-pane>
                        <el-tab-pane label="小食">
                            小食
                        </el-tab-pane>
                        <el-tab-pane label="饮料">
                            饮料
                        </el-tab-pane>
                        <el-tab-pane label="套餐">
                            套餐
                        </el-tab-pane>
                    </el-tabs>
                </div>
            </el-col>
        </el-row>
    </div>
</template>\
<script>
    export default {
        data() {
            return {
                tableData: [],
                oftenGoods: [{
                    goodsId: 1,
                    goodsName: '香辣鸡腿堡',
                    price: 18
                }, {
                    goodsId: 2,
                    goodsName: '田园鸡腿堡',
                    price: 15
                }, {
                    goodsId: 3,
                    goodsName: '和风汉堡',
                    price: 15
                }, {
                    goodsId: 4,
                    goodsName: '快乐全家桶',
                    price: 80
                }, {
                    goodsId: 5,
                    goodsName: '脆皮炸鸡腿',
                    price: 10
                }, {
                    goodsId: 6,
                    goodsName: '魔法鸡块',
                    price: 20
                }, {
                    goodsId: 7,
                    goodsName: '可乐大杯',
                    price: 10
                }, {
                    goodsId: 8,
                    goodsName: '雪顶咖啡',
                    price: 18
                }, {
                    goodsId: 9,
                    goodsName: '大块鸡米花',
                    price: 15
                }, {
                    goodsId: 20,
                    goodsName: '香脆鸡柳',
                    price: 17
                }],
                type0Goods: [{
                    goodsId: 1,
                    goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos001.jpg",
                    goodsName: '香辣鸡腿堡',
                    price: 18
                }, {
                    goodsId: 2,
                    goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos002.jpg",
                    goodsName: '田园鸡腿堡',
                    price: 15
                }, {
                    goodsId: 3,
                    goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos004.jpg",
                    goodsName: '和风汉堡',
                    price: 15
                }, {
                    goodsId: 4,
                    goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos003.jpg",
                    goodsName: '快乐全家桶',
                    price: 80
                }, {
                    goodsId: 5,
                    goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos003.jpg",
                    goodsName: '脆皮炸鸡腿',
                    price: 10
                }, {
                    goodsId: 6,
                    goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos004.jpg",
                    goodsName: '魔法鸡块',
                    price: 20
                }, {
                    goodsId: 7,
                    goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos001.jpg",
                    goodsName: '可乐大杯',
                    price: 10
                }, {
                    goodsId: 8,
                    goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos003.jpg",
                    goodsName: '雪顶咖啡',
                    price: 18
                }, {
                    goodsId: 9,
                    goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos002.jpg",
                    goodsName: '大块鸡米花',
                    price: 15
                }, {
                    goodsId: 20,
                    goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos002.jpg",
                    goodsName: '香脆鸡柳',
                    price: 17
                }],
                productSum: 0,
                priceSum: 0
            }
        },
        mounted() {
            let bodyHeight = document.body.clientHeight
            document.getElementById('order-list').style.height = bodyHeight + 'px'
        },
        methods: {
            deleteBtn(id) {
                this.tableData = this.tableData.filter(o => o.goodsId != id);
                this.getSum()
            },
            addBtn(id) {
                let arr = this.tableData.filter(o => o.goodsId == id);
                arr[0].count++;

                this.getSum()
            },
            delAll(){
                this.tableData = []
                this.getSum()
            },
            //常用商品店家
            oftenGoodsClick(goods) {
                let isHave = false;

                this.tableData.forEach((item, i) => {
                    if (item.goodsId == goods.goodsId) {
                        isHave = true
                    }
                })
                if (isHave) {
                    let arr = this.tableData.filter(o => o.goodsId == goods.goodsId);
                    arr[0].count++;
                    // this.tableData[index].count ++
                    // this.tableData[index].price = this.tableData[index].price * this.tableData[index].count
                    // this.tableData.splice(index,1,this.tableData[index]) //此处注意改变数组对象中的参数值，vue不渲染。此处用数组替换解决(此处还有给坑，用goods的对象不行。用新的就行)
                } else {
                    let newGoods = {
                        goodsId: goods.goodsId,
                        goodsName: goods.goodsName,
                        price: goods.price,
                        count: 1
                    }; //此处不要用goods对象，那样会影响oftenGoods中参数且回影响渲染
                    this.tableData.push(newGoods)
                }


                this.getSum()
            },

            getSum() {
                this.productSum = 0;
                this.priceSum = 0;
                this.tableData.forEach(item => {
                    this.productSum += item.count
                    this.priceSum += item.count * item.price
                })
            }
        }
    }
</script>
<style lang="scss">
    #order-list {
        background-color: white
    }

    .title {
        height: 20px;
        border-bottom: 1px solid #D3DCE6;
        background-color: #F9FAFC;
        padding: 10px;
    }

    .often-goods-list ul {
        display: flex;
        flex-wrap: wrap;
    }

    .often-goods-list ul li {
        width: 20%;
        list-style: none;
        // float: left;
        border: 10px solid #E5E9F2;
        padding: 10px;
        // margin: 5px;
        background-color: #fff;
        box-sizing: border-box;
        cursor: pointer;
    }

    .goods-type {
        clear: both;
    }

    .o-price {
        color: #58B7FF;
    }

    .cookList li {
        list-style: none;
        width: 23%;
        border: 1px solid #E5E9F2;
        height: auot;
        overflow: hidden;
        background-color: #fff;
        padding: 2px;
        float: left;
        margin: 2px;
        cursor: pointer;
    }

    .cookList li span {
        display: block;
        float: left;
    }

    .foodImg {
        width: 40%;
    }

    .foodName {
        font-size: 18px;
        padding-left: 10px;
        color: brown;
    }

    .foodPrice {
        font-size: 16px;
        padding-left: 10px;
        padding-top: 10px;
    }

    .sum {
        height: 50px;
        line-height: 50px;
        border-bottom: 1px solid #EBEEF5;
        text-align: center;

        li {
            display: inline-block;
            margin-right: 5px;
            // float: left;
        }
    }

    .btn {
        text-align: center;
        padding: 10px;
    }
</style>