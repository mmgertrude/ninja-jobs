<template>
<div v-if="job"> 
<h1>{{job.title}}</h1>
<p>The Job id is {{$route.params.id}}</p>
<!-- OR 
<p>The Job id is {{$route.params.id}}</p> -->
<p>{{job.details}}</p>
</div>

<div v-else>
    <p> Loading job details ...</p>
</div>

</template>

<script>
export default {
    props: ["id"]
    // data(){
    //     return{
    //         id: this.$route.params.id
    //     }
    // }
,
data(){
return{
    job: null
}
},
mounted(){
        //fetch() API will fetch the data
        fetch("http://localhost:3000/jobs/" + this.id)
        .then((res) => res.json())
        .then(data => this.job = data)
        .catch(err => console.log(err.message)) //if there is one
    }
}
</script>

<style>

</style>