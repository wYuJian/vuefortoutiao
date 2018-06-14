<script type="text/ecmascript-6">
export default {
    name: 'ContentItem',
    props:['data'],
    data() {
        return {}
    },
    render() {
        return (
            <div class='item'>
                <div>
                    <img src={this.data.imgSrc} />
                </div>
                <div class='item-right'>
                    <p>{this.data.title}</p>
                    <div class='item-bottom'>
                        <span class='tag'>{this.data.label} </span>
                        <div class='source'>
                            <img src={this.data.certificationImg} />
                            <p > {this.data.certification} ⋅</p>
                        </div>
                        <span class='source'> {this.data.comm} ⋅</span>
                        <span class='source'>{this.data.time}</span>
                    </div>
                </div>
            </div>
        )
    },
    components: {},
    mounted() {},
    methods: {}
}
</script>

<style scoped lang="less">
.item{
    display: flex;
    flex-direction: row;
    align-items: center;
    padding: 10px 0;
    border-bottom: 1px solid #e8e8e8;
    .item-right{
        width: 80%;
        display: flex;
        text-align: left;
        flex-direction: column;
        margin-left: 16px;
        p{
            font-size: 20px;
            color: #222;
            font-weight: bold;
            margin: 0 0 20px 0;
        }
       .source{
            margin: 0 10px;
        }
        .item-bottom{
            display: flex;
            flex-direction: row;
            color: #777;
            font-size: 14px;
            .tag{
                font-size: 12px;
                padding: 1px 2px;
                border: 1px solid #87a5b5;
                color: #87a5b5;
            }
            div{
                display: flex;
                flex-direction: row;
                align-items: center;
                p{
                    margin: 0;
                    color: #777;
                    font-size: 14px;
                }
                img{
                    width: 18px;
                    height: 18px;
                    border-radius: 50%;
                }
            }
        }
    }
}

</style>
