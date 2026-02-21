# Wellspring Engagement Study

**Live slideshow:** [https://xaderf.github.io/wellspring-study/](https://xaderf.github.io/wellspring-study/)

## Host Online (GitHub Pages)

This repository is configured to auto-deploy `index.html` to GitHub Pages with GitHub Actions.

1. Push to the `main` branch.
2. In GitHub, open `Settings` -> `Pages`.
3. Set **Source** to **GitHub Actions**.
4. In `Settings` -> `Actions` -> `General`, set **Workflow permissions** to **Read and write permissions**.
5. Wait for the `Deploy Slides to GitHub Pages` workflow to finish.
6. Your public URL will be: `https://xaderf.github.io/wellspring-study/`

### If You See `Failed to create deployment (status: 404)`

This usually means GitHub Pages is not enabled for the repo yet, or the workflow token cannot write Pages deployments.

1. Confirm `Settings` -> `Pages` is enabled and set to **GitHub Actions**.
2. Confirm `Settings` -> `Actions` -> `General` has **Read and write permissions** enabled.
3. Re-run the failed workflow from the **Actions** tab after saving those settings.

## Update the Slideshow

If you edit `wellspring.qmd`, rebuild `index.html` and push:

```bash
quarto render wellspring.qmd --to revealjs --output index.html
git add wellspring.qmd index.html
git commit -m "Update slides"
git push
```

## Overview

This project analyzes member engagement at **Wellspring**, a Canadian cancer support organization, following the introduction of a new registration system in March 2024. The study explores how **family status, gender, age, and program interests** relate to participation in Wellspring programs.

The goal is to provide insights that help Wellspring understand drivers of engagement and identify strategies to support diverse members.

---

## Data

Two main datasets were used:

1. **Member Background**  
   - 4,829 members  
   - Demographics, cancer history, program interests, and attendance metrics  
   - Most members from Ontario; average age ~56; majority female  

2. **Service Deliveries**  
   - 45,254 records of program sessions between 2023–2024 for 3,780 members  
   - Most sessions delivered online; attendance marked as “Present” or “Absent”

**Key Variables:**

- `member_id` – Unique member identifier  
- `parent_of_a_child_under_18` – Yes / No / Unknown  
- `gender` – Self-identified gender  
- `age_years` – Age of member  
- `program_interest` – Programs of interest  
- `number_of_present_service_deliveries` – Total sessions attended  
- `number_of_absent_service_deliveries` – Total sessions missed  
- `membership_duration` – Calculated in months from start date  

---

## Methods

### Data Cleaning

- Missing parental status coded as **Unknown**  
- Attendance datasets merged with member information  
- Bootstrapping and multiple regression used to examine engagement patterns  

### Analyses

1. **Research Question 1 (RQ1)**  
   - How do **age, number of program interests, and membership duration** jointly predict total services attended?  
   - **Method:** Multiple linear regression  
   - **Findings:**  
     - Longer membership strongly increases attendance  
     - More program interests lead to higher participation  
     - Older members attend slightly more sessions, but effect is modest  

2. **Research Question 2 (RQ2)**  
   - Do members **with children under 18** attend services differently than those without?  
   - **Method:** Comparison of attendance distributions & hypothesis testing  
   - **Findings:**  
     - Members with children attend fewer sessions on average  
     - Median attendance lower and more concentrated than for members without children  
     - Suggests family responsibilities may limit participation  

3. **Research Question 3 (RQ3)**  
   - How has the **new registration system** affected engagement by gender?  
   - **Method:** Two-proportion hypothesis testing using bootstrapped test statistics  
   - **Findings:**  
     - No statistically significant difference in engagement between male and female members  
     - Slight improvement for female-identifying members observed, but not significant  

---

## Visualizations

- **RQ1:** Partial effects plots for age, program interests, and membership duration  
- **RQ2:** Boxplots comparing attendance by parental status  
- **RQ3:** Boxplot of bootstrapped differences in engagement between genders  

---

## Limitations

- **Limited variables:** Only age, membership duration, program interests, gender, and parental status included  
- **Data quality:** Missing or unspecified values may affect conclusions  
- **Temporal factors:** Cross-sectional analysis; may not capture seasonal or recent changes  
- **Unmeasured influences:** Employment, caregiving schedules, motivation, health, and socioeconomic factors  

---

## Recommendations

1. Collect additional variables on **employment, caregiving, and scheduling availability** to explain participation gaps  
2. Conduct **subgroup analyses** (e.g., age × gender, parental status × program interest)  
3. Track **long-term engagement trends** beyond early months of registration  
4. Leverage **program interest** data for targeted outreach and cross-promotion  

---

## Conclusion

- **Engagement patterns** are influenced by membership duration, program interest, and family responsibilities  
- **System-level changes** like the new registration system may have subtle effects, but personal and social factors remain key drivers  
- Insights can inform **retention strategies, outreach, and program design** to support Wellspring members more effectively

## Notes

**Contributions:** This project was completed as a group. I specifically worked on Research Question 1 (RQ1), including data cleaning, regression analysis, and visualization for that question.
