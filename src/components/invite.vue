<template>
<div class="main" :style="'height:'+screenHeight+'px'">
    <div class="first-son">
        <img :src="'../../static/img/'+avatar" class="avatar lf">
        <div class="lf">
            <p class="purple">{{uname}}喊你来答题</p>
            <p>答对<span class="purple">{{$store.state.questionCount}}题</span>，平分万元奖金池</p>
        </div>
        <div class="clear"></div>
        <p class="center">接受对方的邀请，两人都将获得一张复活卡</p>
    </div>
    <div class="second-son">
      	<div class="index-left">
				<p class="index-today">{{($store.state.gameInfo.activity_exists && showStartTime*1)?(((new Date(showStartTime*1)).getDate()-(new Date()).getDate()) >=3 ?
          (new Date(showStartTime*1)).getMonth()-0+1 + '月' + ((new Date(showStartTime*1)).getDate()-0) + '日':
          ((new Date(showStartTime*1)).getDate()-(new Date()).getDate()) >=2 ?
          '后天' :
          ((new Date(showStartTime*1)).getDate()-(new Date()).getDate()) >=1 ?
          '明天':'今天'
          ):'下一场'}}</p>
				<p class="index-time">{{($store.state.gameInfo.activity_exists && showStartTime*1)?
          (((new Date(showStartTime*1).getHours())<10?'0'+(new Date(showStartTime*1).getHours()):(new Date(showStartTime*1).getHours()))+":"+((new Date(showStartTime*1).getMinutes())<10?"0"+(new Date(showStartTime*1).getMinutes()):(new Date(showStartTime*1).getMinutes())))
          :'即将到来'}}</p>
			</div>
			<div class="index-right">
				<p class="index-today">奖金池</p>
				<p class="index-money">{{$store.state.gameInfo.activity_exists? ((($store.state.gameInfo.amount_money)/10000) + '万') : '准备中'}}</p>
			</div>
    </div>
    <button class="join">预约参加</button>
    <p class="center">关注公众号 小司聊理财 了解答题攻略</p>
</div>    
</template>
<script>
import { screenHeight } from "../assets/utils/sceenHeight";
export default {
  name: "invite",
  data(){
      return{
          screenHeight:0,
          uname:"kk",
          avatar:"avatar.jpg"
      }
  },
  methods:{

  },
  mounted:function(){
      this.screenHeight=screenHeight();
  }
}    
</script>
<style lang="css" scoped>
.main{
    background: url("../assets/img/shareOut1.png") no-repeat;
    background-size:100% 100%;
    padding-top:200px; 
}
.avatar{
    width:52px;
    height:52px;
    border-radius: 50%;
    border:3px solid #fff;
}
.avatar+div{
    width:275px;
    height:70px;
    box-sizing: border-box;
    background: url("../assets/img/Rectangle.png") no-repeat;
    background-size:100% 100%; 
    padding:10px 0 0 30px;
    margin-left:5px;
    color:#333333;
}
.purple{
    color:#781DCF;
}
.avatar+div>p:last-child{
    font-size:18px;
}
.first-son>p:last-child{
    font-size:16px;
    padding-top:30px;
    margin-bottom: 10px;
}
.second-son{
    width:100%;
    height:110px;
    box-sizing: border-box;
    background: #fff;
    border-radius: 5px;
    color:#333333;
}
.join{
    margin-top:30px;
    width:100%;
    color:#781DCF;
    height:50px;
    box-sizing: border-box;
    font-size: 18px;
    border-radius: 5px;
    outline: none;
    border:0;
}
.join+p{
    margin-top:10px;
}
</style>
