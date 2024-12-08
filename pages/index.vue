<template>
    <NuxtLayout name="root-layout">
    <div class="sm:pt-32 pt-20 pb-16 sm:pb-5 ">
        <MainLanding />
    </div>
        <CollectionLanding class="pt-20 pb-16 sm:pb-5 "/>
    <div class="pt-20 pb-16 sm:pb-5">
        <ReductionLanding />
    </div>
        <Support class="pt-20 pb-16 sm:pb-5 "/>
    <!-- </div> -->
    </NuxtLayout>
</template>

<script setup>
const props = defineProps({
    Title: {
        type: String,
        default: "Data to enrich your"
    },
    TitleInline: {
        type: String,
        default: "online business"
    },
    Description: {
        type: String,
        default: "Anim aute id magna aliqua ad ad non deserunt sunt. Qui irure qui lorem cupidatat commodo. Elit sunt amet fugiat veniam occaecat fugiat aliqua."
    },
    btnEnabled: {
        type: Boolean,
        default: true
    }
});
</script>