<template>
    <td class="table__column">
        <div class="block"><img class="block__img" :src="imageSrc" alt="">
            <div class="cost">
                <div class="cost__number">{{ item.id }}.</div>
                <div class="cost__price">{{ item.price }} у.е.</div>
            </div>
        </div>
    </td>
</template>

<script>
    export default {
        name: "VendingItem",
        props: {
            item: Object,
        },
       computed: {
                imageSrc() {
                    return this.isAvailable ? this.item.imagePath : './images/empty.png'
                    // if (this.item.count > 0) {
                    //     return this.item.imagePath
                    // }
                    // return './images/empty.png'
                },
                isAvailable() {
                    return this.item.count > 0
                },
            }
    }
</script>
