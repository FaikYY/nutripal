<!-- TODO: add all the information from the API response -->
<!-- TODO: calculate the total intake of everthing and display it at the end -->


<template>
    <div class="nutrition-fact" v-for="nutrition in nutritionFact" :key="nutrition.id">
        <h3 class="name">{{ nutrition.name ? nutrition.name.toUpperCase() : '' }}</h3>
        <div class="nutrition-info">
            <div class="fact">
                <span class="label">Calories:</span>
                <span class="value">{{ nutrition.calories }}</span>
            </div>
            <div class="fact">
                <span class="label">Protein:</span>
                <span class="value">{{ nutrition.protein_g }}</span>
            </div>
            <div class="fact">
                <span class="label">Fat:</span>
                <span class="value">{{ nutrition.fat_total_g }}</span>
            </div>
            <div class="fact">
                <span class="label">Carbs:</span>
                <span class="value">{{ nutrition.carbohydrates_total_g }}</span>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'NutritionFact',
    props: ['nutritionFact']
}
</script>

<style scoped>
.nutrition-fact {
    background-color: #fff;
    border: 1px solid #ddd;
    padding: 20px;
    margin-bottom: 10px;
}

.name {
    font-size: 18px;
    font-weight: bold;
    margin-bottom: 10px;
}

.nutrition-info {
    display: flex;
    flex-wrap: wrap;
}

.fact {
    width: 50%;
    margin-bottom: 5px;
}

.label {
    font-weight: bold;
}

.value {
    margin-left: 10px;
}
</style>