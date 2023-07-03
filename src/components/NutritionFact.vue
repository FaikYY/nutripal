<template>
    <div class="container">
        <div class="row">
            <div class="col" v-for="fact in filteredFacts" :key="fact.key">
                <div class="nutrition-fact">
                    <h3 class="name">{{ fact.name ? fact.name.toUpperCase() : '' }}</h3>
                    <div class="nutrition-info">
                        <div class="fact col2" v-for="item in fact.properties" :key="item.label">
                            <span class="label">{{ item.label }}:</span>
                            <span class="value">{{ item.value }}</span>
                        </div>
                    </div>
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
}

.row {
    display: flex;
    flex-wrap: wrap;
}

.col {
    flex: 0 0 33.33%;
    /* For PC size, 3 items in a row */
    padding: 10px;
    box-sizing: border-box;
}

.col2 {
    flex: 0 0 25%;
    /* For PC size, 4 items in a row */
    padding: var(--size-xxs);
    box-sizing: border-box;
}

@media (max-width: 768px) {

    /* For tablet size, 2 items in a row */
    .col {
        flex: 0 0 50%;
    }

    .col2 {
        flex: 0 0 33.3%;
    }
}

@media (max-width: 576px) {

    /* For phone size, 1 item per row */
    .col {
        flex: 0 0 100%;
    }

    .col2 {
        flex: 0 0 50%;
    }
}

.nutrition-fact {
    background-color: #ffffff;
    border: 0.15rem solid rgba(29, 188, 87, 0.2);
    padding: 0.5rem;
    margin-bottom: 0.5rem;
    border-radius: 4px;
    box-shadow: 0px 2px 4px rgba(29, 188, 87, 0.1);
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
  