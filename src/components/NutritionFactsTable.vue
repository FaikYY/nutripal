<template>
    <section class="performance-facts">
        <header class="performance-facts__header">
            <h1 class="performance-facts__title">Nutrition Facts</h1>
            <p>Serving Size 1/2 cup (about 82g)</p>
        </header>
        <table class="performance-facts__table">
            <thead>
                <tr>
                    <th colspan="3" class="small-info">
                        Amount Per Serving
                    </th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <th colspan="2">
                        <b>Calories</b>
                        200
                    </th>
                </tr>
                <tr class="thick-row">
                    <td colspan="3" class="small-info">
                        <b>% Daily Value*</b>
                    </td>
                </tr>
                <tr>
                    <th colspan="2">
                        <b>Total Fat</b>
                        14g
                    </th>
                    <td>
                        <b>22%</b>
                    </td>
                </tr>
                <tr>
                    <td class="blank-cell">
                    </td>
                    <th>
                        Saturated Fat
                        9g
                    </th>
                    <td>
                        <b>22%</b>
                    </td>
                </tr>
                <tr>
                    <td class="blank-cell">
                    </td>
                    <th>
                        Trans Fat
                        0g
                    </th>
                    <td>
                    </td>
                </tr>
                <tr>
                    <th colspan="2">
                        <b>Cholesterol</b>
                        55mg
                    </th>
                    <td>
                        <b>18%</b>
                    </td>
                </tr>
                <tr>
                    <th colspan="2">
                        <b>Sodium</b>
                        40mg
                    </th>
                    <td>
                        <b>2%</b>
                    </td>
                </tr>
                <tr>
                    <th colspan="2">
                        <b>Total Carbohydrate</b>
                        17g
                    </th>
                    <td>
                        <b>6%</b>
                    </td>
                </tr>
                <tr>
                    <td class="blank-cell">
                    </td>
                    <th>
                        Dietary Fiber
                        1g
                    </th>
                    <td>
                        <b>4%</b>
                    </td>
                </tr>
                <tr>
                    <td class="blank-cell">
                    </td>
                    <th>
                        Sugars
                        14g
                    </th>
                    <td>
                    </td>
                </tr>
                <tr class="thick-end">
                    <th colspan="2">
                        <b>Protein</b>
                        3g
                    </th>
                    <td>
                    </td>
                </tr>
            </tbody>
        </table>

        <table class="performance-facts__table--grid">
            <tbody>
                <tr>
                    <td colspan="2">
                        Vitamin A
                        10%
                    </td>
                    <td>
                        Vitamin C
                        0%
                    </td>
                </tr>
                <tr class="thin-end">
                    <td colspan="2">
                        Calcium
                        10%
                    </td>
                    <td>
                        Iron
                        6%
                    </td>
                </tr>
            </tbody>
        </table>

        <p class="small-info">* Percent Daily Values are based on a 2,000 calorie diet. Your daily values may be higher or
            lower depending on your calorie needs:</p>

        <table class="performance-facts__table--small small-info">
            <thead>
                <tr>
                    <td colspan="2"></td>
                    <th>Calories:</th>
                    <th>2,000</th>
                    <th>2,500</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <th colspan="2">Total Fat</th>
                    <td>Less than</td>
                    <td>65g</td>
                    <td>80g</td>
                </tr>
                <tr>
                    <td class="blank-cell"></td>
                    <th>Saturated Fat</th>
                    <td>Less than</td>
                    <td>20g</td>
                    <td>25g</td>
                </tr>
                <tr>
                    <th colspan="2">Cholesterol</th>
                    <td>Less than</td>
                    <td>300mg</td>
                    <td>300 mg</td>
                </tr>
                <tr>
                    <th colspan="2">Sodium</th>
                    <td>Less than</td>
                    <td>2,400mg</td>
                    <td>2,400mg</td>
                </tr>
                <tr>
                    <th colspan="3">Total Carbohydrate</th>
                    <td>300g</td>
                    <td>375g</td>
                </tr>
                <tr>
                    <td class="blank-cell"></td>
                    <th colspan="2">Dietary Fiber</th>
                    <td>25g</td>
                    <td>30g</td>
                </tr>
            </tbody>
        </table>

        <p class="small-info">
            Calories per gram:
        </p>
        <p class="small-info text-center">
            Fat 9
            &bull;
            Carbohydrate 4
            &bull;
            Protein 4
        </p>

    </section>
</template>

<script>
export default {
    name: "NutritionFactsTable",
};
</script>

<style>
@charset "UTF-8";

.image {
    width: 250px;
    float: left;
    margin: 20px;
}

body {
    font-size: small;
    line-height: 1.4;
}

p {
    margin: 0;
}

.performance-facts {
    border: 1px solid black;
    margin: 20px;
    float: left;
    width: 280px;
    padding: 0.5rem;
}

.performance-facts table {
    border-collapse: collapse;
}

.performance-facts__title {
    font-weight: bold;
    font-size: 2rem;
    margin: 0 0 0.25rem 0;
}

.performance-facts__header {
    border-bottom: 10px solid black;
    padding: 0 0 0.25rem 0;
    margin: 0 0 0.5rem 0;
}

.performance-facts__header p {
    margin: 0;
}

.performance-facts__table,
.performance-facts__table--grid,
.performance-facts__table--small {
    width: 100%;
}

.performance-facts__table thead tr th,
.performance-facts__table--grid thead tr th,
.performance-facts__table--small thead tr th,
.performance-facts__table thead tr td,
.performance-facts__table--grid thead tr td,
.performance-facts__table--small thead tr td {
    border: 0;
}

.performance-facts__table th,
.performance-facts__table--grid th,
.performance-facts__table--small th,
.performance-facts__table td,
.performance-facts__table--grid td,
.performance-facts__table--small td {
    font-weight: normal;
    text-align: left;
    padding: 0.25rem 0;
    border-top: 1px solid black;
    white-space: nowrap;
}

.performance-facts__table td:last-child,
.performance-facts__table--grid td:last-child,
.performance-facts__table--small td:last-child {
    text-align: right;
}

.performance-facts__table .blank-cell,
.performance-facts__table--grid .blank-cell,
.performance-facts__table--small .blank-cell {
    width: 1rem;
    border-top: 0;
}

.performance-facts__table .thick-row th,
.performance-facts__table--grid .thick-row th,
.performance-facts__table--small .thick-row th,
.performance-facts__table .thick-row td,
.performance-facts__table--grid .thick-row td,
.performance-facts__table--small .thick-row td {
    border-top-width: 5px;
}

.small-info {
    font-size: 0.7rem;
}

.performance-facts__table--small {
    border-bottom: 1px solid #999;
    margin: 0 0 0.5rem 0;
}

.performance-facts__table--small thead tr {
    border-bottom: 1px solid black;
}

.performance-facts__table--small td:last-child {
    text-align: left;
}

.performance-facts__table--small th,
.performance-facts__table--small td {
    border: 0;
    padding: 0;
}

.performance-facts__table--grid {
    margin: 0 0 0.5rem 0;
}

.performance-facts__table--grid td:last-child {
    text-align: left;
}

.performance-facts__table--grid td:last-child::before {
    content: "•";
    font-weight: bold;
    margin: 0 0.25rem 0 0;
}

.text-center {
    text-align: center;
}

.thick-end {
    border-bottom: 10px solid black;
}

.thin-end {
    border-bottom: 1px solid black;
}
</style>