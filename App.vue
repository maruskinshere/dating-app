<script>


export default{
    data(){
        return{
            profiles:[
                {id: 1, name:'Dasha', bio: 'Люблю готовить', img: 'https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.pinterest.com%2Flyssacat05%2Fbrown-cats%2F&psig=AOvVaw2k91KHu5MvBSEGQD9KNUDf&ust=1742055696131000&source=images&cd=vfe&opi=89978449&ved=0CBQQjRxqFwoTCNjw-qn9iYwDFQAAAAAdAAAAABAE'},
                {id: 2, name:'Pasha', bio: 'Люблю готовить', img: 'https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.reddit.com%2Fr%2Faww%2Fcomments%2F18v9hf%2Fchocolate_cat_where_can_i_get_one%2F&psig=AOvVaw2k91KHu5MvBSEGQD9KNUDf&ust=1742055696131000&source=images&cd=vfe&opi=89978449&ved=0CBQQjRxqFwoTCNjw-qn9iYwDFQAAAAAdAAAAABAJ'},
                {id: 3, name:'Sasha', bio: 'Люблю готовить', img: 'https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.litter-robot.com%2Fblog%2Fhavana-brown-cat%2F&psig=AOvVaw2k91KHu5MvBSEGQD9KNUDf&ust=1742055696131000&source=images&cd=vfe&opi=89978449&ved=0CBQQjRxqFwoTCNjw-qn9iYwDFQAAAAAdAAAAABAS'},


            ],
            profilesindex: 0,
            likeprof:[],
            showlikes: false
        };
    },
    methods:{
        getCurrentProfile(){
            return this.profiles[this.profilesindex] || {};
        },
        like(){
            this.likeprof.push(this.getCurrentProfile())
            this.nextprofile()
        },
        dislike(){
            this.nextprofile()
            
        },
        nextprofile(){
            this.profilesindex ++;
            if(this.profilesindex >= this.profiles.length){
                this.profiles = [];
            }
        }, 
        showlikesmodule(){
            this.showlikes = true;

        }




    }
}
</script>

<template>
    <div class="app">
        <div v-if="profiles.length > 0" class="main">
        <img :src="getCurrentProfile().img" alt="">
        <h1>{{ getCurrentProfile().name }}</h1>
        <p>{{ getCurrentProfile().bio }}</p>
        <div class="but">
            <button @click="like()" class="like2">Like</button>
            <button @click="dislike()">Dislike</button>
        </div>
    </div>
    <div v-else>
        <p class="t2">Профили закончились</p>
    </div>
    <button @click="showlikesmodule()" class="butlike">Liked profiles {{ likeprof.length }}</button>
    <div v-if="showlikes" class="module">
        <h2 class="t3">Yours likes</h2>
        <div v-for="profile in likeprof" :key="profile.id" class="modulelike">
            <img :src="profile.img" alt="">
            <p>{{ profile.name }}</p>
            <p>{{ profile.bio }}</p>
        </div>
        <button @click="showlikes = false" class="close">Close</button>
        
    </div>
            
    </div>
</template>

<style scoped>
.app{
    display: flex;
    justify-content: center;
    align-items: center;
}
.but{
    background-color: rgb(209, 187, 216);
    border-radius: 10px;
    padding: 15px;
    width: 150px;
}
.buttons{
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 15px;
    
}

</style>
