<template>
  <div class="">
    <div class="row">
      <div class="col-md-12">
        <h3 class="header smaller lighter blue" style="text-align: left">简历管理列表</h3>
        <div class="table-responsive">
          <div id="sample-table-2_wrapper" class="dataTables_wrapper" role="grid">
            <table class="table-bordered table-striped">
              <thead>
              <tr>
                <th></th>
                <th></th>
                <th></th>
                <th></th>
                <th></th>
                <th></th>
                <th></th>
                <th></th>
                <th></th>
                <th></th>
              </tr>
              </thead>
              <tbody></tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
    <revamp :modifyData="modifyData" v-on:dataInteractTrue="dataInteractTrue"></revamp>
    <add v-on:dataInteractTrue="dataInteractTrue"></add>
  </div>
</template>

<script>
  import revamp from '../revmap/RevampResume'
  import add from '../add/AddResume'

  export default {
    name: "Resume",
    components: {revamp: revamp, add:add},
    data() {
      return {
        cityList: [],
        all: '',
        cur: 1,
        allElement: '',
        modifyData: '',
        table: '',
        educationOption: ['高中', '大专', '本科', '硕士', '博士', '博士后'],
      }
    },
    created: function () {
      try {
        ace.settings.check('breadcrumbs', 'fixed')
      } catch (e) {
      }
    },
    mounted: function () {
      let _this = this;
      _this.table = $('table').DataTable({
        language: {
          "processing": "处理中...",
          "lengthMenu": "显示 _MENU_ 项结果",
          "zeroRecords": "没有匹配结果",
          "info": "显示第 _START_ 至 _END_ 项结果，共 _TOTAL_ 项",
          "infoEmpty": "显示第 0 至 0 项结果，共 0 项",
          "infoFiltered": "(由 _MAX_ 项结果过滤)",
          "infoPostFix": "",
          "search": "搜索:",
          "searchPlaceholder": "搜索...",
          "url": "",
          "emptyTable": "表中数据为空",
          "loadingRecords": "载入中...",
          "infoThousands": ",",
          "paginate": {
            "first": "首页",
            "previous": "上页",
            "next": "下页",
            "last": "末页"
          },
          "aria": {
            "paginate": {
              "first": "首页",
              "previous": "上页",
              "next": "下页",
              "last": "末页"
            },
            "sortAscending": "以升序排列此列",
            "sortDescending": "以降序排列此列"
          },
          "thousands": "."
        },
        serverSide: true,
        searching: false,
        deferRender: true,
        paging: true,
        info: false,
        pageLength: 10,
        ajax: function (data, callback, settings) {
          $.ajax({
            url: _this.HOME + '/vitae/list',
            type: 'get',
            data: {
              "page": _this.cur,
              "type": '0',
              "size": '',
            },
            success: function (data) {
              var returnData = {};
              _this.cityList = data.data.content;
              _this.all = data.data.totalPages;
              returnData.recordsTotal = data.data.totalPages;//返回数据全部记录
              returnData.recordsFiltered = data.data.totalElements;//后台不实现过滤功能，每次查询均视作全部结果
              returnData.data = data.data.content;//返回的数据列表
              callback(returnData);
            },
          })
        },
        dom: "<'row'<'col-md-6'l<'#toolbar'>><'col-md-6'f>r>t<'row'<'col-md-5 sm-center'i><'col-md-7 text-right sm-center'p>>",
        columnDefs: [
          {
            targets: 9,
            data: "",
            title: "操作",
            render: function (data, type, row, meta) {
              return "<div class=\"\">\n" +
                "<a class=\"\" href=\"#\">\n" +
                "<i class=\"fa fa-search-plus bigger-130\"></i>\n" +
                "</a>\n" +
                "<a class=\"green\" href=\"#\" data-toggle=\"modal\" data-target=\"#revampVitae\">\n" +
                "<i class=\"fa fa-pencil bigger-130\"></i>\n" +
                "</a>\n" +
                "<a class=\"red\" href=\"#\">\n" +
                "<i class=\"fa fa-trash bigger-130\"><span style='display: none'>" + row.id + "</span></i>\n" +
                "</a>\n" +
                "</div>";
            }
          },
          {
            targets: 8,
            data: "mobilePhoneNum",
            title: "手机号",
          },
          {
            targets: 7,
            data: "education",
            title: "学历",
            render: function (data, type, row, meta) {
              return _this.educationOption[row.education - 1];
            }
          },
          {
            targets: 6,
            data: "",
            title: "工作年限",
            render: function (data, type, row, meta) {
              return row.workingLife + '年';
            }
          },
          {
            targets: 5,
            data: "birthday",
            title: "生日",
          },
          {
            targets: 4,
            data: "",
            title: "性别",
            render: function (data, type, row, meta) {
              if (Math.ceil(row.sex) === 1) {
                return '男';
              } else if (Math.ceil(row.sex) === 2) {
                return '女';
              }
            }
          },
          {
            targets: 3,
            data: "name",
            title: "姓名",
          },
          {
            targets: 2,
            data: "salary",
            title: "期望薪资",
          },
          {
            targets: 1,
            data: "wantedPosition",
            title: "职位类别",
          },
          {
            targets: 0,
            data: "id",
            title: "Id",
          },
        ],
        buttons: [
          'copy', 'excel', 'pdf'
        ],
        initComplete: function () {
          //手动添加按钮到表格上
          $("#toolbar").css("float", "left").css("display", "inline").css("margin-left", "10px");
          $("#toolbar").append("<input type='button' value='新建' class='btn-purple' style='color: #fff; margin-right: 5px;' data-toggle=\"modal\" data-target=\"#addVitae\"/>");
          // $("#toolbar").append("<input type='button' value='修改' class='btn-success'/>");
          // $("#toolbar").append("<input type='button' value='删除' class='btn-pink' style='margin: 0 5px 0 0;color: #fff;'/>");
          // $("#toolbar").append("<input type='button' value='全部删除' class='btn-info'/>");
          $("#toolbar input[class='btn-yellow']").click(_this.deleteData);
          let deleteButton = $("tr").children('td').children("div").children('a[class="red"]');
          $(deleteButton).click(_this.deleteData)
          $("tr").children('td').children("div").children('a[class="green"]').click(_this.toModify);
          if (_this.all >= 2) {
            $('.dataTables_paginate>a').on('click', _this.pageClick);
          }
        },
      });
    },
    methods: {
      deleteData: function (e) {
        let index = $(e.target).children().text();
        let delete_this = this;
        if (confirm('确定删除？')) {
          this.$axios({
            method: 'post',
            url: delete_this.HOME + '/vitae/delete?id=' + index,
          }).then(function (response) {
            if (Math.ceil(response.data.code) === 200) {
              delete_this.table.draw(false);
            }
          }).catch(function (error) {
            console.log(error);
          })
        }
      },
      toModify: function (e) {
        this.modifyData = this.cityList[$(e.target).parent().parent().parent().parent().index()];
      },
      dataInteractTrue: function (e) {
        this.table.draw(false);
      },
      pageClick: function (e) {
        this.cur = $(e.target).attr('data-dt-idx');
        this.table.page('next').draw(false);
      }

    }
  }
</script>

<style scoped>
  table {
    font-size: 14px;
    font-family: 微软雅黑;
    border: 1px solid #ddd;
    padding: 0;
  }

  table thead {
    background: #1a89ed;
    color: #ffffff;
    font-size: 18px;
  }

  .table-bordered > thead > tr > td, .table-bordered > thead > tr > th {
    border-bottom-width: 2px !important;
  }

  table.table-bordered tbody th, table.table-bordered tbody td {
    border-left-width: 0 !important;
    border-bottom-width: 0 !important;
  }

  .table-striped > tbody > tr:nth-of-type(odd) {
    background-color: #f9f9f9 !important;
  }

  .dataTable th[class*=sorting_] {
    color: #ffffff !important;
  }

  .dataTable th[class*=sort]:hover {
    color: #ffffff !important;
  }

  .table-bordered {
    border: 1px solid #ddd;
  }
</style>
