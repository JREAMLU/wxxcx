<template>
    <div>
        <div class="news">
            <text class="news-title">惠民通APP</text>
            <block v-for="item in products" :key="item.id">
                <a :href="'/pages/news-detail/main?id=' + item.id">
                    <div class="news-item line">
                        <div class="news-item-pic">
                            <image mode="widthFix" :src="item.pic" class="news-item-image" width="" height=""></image>
                        </div>
                        <div class="news-item-words">
                            <div class="news-item-title"><text>{{item.title}}</text></div>
                            <div class="news-item-content"><text>{{item.content}}</text></div>
                        </div>
                    </div>
                </a>
            </block>
        </div>

        <div class="news">
            <text class="news-title">服务理念</text>
            <block v-for="item in services" :key="item.id">
                <a :href="'/pages/news-detail/main?id=' + item.id">
                    <div class="news-item line">
                        <div class="news-item-pic">
                            <image mode="widthFix" :src="item.pic" class="news-item-image" width="" height=""></image>
                        </div>
                        <div class="news-item-words">
                            <div class="news-item-title"><text>{{item.title}}</text></div>
                            <div class="news-item-content"><text>{{item.content}}</text></div>
                        </div>
                    </div>
                </a>
            </block>
        </div>
    </div>
</template>

<script>
import config from '../../config'

export default {

    data () {
        return {
            products: [
                {
                    'id': 100,
                    'pic': 'http://www.jsssha.com/wp-content/uploads/2016/07/%E7%89%A9%E8%81%94%E7%BD%91.jpg',
                    'title': '应用简介',
                    'content': '惠民通，您身边的贴身助手，随时随地处理您身边事—便民利民惠民是我们的服务理念'
                }
            ],

            services: [
                {
                    'id': 1000,
                    'pic': 'http://www.jsssha.com/wp-content/uploads/2016/07/%E7%89%A9%E8%81%94%E7%BD%91.jpg',
                    'title': '安防改造升级——利民',
                    'content': '随着科技不断发展、流动人口增加和城市人口集聚，给社会治安带来巨大的挑战，传统的犯罪打击手段已不足以应对。基于大数'
                },
                {
                    'id': 1001,
                    'pic': 'http://www.jsssha.com/wp-content/uploads/2016/07/201609230617002103-300x250.jpg',
                    'title': '特色政务服务——便民',
                    'content': '为加速推进“智慧城市”的建设步伐，建立智慧型城市管理格局，有效整合信息资源，推动跨部门、跨条线、跨行业的信息连通，集成惠民通平台'
                },
                {
                    'id': 1002,
                    'pic':'http://www.jsssha.com/wp-content/uploads/2016/10/%E6%9C%8D%E5%8A%A1%E7%AB%99%E6%AD%A3%E9%9D%A2%E5%9B%BE1-300x250.jpg',
                    'title': '社区民生服务——惠民',
                    'content': '随着全国各地新型智慧城市建设的快速发展，特别是进入大数据时代，智慧社区实为本地生活服务的互联网化，更加快捷方便地满足社区住户的生活'
                },
                {
                    'id': 1003,
                    'pic':'http://www.jsssha.com/wp-content/uploads/2016/07/%E6%83%A0%E6%B0%91%E4%B8%80%E5%8D%A1%E9%80%9A-300x250.jpg',
                    'title': '智慧一卡通',
                    'content': '公司与苏州市民卡公司、张家港社保局应用市民卡B卡深度合作，在“惠民一卡通”IC芯片中写入业主基本信息，并与NFC'
                }
            ]
        }
    },

    components: {
    },

    created () {
    },

    onLoad() {
        this.getProducts();
        this.getServices();
    },

    methods: {
        getProducts() {
            var that = this;
            wx.request({
                url: config.API_URL.NEWS,
                method: 'POST',
                data: {
                    pageindex: 9,
                    pagesize: 1,
                },
                header: {
                    'content-type': 'application/json',
                },
                success: function(res) {
                   that.news = res.data.data.list;
                },
            });
        },
        getServices() {
            var that = this;
            wx.request({
                url: config.API_URL.NEWS,
                method: 'POST',
                data: {
                    pageindex: 10,
                    pagesize: 4,
                },
                header: {
                    'content-type': 'application/json',
                },
                success: function(res) {
                   that.news = res.data.data.list;
                },
            });
        }
    },

    watch: {
    }
}
</script>

<style scoped>
@import "../../../static/css/app.css";
</style>
