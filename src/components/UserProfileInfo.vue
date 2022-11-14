<template>
    <div class="card">
        <div class="card-body">
            <div class="row">
        <div class="col-3">
            <img class="img-fluid" src="https://cdn.acwing.com/media/user/profile/photo/216501_lg_0d931dc027.jpg" alt=""/>
        </div>
        <div class="col-9">
            <div class="username">{{fullName}}</div>
            <div class="fans">{{user.followerCount}}</div>
            <button @click="follow" v-if="!user.is_followed" type="button" class="btn btn-secondary btn-sm">+关注</button>
            <button @click="unfollow" v-if="user.is_followed" type="button" class="btn btn-secondary btn-sm">取消关注</button>
        </div>
    </div>
        </div>
    </div>
    
</template>

<style scoped>
img{
    border-radius: 50%;
}
.username{
    font: bolder;
}

.fans{
    font-size: 12px;
    color: grey;
}

button{
    padding: 2px 4px;
    font-size: 12px;
}
</style>

<script>
import {computed} from 'vue';

export default{
    name : "UserProfileInfo",
    props:{
        user: {
            type:Object,
            required: true,
        }
    },
    setup(props,context){
        let fullName = computed(()=>props.user.lastName+' '+props.user.firstName);

        const follow = ()=>{
            context.emit('follow');
        }
        
        const unfollow = ()=>{
            context.emit('unfollow');
        }

        return {
            fullName,
            follow,
            unfollow,
        }
    }
}
</script>
