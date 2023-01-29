<template>
    <td class="table__column">
        <div class="block"><img class="block__img" :src="item.imagePath" alt="">
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
    }
</script>
