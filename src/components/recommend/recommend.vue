<template>
  <div class="recommend">
    <div class="recommend-content">
      <div class="slider-wrapper">
        <slider>
          <div v-for="item in recommends">
            <a :href="item.linkUrl">
              <img :src="item.picUrl" />
            </a>
          </div>
        </slider>
      </div>
      <div class="recommend-list">
        <h1 class="list-title">xxx</h1>
        <ul>
        </ul>
      </div>
    </div>
  </div>
</template>

<script type="text/javascript">
  import Slider from 'base/slider/slider'
	//import {getRecommend} from 'api/recommend'
	import {ERR_OK} from 'api/config'
  import axios from 'axios'
  // import $ from 'jquery'
  import qs from 'qs';

	export default{
    data() {
      return {
        recommends: []
      }
    },
		created() {
			// this._getRecommend()
      axios.get('http://www.sixiaxiao.com:3000/aa')
      .then(res => {
        console.log(res.data);
      })
      .catch(err => {
        console.log(err);
      });


      // axios.post('http://www.sixiaxiao.com:3000/bb',{bb:"bb"})
      // .then(function(response){
      //   console.log(response.data);
      // })
      // .catch(function(err){
      //   console.log(err);
      // });
      // console.log(qs.stringify({name:'test',name2:'test2'}))
      axios.post('http://www.sixiaxiao.com:3000/bb',qs.stringify({name:'test'}))
      .then(res => {
        console.log(res.data);
      })
      .catch(err => {
        // console.log(err);
      });

      // $.ajax({
      //   url:'http://www.sixiaxiao.com:3000/bb',
      //   type:'post',
      //   data:{bb:'bb'},
      //   success:function(){
      //     console.log(1)
      //   }
      // })
		},
		methods: {
			// _getRecommend() {
			// 	getRecommend().then((res) => {
			// 		if(res.code === ERR_OK){
			// 			this.recommends = res.data.slider
			// 		}
			// 	})
			// }
		},
    components:{
      Slider
    }
	}
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
  @import "~common/stylus/variable"

  .recommend
    position: fixed
    width: 100%
    top: 88px
    bottom: 0
    .recommend-content
      height: 100%
      overflow: hidden
      .slider-wrapper
        position: relative
        width: 100%
        overflow: hidden
      .recommend-list
        .list-title
          height: 65px
          line-height: 65px
          text-align: center
          font-size: $font-size-medium
          color: $color-theme
        .item
          display: flex
          box-sizing: border-box
          align-items: center
          padding: 0 20px 20px 20px
          .icon
            flex: 0 0 60px
            width: 60px
            padding-right: 20px
          .text
            display: flex
            flex-direction: column
            justify-content: center
            flex: 1
            line-height: 20px
            overflow: hidden
            font-size: $font-size-medium
            .name
              margin-bottom: 10px
              color: $color-text
            .desc
              color: $color-text-d
      .loading-container
        position: absolute
        width: 100%
        top: 50%
        transform: translateY(-50%)
</style>