<style lang="less" scoped>
    @import "./details.less";
</style>
<template>
    <div id="app">
        <h1>资讯详情</h1>  
        <Row :gutter="16" align="top">
            <Col span="18" style="background-color:#fff;padding:20px;height:500px;overflow-y: scroll;" >
                <div class="title">
                    <h3 class="h3">{{data[0].title}}</h3>
                    <img :src=data[0].cover alt="封面图片" class="cover">
                    <div class="line"></div>
                    <h5 class="h5">{{data[0].subtitle}}</h5>
                </div>
                <div class="content" v-html="data[0].content"></div>
            </Col>
            <Col span="6"  style="background-color:#fff">
                <Tag type="dot" closable color="blue" style="display:block;width:100px">来源信息</Tag>
                <div class="l1">
                    <p>编辑者</p>
                    <p>{{data[0].name}}</p>
                </div>
                <div class="l1">
                    <p>所属模块</p>
                    <p>{{data[0].lei}}</p>
                </div>
                <div class="l1">
                    <p>角色</p>
                    <p>{{data[0].role}}</p>
                </div>
                <div class="l2">
                    <p>发布时间</p>
                    <p>{{data[0].time}}</p>
                </div>
                <div class="l1">
                    <p>点赞数</p>
                    <p>{{data[0].thumbs}}</p>
                </div>
                <div class="l1">
                    <p>评论数</p>
                    <p>{{data[0].forword}}</p>
                </div>
                <div class="l1">
                    <p>评论数</p>
                    <p>{{data[0].comment}}</p>
                </div>
            </Col>
        </Row>
        <div class="active" v-if="display" style="position: absolute;right:0px;top:390px;background-color:#fff;height:200px;width:25%">
            <Tag type="dot" closable color="blue" style="display:block;width:100px;">内容操作</Tag>
            <div class="l3">
                <span>发布</span>
                <span>不发布</span>
            </div>
            <div class="l3">
                <span>置顶</span>
                <span>不置顶</span>
            </div>
            <div class="l3" style="padding-left:20px;padding-right:20px;margin-top:0px">
                <b>分类</b>
                <Select v-model="select">
                    <Option value="0">全部</Option>
                    <Option value="1">资讯全部分类</Option>
                    <Option value="2">其他分类</Option>
                </Select>
            </div>
            <div class="l3" style="margin-top:0px;">
                <Button type="primary" style="margin-top:30px" >保存</Button>
            </div>
            <div class="l3">
                <Button type="primary">查看全部文章</Button>
            </div>
            <div class="l3">
                <Button type="error">删除该内容</Button>
            </div>
        </div>
        <div class="active"></div>
         <Tag type="dot" closable color="blue" style="display:block;margin-top:20px;width:230px">评论列表</Tag>
        <Row type="flex" align="top" class="code-row-bg" :gutter="16">
            <Col span="18" style="background-color:#fff;height:300px;overflow-y: scroll">
                <Table border :columns="columns7" :data="data6"></Table>
            </Col>
            <Col span="6" style="background-color:#fff;height:300px;">
                 <Tag type="dot" closable color="blue" style="display:block;width:100px">内容机器人</Tag>
                <Form :model="formInline" :label-width="80">
                    <FormItem label="点赞数">
                        <Input v-model="formInline.praise" placeholder="请输入"></Input>
                    </FormItem>
                    <FormItem label="转发数">
                        <Input v-model="formInline.forward" placeholder="请输入"></Input>
                    </FormItem>
                    <FormItem label="评论数">
                        <Input v-model="formInline.comment" placeholder="请输入"></Input>
                    </FormItem>
                    <FormItem label="结缘数">
                        <Input v-model="formInline.kechien" placeholder="请输入"></Input>
                    </FormItem>
                    <FormItem>
                        <Button type="primary">提交机器人</Button>
                    </FormItem>
                </Form>
            </Col>
        </Row>
    </div>
</template>
<script>
    export default {
        name:"information_details",
        data(){
            return{
                spinShow: true,
                display:'',
                select:"",
                formInline: {
                    praise: '',
                    forward: '',
                    comment:'',
                    kechien:'',
                },
                data: [
                {
                    id:1,
                    name: "张三",
                    title:"资讯详情标题测试用",
                    subtitle:"资讯详情副标题测试用",
                    cover:"http://p0.ifengimg.com/pmop/2018/0227/32F18289287553767DC9EE7D7C9018948EEC1ACD_size11_w499_h321.jpeg",
                    content:'<div id="main_content" class="js_selection_area" data-fid="f73556cbf7d"><!--mainContent begin--><p>日前，三星S9已经发布。新机支持指纹、虹膜、面部三种识别功能，并且有高通骁龙845和三星Exynos 9810两大顶级SoC的加持，要知道骁龙845处理器是第二代10nm LPP工艺，性能和功耗上更胜上一代的骁龙835处理器，图形性能非常突出，这确保了其Android机皇地位，并且在当前来看，S9依然是你最早能买到的骁龙845手机，没有之一。要知道，三星旗舰的使命一向都是对标苹果，但从目前的形势来看，S9对标iPhone X，S9胜算几何？</p><p>对比S8，这次S9在工业设计上改进幅度并不大，屏幕显示方面，S8、S9系列的屏幕完全一致，并无差别。包括尺寸、分辨率都完全一致。电池规格上，S9系列与S8系列在3000mAh/3500mAh的电池容量上没有变化，不过骁龙845是一款更加省电的处理器，因而其整体续航表现预期是优于S8系列的。从配置来看，相机是S9最明显的改进，其中，S9为Super Speed Dual Pixel 1200万像素单摄，支持F1.5、F2.4可变光圈，前置镜头没有变化，依然是800万像素（F1.7）。</p><p class="detailPic"><img src="http://p0.ifengimg.com/a/2018_09/8989e72781e6e2a_size23_w500_h500.jpeg" width="500" height="500" alt=""></p><p>总体来看，三星S9给人的感觉是稳中求变，整体升级幅度不大，但在各方面的打磨却更为极致，在外观设计依然坚持了三星S系列固有的设计风格，包括5.8/6.2吋QHD+级全视曲面屏和双面玻璃机身。S8有的，S9都有，包括「IP68级防水防尘」、「虹膜识别」、「三星KNOX」、「无线充电」、「三星DeX」等代表三星手机的标志性的基因特性一应俱全，总体来看，三星S9比S8带来更为精细化的打磨与设计，包括更窄的下巴所带来更高的屏占比，指纹键也进行了优化与改进。</p><p>拍照是三星旗舰手机的重要卖点，尤其因为强悍的夜拍效果，三星表示，凭借Dual Pixel 等技术，Galaxy S9 系列可以比上代手机在夜间情况下获取超过4 倍的像素。但更重要的是，它可以实现慢动作视频拍摄，一眨眼可以拍出960 张视频；在现场，三星专门用了与水有关的慢动作视频拍摄，效果惊人。</p><p>三星为S9提供了可变光圈的功能支持，在拍照中可以在F/2.4与F/1.5光圈之间来回切换，这也是从过去的“大光圈虚化”到真真正正的改变了物理光圈的一次跃进，提供「F1.5」和「F2.4」两个档位，在自动模式下相机会根据环境自动切换光圈值，而在专业模式下，用户可以手动选择光圈值，在暗光环境下，三星S9会自动启用F/1.5大光圈，它能够在安全环境下提供更慢的快门，确保拍照不糊片与足够的亮度。这是三星在拍照功能上的一个重要卡位。也是新一代的拍照黑科技。</p><p>在过去，众多国产手机都将拍照作为重要卖点，如今S9的拍照效果一出，这可能意味着下一波国产手机需要寻找新的卖点方向了。</p><p>在处理器性能方面，苹果的iPhone X使用的是自家的A11仿生处理器，主频大约为2.4GHz，拥有6个处理核心。但可以肯定的是，无论是iPhone X还是S9系列，处理性能层面应该是不相伯仲的。而在屏幕方面，三星S9则比iPhone X更为出色，三星Galaxy S9搭载的是一块5.8英寸1440 x 2960 Super AMOLED显示屏，比iPhone X的5.8英寸1125 x 2436 Super Retina显示屏提供了更高的像素密度。在硬件配置与性能层面，三星S9可以说不输于甚至是超过了iPhone X。</p><p>但关键在于软件系统层面，尽管经历了降速门事件，但短时间内，人们对iOS独一性与稳定性、流畅性更强的固有的品牌认知很难改变，因此苹果依赖其封闭性的软件生态与品牌调性加持，在这方面，相对于三星S8，iPhone X依然在高端品牌的认可度上略胜一筹。</p><p>总体而言，三星S9是一款中规中矩、坚持小步快跑，将性能进行常规化升级的手机，但综合素质依然是Android阵营中最高的。在笔者看来，三星S9如果在定价上偏低一点，往往就能对在iPhone X观望的群体形成一定的收割之势。</p><p>毕竟，理由大家都懂的，三星在经历了note7燃损事件之后，虽然过去时间很久了，但是其用户信任度与忠诚度的重建依然是一个艰难的过程中，人们面对三星手机产品，裹挟了太多的情绪，如果三星能够在价格上做出一定让步，可能更能体现出三星对于中国这个特定市场的诚意，也更能扩大中国市场的占有率。</p><p>但遗憾的是，与苹果iPhone X的起售价格999相比，三星S9同样不遑多让，数据显示，三星S9在美国Verizon、AT＆TS9等运营商的零售价达到800美元左右，S9 Plus的价格相比S8 Plus上涨了100美元，达到了950美元左右。某种程度上，价格可能是阻挡人们尝鲜S9、收割iPhone X用户的一大门槛。</p><p>要知道，在目前，人们的换机周期变得越来越长，对于手机厂商而言，理所当然需要涨价来维持利润率，但这又是一对矛盾，如今iPhone X面临的问题是由于其价格高企而销量后劲不足，目前有消息称苹果将推出5800元左右的廉价版iPhone X来救场，但如果与三星S9竞争的话，廉价版iPhone X由于与iPhone X对比差距过于强烈，尤其是给予人们的社交资本的加持与保值性不足，部分用户倒向三星S9也不一定，但高企的价格或许也阻挡了三星这一波新的收割机会。</p><p>从iPhone X销量后劲不足可以看出，人们对价格的敏感度依然没有消失，而在一人多机的情况下，手机已经告别稀缺品的价值属性，要激发人们的购买欲变得越来越难，人们对手机价格的敏感度不减反增。</p><p>有业内人士表示，对于S8的用户而言，其升级的欲望应该不会太强烈。但是，问题的关键是，目前S8存量用户群体过于稀少，可以说，S9瞄准的用户群体依然是庞大的中高端用户群。</p><p>而S9要在全球畅销，中国市场是重中之重。因为在高端产品方面，中国的消费市场走势尽管在基本面上与全球市场的趋势一致，但在对高端产品的敏感度、关注度与需求度来看，比全球还要超前。</p><p>在当前消费升级与存量换机市场的情况下，让消费者掏腰包变得越来越难，在高端旗舰上的竞争，有几个重要因素非常重要，1：产品差异化与创新特性有几个点非常突出；2.品牌溢价能力能支撑售价。3.性能、创新与工业设计上有明显的亮点。4.配置上性能达到顶级。从目前来看，三星S9勉强能达成要求，但从今天来看，问题的关键是智能机市场的饱和程度已经非常突出，尤其在发达国家。</p><p>当整个行业面临下降周期而且头部厂商争夺存量市场变得空前激烈的时候，厂商将会通过更加激烈的价格战和库存战来抢占存量市场用户。这对于用户来说，在中高端价位，可选择性越来越多，这让用户的心理发生了变化，选择性太多干脆就不做选择，静待下一款能够有突破性改变的产品。这导致用户的换机周期越来越长。</p><p>根据Counterpoint的数据，中国手机用户的换机周期平均为22个月，全球市场的换机周期是21个月，而日前根据市场研究公司凯度集团（Kantar）的调查，2015年，美国人平均每隔23.6个月就更换手机，但是去年，换机周期延长到了25.3月。</p><p>笔者曾经指出，在刚需性需求缺乏的情况下，人们对于改善型的需求的价格有一个接受区间——而三星S9需要考虑的是，其性能与产品创新程度是否超过了用户在换机周期变长的情况下能接受的价格区间，这是防止市场需求被填补之后很快进入冷却期的一种价格层面的预判。</p><p>三星S9面临的对手可能就在于可能还包括国产手机，在中国市场，华为OV在中高端市场的影响力已经逐步做出来了，华为P20发布在即，在中国中高端市场，华为OV是三星不容忽视的对手。而且在用户认可度与渠道经营上，国产手机也更占优势。</p><p>总体而言，三星S9系列有着当前最为顶级的性能配置与拍照能力与工业设计，三星依然证明了它是Android阵营中在软硬件综合水平最高的企业。</p>',
                    time:"2017.7.1  10:47:32",
                    lei:"资讯",
                    role:"管理员",
                    thumbs:"5",
                    forword:"20",
                    comment:"15",
                },
            ],
            columns7: [
            {
                title: '序号',
                key: 'id',
            },
            {
                title: '昵称',
                key: 'name'
            },
            {
                title: '评论内容',
                key: 'comment_content'
            },
            {
                title: '评论时间',
                key: 'time'
            },
            {
                title: '操作',
                key: 'action',
                width: 300,
                align: 'center',
                render: (h, params) => {
                    return h('div', [
                        h('Button', {
                            props: {
                                type: 'primary',
                                size: 'small'
                            },
                            style: {
                                marginRight: '5px'
                            },
                            on: {
                                click: () => {
                                    this.show(params.index)
                                }
                            }
                        }, '查看内容'),
                        h('Button', {
                            props: {
                                type: 'info',
                                size: 'small'
                            },
                            style: {
                                marginRight: '5px'
                            },
                            on: {
                                click: () => {
                                    this.show(params.index)
                                }
                            }
                        }, '管理用户'),
                        h('Button', {
                            props: {
                                type: 'error',
                                size: 'small'
                            },
                            on: {
                                click: () => {
                                    this.remove(params.index)
                                }
                            }
                        }, '删除')
                    ]);
                }
            }
            ],
            data6: [
                    {
                        id:"1",
                        name: 'John Brown',
                        comment_content: 18,
                        time: '2017.7.1  10:47:32'
                    },
                    {
                        id:"2",
                        name: '张三',
                        comment_content: 'Nam id semper purus',
                        time: '2017.7.1  10:47:32'
                    },
                   {
                        id:"3",
                        name: '张三',
                        comment_content: 'Nam id semper purus',
                        time: '2017.7.1  10:47:32'
                    },
                   {
                        id:"2",
                        name: '张三',
                        comment_content: 'Nam id semper purus',
                        time: '2017.7.1  10:47:32'
                    }
                ]
            }
        },
        methods: {
            show (index) {
                this.$Modal.info({
                    title: '评论详情',
                    content: `id：${this.data6[index].id}<br>姓名：${this.data6[index].name}<br>评论详情：${this.data6[index].comment_content}<br>评论时间：${this.data6[index].time}`
                })
            },
            remove (index) {
                this.data6.splice(index, 1);
            },
        }
    }
</script>
