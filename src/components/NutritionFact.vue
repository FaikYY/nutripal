<template>
    <div class="container">
        <div class="nutrition-info-container" v-for="fact in filteredFacts" :key="fact.key">
            <h3 class="fact-name">{{ fact.name ? fact.name.toUpperCase() : '' }}</h3>
            <div class="nutrition-fact-item">
                <div class="fact" v-for="item in fact.properties" :key="item.label">
                    <span class="fact-label">{{ item.label }}:</span>
                    <span class="fact-value">{{ item.value }}</span>
                </div>
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
.container {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    padding: 0.5rem;
    width: 100%;
}

.nutrition-info-container {
    padding: 20px;
}

.nutrition-fact-item {
    width: 25rem;
    display: flex;
    flex-wrap: wrap;
    padding: var(--size-m);
}

.fact {
    width: calc(50% - 20px);
    padding: 5px;
    margin: 5px;
}

.fact span {
    font-size: var(--size-m);
}

@media (max-width: 768px) {
    .container {
        width: 85%;
    }

    .fact span {
        font-size: calc(var(--size-s) + 0.2rem);
    }
}

@media (max-width: 576px) {
    .container {
        width: 85%;
    }

    .nutrition-fact-item {
        width: 85%;
    }

    .fact span {
        font-size: var(--size-m);
    }
}

@media (max-width: 450px) {
    .container {
        width: 85%;
    }

    .nutrition-fact-item {
        width: 85%;
    }

    .fact span {
        font-size: calc(var(--size-xs) + .1rem);
    }
}

.nutrition-info-container {
    background-color: #ffffff;
    border: 0.15rem solid rgba(29, 188, 87, 0.2);
    padding: 0.5rem;
    margin-bottom: 0.5rem;
    border-radius: 4px;
    box-shadow: 0px 2px 4px rgba(29, 188, 87, 0.1);
}

.fact-name {
    font-size: var(--font-size-l);
    font-weight: bold;
    color: var(--color-primary);
    margin-bottom: 10px;
}

.fact-label {
    font-weight: bold;
    color: var(--color-primary);
    font-size: 0.8rem;
}

.fact-value {
    margin-left: 10px;
    font-size: 0.75rem;
}
</style>
  