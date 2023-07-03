<template>
    <div class="nutrition-fact" v-for="fact in filteredFacts" :key="fact.key">
        <h3 class="name">{{ fact.name ? fact.name.toUpperCase() : '' }}</h3>
        <div class="nutrition-info ">
            <div class="fact" v-for="item in fact.properties" :key="item.label">
                <span class="label">{{ item.label }}:</span>
                <span class="value">{{ item.value }}</span>
            </div>
        </div>
    </div>
</template>
  
<script>
export default {
    name: "NutritionFact",
    props: ["nutritionFact"],
    computed: {
        filteredFacts() {
            const facts = { ...this.nutritionFact };
            return Object.entries(facts).map(([key, value]) => ({
                key: key,
                name: value.name,
                properties: Object.entries(value).map(([label, propValue]) => ({
                    label,
                    value: propValue,
                })),
            }));
        },
    },
};
</script>
  
<style scoped>
.nutrition-fact {
    background-color: #ffffff;
    border: .15rem solid rgb(29, 188, 87, 0.2);
    padding: 0.5rem;
    margin-bottom: .5rem;
    border-radius: 4px;
    box-shadow: 0px 2px 4px rgba(29, 188, 87, 0.1);
    width: 100%;
}

.name {
    font-size: var(--font-size-l);
    font-weight: bold;
    color: var(--color-primary);
    margin-bottom: 10px;
}

.nutrition-info {
    display: flex;
    flex-wrap: wrap;
}

.fact {
    width: 100%;
    margin-bottom: 5px;
}

.label {
    font-weight: bold;
    color: var(--color-primary);
    font-size: 0.8rem;
}

.value {
    margin-left: 10px;
    font-size: 0.75rem;
}
</style>