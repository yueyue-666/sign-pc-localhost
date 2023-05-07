<template>
  <div class="home">
    <a-row :gutter="24">
      <a-col :xl="12" :md="24">
        <a-card :bordered="false" title="账号资料"></a-card>
        <div class="info">
          <section>
            <img :src="require('@/assets/portrait.jpeg')" />
            <div class="zh">
              <span>账号：admin</span>
              <span>
                <a-icon slot="prefix" type="safety" :style="{ color: '#1890ff', fontSize: '15px' }" />3后台管理员
              </span>
            </div>
          </section>
          <div class="yl">
            <p>
              <span class="top">超级签名V2余量</span>
              <span>
                <em>992</em>
                台
              </span>
            </p>
            <p>
              <span class="top">超级签名V3余量</span>
              <span>
                <em>0</em>
                台
              </span>
            </p>
            <a-button key="submit" type="primary">充值</a-button>
          </div>
        </div>
        <div class="xhl">
          <section>
            <p>今日ios消耗量</p>
            <h5>0</h5>
          </section>
          <a-divider type="vertical" style="height: 80px; background-color:  #E6E6E6" />
          <section>
            <p>昨日ios消耗量</p>
            <h5>0</h5>
          </section>
          <a-divider type="vertical" style="height: 80px; background-color:  #E6E6E6" />
          <section>
            <p>今日Android下载量</p>
            <h5>0</h5>
          </section>
          <a-divider type="vertical" style="height: 80px; background-color:  #E6E6E6" />
          <section>
            <p>昨日Android下载量</p>
            <h5>0</h5>
          </section>
        </div>
      </a-col>
      <a-col :xl="12" :md="24">
        <a-card :bordered="false" title="数据统计" class="tj">
          <div class="xh">
            <section>
              <p>ios累计消耗量</p>
              <h5>1</h5>
            </section>
            <section>
              <p>Android累计消耗量</p>
              <h5>0</h5>
            </section>
            <section>
              <p>应用数量</p>
              <h5>3</h5>
            </section>
          </div>
        </a-card>
        <a-card :bordered="false" title="快捷操作" class="cz">
          <div class="xh">
            <section>
              <a-icon type="export" style="font-size:25px" color="#fff"></a-icon>
              <p>发布应用</p>
            </section>
            <section>
              <a-icon type="pay-circle" style="font-size:25px" color="#fff"></a-icon>
              <p>财务信息</p>
            </section>
            <section>
              <a-icon type="team" style="font-size:25px" color="#fff"></a-icon>
              <p>修改密码</p>
            </section>
          </div>
        </a-card>
      </a-col>
    </a-row>
    <a-row :gutter="24">
      <a-col :xl="24" :md="24">
        <a-card :bordered="false" title="常用应用">
          <a-table :columns="columns" :data-source="data">
            <a slot="name" slot-scope="text">{{ text }}</a>
            <span slot="customTitle">
              <a-icon type="smile-o" />Name
            </span>
            <span slot="tags" slot-scope="tags">
              <a-tag
                v-for="tag in tags"
                :key="tag"
                :color="tag === 'loser' ? 'volcano' : tag.length > 5 ? 'geekblue' : 'green'"
              >{{ tag.toUpperCase() }}</a-tag>
            </span>
            <span slot="action" slot-scope="text, record">
              <a>Invite 一 {{ record.name }}</a>
              <a-divider type="vertical" />
              <a>Delete</a>
              <a-divider type="vertical" />
              <a class="ant-dropdown-link">
                More actions
                <a-icon type="down" />
              </a>
            </span>
          </a-table>
        </a-card>
      </a-col>
    </a-row>
    <a-row :gutter="24">
      <a-col :xl="24" :md="24">
        <a-card :bordered="false" title="最近一周数据统计"></a-card>
      </a-col>
    </a-row>
  </div>
</template>

<script>
const columns = [
  {
    title: '应用名称',
    dataIndex: 'name',
    key: 'name',
    slots: { title: 'customTitle' },
    scopedSlots: { customRender: 'name' }
  },
  {
    title: '版本',
    dataIndex: 'age',
    key: 'age'
  },
  {
    title: 'ios消耗量',
    dataIndex: 'address',
    key: 'address'
  },
  {
    title: 'Tags',
    key: 'tags',
    dataIndex: 'tags',
    scopedSlots: { customRender: 'tags' }
  },
  {
    title: 'Action',
    key: 'action',
    scopedSlots: { customRender: 'action' }
  }
]
const data = [
  {
    key: '1',
    name: 'John Brown',
    age: 32,
    address: 'New York No. 1 Lake Park',
    tags: ['nice', 'developer']
  },
  {
    key: '2',
    name: 'Jim Green',
    age: 42,
    address: 'London No. 1 Lake Park',
    tags: ['loser']
  },
  {
    key: '3',
    name: 'Joe Black',
    age: 32,
    address: 'Sidney No. 1 Lake Park',
    tags: ['cool', 'teacher']
  }
]
export default {
  data() {
    return {
      data,
      columns
    }
  },
  created() {
    this.getUserData()
  },
  methods: {
    getUserData() {
      this.$http
        .post('/backstage/getUserData', {})
        .then(res => {
          // $('#infoiostoday').text(data.data.iosTodayUsed)
          // $('#infoiosyestoday').text(data.data.iosLastDayUsed)
          // $('#infoiosall').text(data.data.iosTotalUsed)
          // $('#infoandtoday').text(data.data.androidTodayUsed)
          // $('#infoandyestoday').text(data.data.androidLastDayUsed)
          // $('#infoandall').text(data.data.androidTotalUsed)
          console.log(res)
        })
        .catch(() => {})
    }
  }
}
</script>

<style scoped lang="less">
.home {
  .info {
    display: flex;
    color: #333;
    background: #f8f8f8;
    section {
      display: flex;
      flex: 1;
      text-align: center;
      padding: 19px;
      align-items: center;
      img {
        width: 70px;
        height: 70px;
        border-radius: 50%;
      }
      .zh {
        margin-left: 10px;
        height: 70px;
        display: flex;
        align-items: center;
        flex-direction: column;
        justify-content: center;
        span:nth-child(1) {
          font-size: 16px;
          color: #333;
        }
      }
    }
    .yl {
      padding: 19px;
      display: flex;
      align-items: center;
      p {
        display: flex;
        flex-direction: column;
        align-items: center;
        .top {
          padding: 3px;
          margin-right: 10px;
        }
        em {
          font-size: 30px;
          color: #ff5722;
          font-style: normal;
        }
      }
    }
  }
  .xhl {
    background-color: #fff;
    display: flex;
    padding: 43px 0;
    justify-content: space-evenly;
    margin-bottom: 20px;

    section {
      color: #999;
      h5 {
        color: #666;
        font-size: 30px;
        text-align: center;
      }
    }
  }

  .tj {
    margin-bottom: 10px;
    .xh {
      display: flex;
      color: #fff;
      line-height: 36px;
      justify-content: space-between;
      p {
        margin: 0;
      }

      h5 {
        margin: 0;
        color: #fff;
        font-size: 30px;
        text-align: center;
      }
      section {
        padding: 0 10px;
        display: flex;
        width: 30%;
        flex-direction: column;
        align-items: flex-start;
      }
      section:nth-child(1) {
        background-color: rgb(13, 107, 228);
      }
      section:nth-child(2) {
        background-color: rgb(0, 147, 229);
      }
      section:nth-child(3) {
        background-color: rgb(98, 128, 219);
      }
    }
  }

  .cz {
    margin-bottom: 10px;
    .xh {
      display: flex;
      color: #fff;
      line-height: 36px;
      justify-content: space-between;
      p {
        margin: 0;
      }

      section {
        padding: 10px 10px 0 10px;
        display: flex;
        width: 30%;
        flex-direction: column;
        align-items: center;
      }
      section:nth-child(1) {
        background-color: rgb(39, 198, 200);
      }
      section:nth-child(2) {
        background-color: rgb(0, 201, 133);
      }
      section:nth-child(3) {
        background-color: rgb(156, 93, 214);
      }
    }
  }
}
</style>