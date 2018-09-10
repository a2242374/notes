# 模拟table

#### HTML

```html
<div class="main-list">
  <div class="block main-data-scroll">
    <el-row class="table_title" align="center" :gutter="5" style="width: 100%;">
      <el-col :span="1"><span>序号</span></el-col>
      <el-col :span="3"><span>供应商名称</span></el-col>
    </el-row>
    <div @click="jumpSupplierDetails(item.compId)" v-for="(item,index) in tableData" :key="index">
    <el-row class="inner" type="flex" align="middle" :gutter="5" >
      <el-col  :span="1"><div class="cell">{{index+1}}</div></el-col>
      <el-col  :span="3"><div class="cell" :title="item.compName" align="left">{{item.compName}}</div></el-col>
    </el-row>
    </div>
    <div class="none-data" v-show="tableData.length==0">暂无数据</div>
  </div>
  <div class="block tar scrollHeight">
    <el-pagination
      background
      @size-change="handleSizeChange"
      @current-change="handleCurrentChange"
      :page-sizes="[10, 20, 30, 50]"
      :page-size="form.size"
      :total="form.total"
      :current-page="form.pageNo"
      layout="total, sizes, prev, pager, next, jumper"
    >
    </el-pagination>
  </div>
</div>
```
#### CSS

```css
.my-data-list{
  .el-row{
    margin-bottom: 0;
  }
  .my-data-list-hd{
    border-bottom: 1px solid #EEEEEE;
    .tal{
      text-align: left;
    }
    .cell{
      line-height: @my-list-height;
      height: @my-list-height;
      font-size: 14px;
    }
  }
  .my-data-list-bd{
    //max-height: 530px;
    overflow-y:hidden;
    overflow-x: hidden;
    .el-row{
      border-bottom: 1px solid #EEEEEE;
      &:hover{
        background: #F5F7FA;
      }
    }
    .el-row:last-child{
      //border-bottom: 0 none;
    }
    .sortable-chosen{
      border-bottom: 1px dashed #ccc;
      background: #F5F7FA;
    }
    .enable-class{ //是否启用
      @{deep} .el-input__inner{
        width: 70px;
      }
    }
    .cell{
      line-height: @my-list-height;
      height: @my-list-height;
      font-size: 12px;
      color: #666;
      .banner-name @{deep} input{

      }
      .thumbnail-box{
        position: relative;
        width: 140px;
        height: 37px;
        display: inline-block;
        cursor: pointer;
        &:hover:after{
          content:'查看原图';
          width: 100%;
          height: 37px;
          line-height: 37px;
          background: #000;
          color: #fff;
          opacity: 0.7;
          display:block;
          position: absolute;
          left: 0;
          top: 7px;
        }
        .close-img{
          position: absolute;
          right: -3px;
          top: 2px;
          width: 18px;
          height: 18px;
          background: #fff;
          border-radius:50%;
          display: inline-block;
          z-index: 100;
          font-size: 20px;
          &:before{
            position: relative;
            left: -2px;
          }
          &:hover:before{
            color: #525252;
          }
        }
        .banner-mini{
          width: 140px;
          height: 37px;
          position: relative;
          top: 7px;
          &::after{
            content: '';
            background: #000;
          }
        }
      }
    }
  }
}
```


