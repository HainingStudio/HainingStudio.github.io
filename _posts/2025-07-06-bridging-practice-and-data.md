---
layout: post
title: Bridging Practice and Data — Visualizing Chinese Herbs
data_story: true
description: Combining field observation in the pharmacy with large-scale data analysis from the SymMap database to understand how nature, taste, and part used shape traditional Chinese medicine.
date: 2025-07-06 10:30:00
image: '/images/23.jpg'
tags: [TCM, Data Visualization, Science]
tags_color: '#3478e5'
---

### Introduction: From Pharmacy Shelves to Data Tables

My exploration of Chinese herbs began in my family's pharmacy, where I learned to identify, weigh, and prepare different medicinal materials. But beyond these practical skills, I became increasingly fascinated by the logic behind herb classification — how ancient physicians described the world through *nature (性)* and *taste (味)*.

To better understand this structure, I turned to **real, large-scale data** — specifically,  
**[SymMap v1.0: Symptom–Herb Mapping Database](https://www.symmap.org/)**, a scientific dataset developed by Peking University and collaborators.  
This database integrates information from both traditional Chinese medicine (TCM) literature and modern biomedical sources, linking **499 herbs** to their properties, components, and indications.

---

### Data Source and Method

In the original SymMap dataset, every herb is annotated with:
- **Nature (性)** — how the herb affects the body’s temperature balance: *cold, cool, neutral, warm,* or *hot*  
- **Taste (味)** — its dominant flavor profile: *sour, bitter, sweet, pungent,* or *salty*  
- **Part Used (部位)** — which part of the plant is used: *root, leaf, flower, bark, seed,* etc.  
- **Associated Functions and Targets** — the herb’s described pharmacological actions and molecular-level targets (for modern correlation studies)

I focused on these three descriptive attributes to explore how TCM concepts translate into measurable patterns.  
The data was processed using **Python (pandas)** and visualized with **Altair**, producing an interactive dashboard stored as  
 {% raw %}
<div id="herb-vis" style="max-width:900px;margin:2rem auto;"></div>

<!-- Vega / Vega-Lite / Vega-Embed CDN -->
<script src="https://cdn.jsdelivr.net/npm/vega@5"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-lite@5"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-embed@6"></script>

<script>
  const specUrl = "/images/herb_dashboard.json"; // 你的 JSON 路径
  vegaEmbed("#herb-vis", specUrl, {actions: false})
    .then(({view}) => {
      // 可选：view.resize();
    })
    .catch(console.error);
</script>
{% endraw %}
.

This dashboard allows users to:
- View the *Nature × Taste* heatmap of 499 herbs  
- Filter results by part used (root, seed, leaf, etc.)  
- Compare how flavor and thermal properties vary across different plant parts  
- Observe patterns that align with classical TCM theory

---

### Quantitative Patterns in Traditional Classification

From the aggregated data, several interesting distributions emerged:

1. **“Sweet” and “Warm” dominate** — Over 30% of all herbs fall under the category of *sweet* in taste and *warm* in nature.  
   These herbs are often restorative or tonifying, such as *Ginseng (人参)*, *Astragalus (黄芪)*, and *Licorice (甘草)*, which strengthen Qi and improve energy circulation.

2. **“Bitter” herbs are usually “Cold” or “Cool”** — This combination accounts for roughly a quarter of the dataset.  
   It supports classical doctrine: *bitter clears heat*. Herbs like *Coptis (黄连)* and *Scutellaria (黄芩)* are used to eliminate internal heat and reduce inflammation.

3. **“Pungent” correlates with “Warm”** — Many herbs that disperse cold or promote circulation share this profile.  
   Examples include *Ginger (生姜)* and *Cinnamon twig (桂枝)*, both used to expel wind-cold and unblock the meridians.

4. **Neutral and mild herbs are relatively few** — Only about 10–15% of herbs are classified as neutral.  
   These herbs tend to harmonize rather than strongly stimulate or suppress physiological activity, like *Jujube (大枣)* or *Poria (茯苓)*.

---

### Structural Diversity by Part Used

When analyzing **which parts of plants are most frequently medicinal**, clear patterns also emerged:

- **Roots and rhizomes** make up nearly 40% of all recorded herbs — their concentration of active compounds corresponds with TCM’s emphasis on “root vitality.”  
- **Leaves and flowers** represent about 25%, mostly associated with dispersing effects, cooling actions, or external symptom relief.  
- **Seeds and fruits** (around 15%) are more often linked to internal nourishment or stabilizing functions.  
- **Barks and stems** have specialized, often purgative or detoxifying roles.

This distribution reflects not only the physiological structure of plants but also how Chinese pharmacology evolved from centuries of empirical observation — connecting *part function* with *organ function* in the human body.

---

### Linking Data and Doctrine

When plotted in a **Nature × Taste matrix**, clusters become visually evident:  
most *cold-bitter* herbs concentrate in the upper left, while *warm-sweet* herbs dominate the lower right — an elegant data pattern mirroring centuries of textual tradition.

Even without explicitly coding these rules, the dataset reflects **TCM’s internal logic**:  
- **Bitter → descends, drains, clears heat**  
- **Sweet → tonifies, harmonizes, moistens**  
- **Pungent → disperses, moves Qi and blood**  
- **Sour → consolidates, prevents leakage**  
- **Salty → softens hardness, purges accumulations**

Each function connects taste, nature, and physiological outcome, illustrating how **TCM embodies a natural taxonomy of effects**, long before biochemical analysis existed.

---

### Discussion: Tradition Meets Data Science

What’s fascinating about this project is how ancient descriptive systems align with modern analytical frameworks.  
Through simple data grouping and visualization, we can observe:
- Hierarchical clustering among herbs of similar taste/nature combinations  
- Correlations between thermal property and botanical part  
- The persistence of empirical logic across centuries, validated by large datasets

In modern biomedical studies, such datasets allow cross-referencing between traditional classifications and chemical compound families —  
for instance, *flavonoids* are often bitter and cooling, while *volatile oils* contribute to warming and pungent effects.  
This overlap demonstrates how **traditional taste and nature descriptors capture underlying biochemical principles** in surprisingly accurate ways.

> Data doesn’t replace experience — it amplifies it.  
> Through visualization, we can *see* the wisdom once only described in words.

---

### Conclusion

By merging first-hand observation from the pharmacy with large-scale data analysis, I found that the art of traditional Chinese medicine is inherently quantitative.  
Patterns once described as “warm” or “bitter” can now be expressed as measurable distributions — not to diminish their poetry, but to deepen understanding.  

The `/images/herb_dashboard.json` file represents more than a dataset; it is a bridge — connecting modern data science with centuries of sensory experience, observation, and healing logic.

{: .tip }
This visualization and analysis are part of my broader bilingual TCM education project, aimed at helping young learners see the beauty of traditional knowledge through interactive, data-driven storytelling.
