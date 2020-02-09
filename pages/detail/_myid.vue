<template>
    <div>
        detail--{{$route.params.myid}}
    </div>
</template>
<script>
export default {
    layout: "detailtemplate",
    asyncData(data) {
        console.log(data.params)
    }
}
</script>