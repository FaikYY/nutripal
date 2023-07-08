<template>
    <div class="container">
        <div class="total-facts">
            <h3 class="total-calories-label">Total Calories:</h3>
            <span class="total-calories-value">100</span>
            <div class="nutrition-fact-item">
                <div class="fact total-fact" v-for="(value, label) in totalFact" :key="label">
                    <span class="total-calories-label fact-label">Total {{ label }}:</span>
                    <span class="fact-value">{{ value }}</span>
                </div>
            </div>
        </div>
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
    name: "NutritionFacts",
    props: ["nutritionFact"],
    computed: {
        filteredFacts() {
            const facts = { ...this.nutritionFact };
            return Object.entries(facts).map(([key, value]) => ({
                key: key,
                name: value.name,
                properties: Object.entries(value).map(([label, propValue]) => ({
                    label: this.formatLabel(label),
                    value: propValue,
                })),
            }));
        },
        totalFact() {
            let totalFact = {};
            this.filteredFacts.forEach(fact => {
                fact.properties.forEach(item => {
                    // Check if the value is numeric to prevent name sum operation
                    if (!isNaN(Number(item.value))) {
                        if (!totalFact[item.label]) {
                            totalFact[item.label] = 0;
                        }
                        totalFact[item.label] += Number(item.value);
                        totalFact[item.label] = Number(totalFact[item.label].toFixed(4));
                    }
                });
            });
            return totalFact;
        }
    },
    methods: {
        formatLabel(label) {
            let formattedLabel = label.replace(/_/g, ' '); // Replace underscores with spaces
            formattedLabel = formattedLabel.charAt(0).toUpperCase() + formattedLabel.slice(1); // Capitalize the first letter
            if (formattedLabel.includes(' g') || formattedLabel.includes(' mg')) { // Add parentheses if needed
                formattedLabel = formattedLabel.replace(' g', ' (g)').replace(' mg', ' (mg)');
            }
            return formattedLabel;
        }
    }
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

.total-fact {
    width: calc(50% - 20px);
    padding: 5px;
    /* margin: 5px; */
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
    font-size: 0.8rem;
}

.fact-value {
    margin-left: 10px;
    font-size: 0.75rem;
    color: var(--color-primary);
}

.total-facts {
    margin-top: var(--size-xs);
    font-size: 1.2rem;
    font-weight: bold;
}

.total-calories-label {
    display: inline-block;
    margin-right: 5px;
}
</style>
  