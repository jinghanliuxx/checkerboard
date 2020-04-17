<template>
    <div class="page">
        <div class="table">
            <div class="col" v-for="(col,index) in data" :key="index">
                <div @click="addPiece(cell.type, index, index2)" class="cell" v-for="(cell, index2) in col" :key="index2">{{cell.type == 'o'? 'O' : (cell.type == 'x' ? 'X' : '')}} <span style="opacity: 0;">1</span> </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            data: [
                [{type: ''}, {type: ''}, {type: ''}],
                [{type: ''}, {type: ''}, {type: ''}],
                [{type: ''}, {type: ''}, {type: ''}]
            ],
            flag: false,  // false奇数画圆，true偶数画叉
        }
    },
    methods: {
        addPiece(type, colIndex, cellIndex) {
            if (!this.flag) {   // 画圆s
                this.data[colIndex][cellIndex].type = 'o'
            } else {
                this.data[colIndex][cellIndex].type = 'x'
            }
            this.flag = !this.flag;
            // 行
            if ((this.data[colIndex][0].type == this.data[colIndex][1].type) && (this.data[colIndex][1].type == this.data[colIndex][2].type)) {
                if (this.data[colIndex][0].type == 'o') {
                    alert("恭喜o胜利！")
                } else if (this.data[colIndex][0].type == 'x') {
                    alert("恭喜x胜利！")
                }
            }
            // 列
            if ((this.data[0][cellIndex].type == this.data[1][cellIndex].type) && (this.data[1][cellIndex].type == this.data[2][cellIndex].type)) {
                if (this.data[0][cellIndex].type == 'o') {
                    alert("恭喜o胜利！")
                } else if (this.data[0][cellIndex].type == 'x') {
                    alert("恭喜x胜利！")
                }
            }
            // 对角
            if ((this.data[0][0].type == this.data[1][1].type) && (this.data[1][1].type == this.data[2][2].type)) {
                if (this.data[0][0].type == 'o') {
                    alert("恭喜o胜利！")
                } else if (this.data[0][0].type == 'x') {
                    alert("恭喜x胜利！")
                }
            }
            if ((this.data[0][2].type == this.data[1][1].type) && (this.data[1][1].type == this.data[2][0].type)) {
                if (this.data[0][2].type == 'o') {
                    alert("恭喜o胜利！")
                } else if (this.data[0][2].type == 'x') {
                    alert("恭喜x胜利！")
                }
            }
        }
    }
}
</script>
<style>
    .page{
        padding: 0;
        margin: 0;
        text-align: center;
    }
    .table{
        width: 600px;
        height: 600px;
        margin: 50px auto;
    }
    .col{
        height: 200px;
        width: 100%;
        white-space: nowrap;
    }
    .cell{
        width: 200px;
        height: 200px;
        display: inline-block;
        line-height: 200px;
        border: 1px solid #999;
    }
</style>