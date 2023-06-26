<template>
    <div class="nutrition">
        <p v-if="nutritionInfo.name">Name: {{ nutritionInfo.name }}</p>
        <p v-if="nutritionInfo.calories">Calories: {{ nutritionInfo.calories }}</p>
        <p v-if="nutritionInfo.protein_g">Protein: {{ nutritionInfo.protein_g }}</p>
        <p v-if="nutritionInfo.fat_total_g">Fat: {{ nutritionInfo.fat_total_g }}</p>
    </div>
</template>

<script>
export default {
    name: 'NutritionInfo',
    props: ['nutritionInfo']
}
</script>