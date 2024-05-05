# Nutrition-Optimized-Menu-Planning
This GitHub repository provides tools and data for optimizing menu planning across different age groups. The focus is on maximizing nutrition and cost efficiency in meal plans tailored to diverse demographic needs.

## Table of Contents
- [Relevance of the problem](#relevance-of-the-problem)
- [Problem Description](#problem-description)
- [Model Formulation](#model-formulation)
  - [Decision Variables](#decision-variables)
  - [Objective Function](#objective-function)
  - [Constraints](#constraints)
- [Numerical Analysis](#numerical-analysis)
  - [Comparative Analysis of Combined vs. Individual Optimization](#comparative-analysis-of-combined-vs-Individual-Optimization)
  - [Impact of Relaxing Diversity Constraints](#Impact-of-Relaxing-Diversity-Constraints)
  - [Price Sensitivity Analysis](#Price-Sensitivity-Analysis)
- [Conclusion](#conclusion)

## Relevance of the problem

## Problem Description  

## Model Formulation
### Model data
The model includes nutritional requirements and item information for various demographic groups:

#### 1. Nutritional Requirements by Demographic Group
This data was gathered from the U.S. Department of Health and Human Services. The data contains nutritional goals for each age/sex group used
in assessing the adequacy of USDA Food Patterns at various calorie levels - [Link](https://health.gov/sites/default/files/2019-09/Appendix-E3-1-Table-A4.pdf)
| Age Group       | Calories | Sodium | Carbohydrates | Dietary Fiber | Protein | Total Fat |
|-----------------|----------|--------|---------------|---------------|---------|-----------|
| Male Child      | 1400     | 2050   | 130           | 19.6          | 26.5    | 30        |
| Female Child    | 1600     | 2050   | 130           | 22.4          | 26.5    | 30        |
| Male Teenager   | 2800     | 2300   | 130           | 30.8          | 52      | 30        |
| ...             | ...      | ...    | ...           | ...           | ...     | ...       |
| Female Adult    | 1800     | 2300   | 130           | 25.2          | 46      | 30        |
| Male Adult      | 2200     | 2300   | 130           | 30.8          | 56      | 30        |

#### 2. Nutritional Information by Menu Item

| Item                         | Calories | Sodium | Carbohydrates | Dietary Fiber | Protein | Total Fat |
|------------------------------|----------|--------|---------------|---------------|---------|-----------|
| Egg McMuffin                 | 300      | 750    | 31            | 4             | 17      | 13        |
| Egg White Delight            | 250      | 770    | 30            | 4             | 18      | 8         |
| ...                          | ...      | ...    | ...           | ...           | ...     | ...       |
| McFlurry ... (Medium)        | 810      | 400    | 114           | 2             | 21      | 32        |
| McFlurry ... (Snack)         | 410      | 200    | 57            | 1             | 10      | 16        |

#### 3. Cost Per Item
The original dataset did not contain this information. This data was appended to the original dataset that contained only the nutritional information. 

| Item                         | Cost  |
|------------------------------|-------|
| Egg McMuffin                 | \$2.50 |
| Egg White Delight            | \$2.50 |
| ...                          | ...   |
| McFlurry ... (Medium)        | \$2.25 |
| McFlurry ... (Small)         | \$1.85 |

### Decision Variables

### Objective Function
The objective function aims to minimize the total cost by optimizing menu choices for different demographic groups:

$$
min \ Z = \sum_{i} \sum_{j} c_i \cdot x_{ij}
$$

where:
-  $c_i$  is the cost of item $i$.
-  $x_{ij}$  is the number of units of item $i$ consumed by demographic group $j$.


### Constraints
The model includes several constraints to ensure nutritional needs and item selection diversity:

- **Nutrition Needs Constraint:**       
  Ensures nutritional requirements are met for each demographic group based on selected menu items.

- **Category Constraint:**  
  Ensures a minimum number of items are chosen from specific menu categories (e.g., breakfast, chicken and fish, beef and pork).

For specific categories:    
- **Breakfasts (Items 1-42):**

$$ \sum_{i=1}^{42} u_{ij} $$

- **Chicken and Fish (Items 43-57):**      

$$ \sum_{i=43}^{57} u_{ij} \geq 3 $$

- **Beef and Pork (Items 58-84):**       

$$ \sum_{i=58}^{84} u_{ij} \geq 3 $$


- **Salads (Items 85-90):**

$$ \sum_{i=85}^{90} u_{ij} \geq 3 $$

- **Snack and Sides (Items 91-103):**

$$ \sum_{i=91}^{103} u_{ij} \geq 3 $$

- **Dessert (Items 104-110):**

$$ \sum_{i=104}^{110} u_{ij} \geq 3 $$

- **Beverages (Items 111-137):**

$$ \sum_{i=111}^{137} u_{ij} \geq 3 $$

- **Coffee and Tea (Items 138-232):**

$$ \sum_{i=138}^{232} u_{ij}$$ 


$$
\
\    .             
\    .       
\    .    
\
$$

$$ \sum_{i=233}^{260} u_{ij} $$

- **Diversity Constraint:**     
  Limits the number of units of each item consumed by a demographic group to ensure variety in the diet.

- **Lower Bound Constraint:**      
  Ensures that the decision variable is binary, indicating whether an item is chosen for a demographic group.

## Numerical Analysis 
### Comparative Analysis of Combined vs. Individual Optimization
This study compares two optimization approaches for meeting nutritional needs across different age groups. By evaluating concurrent optimization of menu schedules for all age groups versus individual optimization for each group, the research aims to determine the most effective method in fulfilling dietary requirements while respecting specific constraints and guidelines for each demographic category. Two menu designs were created: one aimed at meeting overall nutritional needs for all demographics at a minimal cost, and another tailored to the unique nutritional requirements of each demographic group.

### Impact of Relaxing Diversity Constraints
In this experiment, we adjusted the Diversity Constraint to observe its impact on optimized menus. Surprisingly, even with a significantly looser constraint, the results remained similar to more constrained settings. This suggests that menu diversity was inherently limited, aligning with the unique dietary needs of each group while optimizing cost efficiency.

### Price Sensitivity Analysis
This analysis examines the impact of item price variations on menu composition, essential for business profitability and consumer satisfaction. To maintain profitability and customer appeal, businesses like McDonald’s must understand how price adjustments affect menu choices. Similarly, consumers' purchasing decisions are influenced by price changes, emphasizing affordability and value. We conduct two experiments from these dual perspectives: one focused on inflation-based scenarios, and the other on market disruptions affecting item prices.

## Conclusion

## Future Work
- [ ] Adding an interface to turn this model into a web application
- [ ] Add an efficient implementation of the Simplex algorithm - Python
- [ ] Try changing the model to get more insights from the business perspective.
  - [ ] Changing the objective to maximize the cost(Selling Price)
  - [ ] Products that need improvement/boost in marketing
