<template>
  <div class="modal fade" id="revampNews" tabindex="-1" role="dialog" aria-labelledby="myModalLabel"
       aria-hidden="true">
    <div class="modal-dialog" role="document">
      <div class="modal-content">
        <div class="modal-title" id="myModalLabel">
          <button type="button" id="close" class="close" data-dismiss="modal" aria-hidden="true">&times;
          </button>
          <h1 class="modal-header">修改新闻信息<span id="newsId" style="display: none">{{modifyData.newsID}}</span></h1>
        </div>
        <div class="modal-body">
          <form class="form-horizontal">
            <div class="form-group">
              <label for="title" class="col-2 control-label">
                <i>标题</i>
              </label>
              <input id="title" type="text" class="form-control col-10" name="parts_city_title"
                     v-bind:value="modifyData.newsTitle">
            </div>
            <div class="form-group">
              <label for="publishTime">
                <i>汽配城名称</i>
              </label>
              <input id="publishTime" type="text" class="form-control" name="parts_city_name"
                     v-bind:value="modifyData.publishTime">
            </div>
            <div class="form-group">
              <label for="content">
                <i>汽配城简介</i>
              </label>
              <textarea id="content" rows="3" class="form-control" name="parts_city_content">{{modifyData.cityContent}}</textarea>
            </div>
            <div class="form-group">
              <label for="imgUrl">
                <i>汽配城图片</i>
              </label>
              <input id="imgUrl" type="file" class="form-control" name="parts_city_img_url"/>
              <!--v-bind:value="modifyData.cityImgUrl">-->
            </div>
          </form>
        </div>
        <div class="modal-footer" style="">
          <button type="button" value="" class="btn btn-sm btn-secondary" data-dismiss="modal">返回</button>
          <button type="button" value="" class="btn btn-sm btn-primary" @click="revampData">确认</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "RevampCity",
    props: ['modifyData'],
    methods: {
      revampData: function () {
        let _this = this;
        this.$axios({
          url: _this.HOME + '/news/modify',
          method: 'POST',
          headers: { 'content-type': 'application/x-www-form-urlencoded' },
          data: _this.qs.stringify({
            "news_id": $('#newsId').text(),
            "news_title": $('#title').val(),
            "publish_time": $('#publishTime').val(),
            "news_content": $('#content').val(),
            "news_img_url": $('#imgUrl').val(),
          })
        }).then(res => {
          alert(res.data.message);
          $('#close').click();
          _this.$emit('dataInteractTrue');
        }).catch(e => {
          console.log(e);
        })
      }
    }
  }
</script>

<style scoped>

</style>
