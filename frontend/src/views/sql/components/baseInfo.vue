<style scoped>
</style>

<template>
    <div>
      <div style="margin-top:10px;margin-bottom:10px">
        <Row>
          <Col span="2">
            <p> <b>ID：</b> </p>
          </Col>
          <Col span="10">
            <p> {{row.id}} </p>
          </Col>
          <Col span="2">
            <p> <b>数据库：</b>  </p>
          </Col>
          <Col span="10">
            <p> {{row.db_name}} </p>
          </Col>
        </Row>

        <Row>
          <Col span="2">
            <p> <b>提交时间：</b> </p>
          </Col>
          <Col span="10">
            <p> {{getTime}} </p>
          </Col>
          <Col span="2">
            <p> <b>影响的行数：</b>  </p>
          </Col>
          <Col span="10">
            <p> {{row.exe_affected_rows}} </p>
          </Col>
        </Row>

        <Row>
          <Col span="2">
            <p> <b>提交人：</b> </p>
          </Col>
          <Col span="10">
            <p> {{row.commiter}} </p>
          </Col>
          <Col span="2">
            <p> <b>执行人：</b>  </p>
          </Col>
          <Col span="10">
            <p> {{row.treater}} </p>
          </Col>
        </Row>

        <Row>
          <Col span="2">
            <p> <b>环境：</b> </p>
          </Col>
          <Col span="10">
            <p> {{row.env}} </p>
          </Col>
          <Col span="2">
            <p> <b>状态：</b>  </p>
          </Col>
          <Col span="10">
            <p v-if="row.status == -3" > <Tag>已回滚</Tag> </p>
            <p v-else-if="row.status == -2" > <Tag>已暂停</Tag> </p>
            <p v-else-if="row.status == -1" > <Tag color="blue">待执行</Tag> </p>
            <p v-else-if="row.status == 0" > <Tag color="green">已执行</Tag> </p>
            <p v-else-if="row.status == 1" > <Tag color="yellow">已放弃</Tag> </p>
            <p v-else-if="row.status == 2" > <Tag color="red">执行失败</Tag> </p>
          </Col>
        </Row>
        <Row>
          <Col span="2">
            <p> <b>备注：</b> </p>
          </Col>
          <Col span="10">
            <p> {{row.remark}} </p>
          </Col>
        </Row>
      </div>
    </div>
</template>

<script>
export default {
  props: ['row', 'sqlContent'],
  computed: {
    getTime: function () {
      return this.row.createtime.split('.')[0].replace('T',' ')
    } 
  }
}
</script>


