## 1. The Executive Data Analysis Workflow

The workflow consists of four stages:

### D1: Discover

**Question:** What data do I have?

Copilot reviews the workbook and explains its worksheets, columns, measures, relationships, data quality, and possible business purpose.

### D2: Diagnose

**Question:** What analyses are possible?

Copilot identifies meaningful analyses supported by the available data and explains the business value of each.

### D3: Decide

**Question:** Which analyses matter most for my role and decision?

Copilot prioritises the most relevant analyses for roles such as CEO, CFO, COO, CHRO, Sales Head, Operations Head, or Regional Manager.

### D4: Deliver

**Question:** How do I perform the selected analysis effectively?

The participant selects one analysis and uses an RTCFCT meta-prompt to generate a detailed, professional Copilot prompt.

> **Workflow:** Workbook → Understand Data → Discover Analyses → Prioritise by Role → Select Analysis → Generate RTCFCT Prompt → Perform Analysis → Verify Output → Decide and Act

## 2. Objective

Before asking Copilot to analyse a workbook, first ask it to explain what is actually available. This reduces the risk of selecting an analysis that the workbook cannot support.

Copilot should identify:

- Workbook purpose, where reasonably evident from the data
- Worksheet names and the likely purpose of each worksheet
- Tables, columns, fields, measures, and units
- Date or time fields
- Categories and dimensions
- Numerical and performance measures
- Possible relationships between worksheets or tables
- Missing values, duplicates, inconsistent formats, and other data-quality concerns
- Business questions that the available data may help answer
- Information that is not available but may be required for deeper analysis

## 4. Step 1 Prompt: Workbook Data Discovery

```text
Role:
Act as a senior business data analyst and Excel workbook reviewer.

Task:
Review the uploaded Excel workbook and explain what data it contains. Do not perform detailed business analysis yet. First help me understand the workbook's structure, contents, apparent business purpose, and readiness for analysis.

Context:
I am an executive officer who needs a clear, non-technical understanding of the workbook before deciding which analyses to perform. The workbook may contain multiple worksheets, tables, business measures, date fields, categories, and related datasets.

Output Format:
Present the response in the following sections:

1. Executive Overview
   - Briefly explain what the workbook appears to contain and its likely business purpose.

2. Workbook Structure
   - List every worksheet.
   - For each worksheet, explain its apparent purpose.
   - Identify the main table or data range, where detectable.

3. Data Dictionary
   - Provide a table with these columns:
     - Worksheet
     - Column or Field
     - Data Type
     - Plain-Language Meaning
     - Example Value
     - Possible Business Use

4. Key Measures and Dimensions
   - Identify numerical measures, categories, dates, locations, products, customers, employees, departments, or other important dimensions.

5. Relationships
   - Explain possible relationships between worksheets or tables.
   - Identify likely common keys, such as Employee ID, Customer ID, Product ID, Order ID, Department, Region, or Date.
   - Clearly label any inferred relationship as an assumption.

6. Data-Quality Review
   - Identify missing values, duplicate records, inconsistent labels, blank rows, formula errors, mixed date formats, outliers, or other visible concerns.

7. Business Questions Supported by the Data
   - List the business questions that can reasonably be answered using the available fields.

8. Data Gaps
   - Identify information that is missing and may be required for more advanced or reliable analysis.

Constraints:
- Base the response only on information available in the workbook.
- Do not invent the meaning of unclear fields.
- Clearly distinguish facts observed in the workbook from assumptions or interpretations.
- Do not calculate or claim findings that the available data does not support.
- Explain technical terms in plain business language.
- Mention worksheets or fields that appear empty, hidden, incomplete, or unusable, if detectable.
- Protect confidential, personal, financial, regulated, or sensitive information. Do not reproduce unnecessary record-level sensitive data.

Tone:
Professional, executive-friendly, clear, concise, neutral, and data-driven.
```

## 5. Questions the Executive Should Ask After Step 1

Use these questions to validate Copilot's understanding:

- Has Copilot identified every worksheet?
- Are all important measures and dimensions included?
- Has Copilot distinguished observed facts from inferred meanings?
- Are the relationships between tables supported by common fields?
- Are date ranges, currencies, percentages, and units clear?
- Are there missing values, duplicates, outliers, or inconsistent labels?
- Does the workbook contain enough information to answer the intended business question?
- Is any confidential or personal information present?

## 6. Optional Step 1 Follow-Up Prompts

### Create a concise data dictionary

```text
Using the workbook review, create a concise data dictionary. For every field, provide the worksheet, field name, data type, plain-language definition, example value, and possible business use. Mark uncertain definitions as "Requires confirmation".
```

### Check analysis readiness

```text
Assess whether this workbook is ready for business analysis. Group issues into Critical, Important, and Minor. For every issue, state its possible impact on analysis and recommend a correction. Do not change the workbook.
```

### Identify sensitive information

```text
Review the workbook structure for fields that may contain confidential, personal, financial, regulated, or commercially sensitive information. Name the field categories without reproducing sensitive record-level values. Recommend safe handling precautions before using the data in an AI prompt.
```

---

# Step 2: Discover Analysis Opportunities

## 7. Objective

After understanding the workbook, ask Copilot to identify the analyses that the available data can genuinely support. At this stage, the goal is to create an analysis catalogue, not to perform every analysis.

## 8. Step 2 Prompt: Analysis Discovery

```text
Role:
Act as a senior business intelligence consultant and executive analytics advisor.

Task:
Based only on the data available in the uploaded workbook, identify meaningful analyses that can be performed. Provide analysis names and a one-line explanation for each analysis.

Context:
I have already reviewed the workbook's structure and now need to understand how its data can support operational, financial, customer, workforce, sales, risk, or strategic decisions. The analyses must be feasible using the fields present in the workbook.

Output Format:
Create a structured table with the following columns:

1. Analysis Name
2. One-Line Explanation
3. Business Question Answered
4. Key Fields Required
5. Suitable Executive or Functional Roles
6. Business Value: High, Medium, or Low
7. Complexity: Basic, Intermediate, or Advanced
8. Data Readiness: Ready, Partly Ready, or Not Ready

Group the analyses into relevant categories, such as:
- Descriptive analysis
- Trend analysis
- Comparative analysis
- Variance analysis
- Profitability or financial analysis
- Customer analysis
- Sales analysis
- Operational analysis
- Workforce analysis
- Risk analysis
- Forecasting or predictive analysis

Include only categories supported by the workbook.

Constraints:
- Recommend only analyses supported by the available fields.
- Do not invent missing variables or business rules.
- If an analysis requires unavailable data, mark it "Not Ready" and list the missing fields.
- Avoid presenting different names for essentially the same analysis.
- Keep each explanation to one clear sentence.
- Distinguish calculated analysis from predictive analysis.
- Do not perform the analyses at this stage.

Tone:
Professional, analytical, practical, concise, and decision-oriented.
```

## 9. Useful Analysis Types Copilot May Identify

The actual list must depend on the workbook. Typical categories may include:

- Summary statistics
- Trend analysis
- Period-over-period comparison
- Actual versus target analysis
- Budget versus actual analysis
- Variance analysis
- Contribution analysis
- Pareto or 80/20 analysis
- Product or service performance
- Customer segmentation
- Customer concentration
- Sales performance
- Regional performance
- Profitability analysis
- Cost-driver analysis
- Operational efficiency
- Capacity or utilisation analysis
- Workforce distribution
- Attrition analysis
- Absenteeism analysis
- Risk concentration
- Outlier detection
- Correlation analysis
- Forecasting
- Scenario analysis


---
# Executive Data Analysis Workflow
## Short, Action-Oriented Prompts for Executives

---

# Stage 1: Understand the Data

## Understand the Workbook

> Act as a Business Data Analyst. Review this workbook and explain what data it contains, the purpose of each worksheet, the key metrics available, and the business questions this data may help answer. Use a simple and executive-friendly tone.

---

## Explain the Worksheets

> Act as an Excel Data Advisor. Review every worksheet and explain its purpose, important fields, key measures, and relationship with other worksheets. Use a clear and concise tone.

---

## Identify Key Business Measures

> Act as a Business Intelligence Advisor. Identify the most important business measures, categories, dates, dimensions, and identifiers available for analysis. Explain them in plain business language. Use a practical tone.

---

## Create a Data Dictionary

> Act as a Business Intelligence Advisor. Create a simple data dictionary explaining the business meaning and possible use of each important field in this workbook. Use an informative tone.

---

## Identify Business Questions

> Act as an Executive Analytics Advisor. Review this workbook and list the business questions the available data can answer. Group them by business function and decision area. Use a strategic tone.

---

# Stage 2: Validate the Data

## Data Quality Review

> Act as a Data Quality Advisor. Review this workbook and identify missing data, duplicate records, inconsistent values, and calculation issues that could affect analysis. Use a practical tone.

---

## Analysis Readiness Check

> Act as an Analytics Readiness Advisor. Assess whether this workbook is ready for meaningful business analysis and identify any important limitations. Use an objective tone.

---

## Identify Missing Information

> Act as a Business Data Advisor. Identify missing fields, measures, targets, or business rules that may limit analysis and recommend additional information required. Use a practical tone.

---

## Sensitive Information Review

> Act as a Responsible AI Advisor. Review the workbook and identify any confidential, personal, financial, or sensitive information that should be handled carefully. Use a professional tone.

---

# Stage 3: Discover Analysis Opportunities

## Identify Possible Analyses

> Act as a Business Analytics Advisor. Identify all meaningful analyses that can be performed using this workbook and provide a one-line explanation for each. Use a business-focused tone.

---

## Categorise the Analyses

> Act as a Decision Support Consultant. Categorise the available analyses into Finance, Sales, Operations, Customers, Workforce, Risk, and Strategic Insights. Use a structured tone.

---

## Rank Analyses by Business Value

> Act as a Senior Business Consultant. Rank the available analyses by business value and explain which analyses are most likely to support executive decision-making. Use a strategic tone.

---

## Identify Quick Wins

> Act as an Executive Analytics Advisor. Identify the analyses that can deliver the quickest business value using the available data and explain why they should be prioritised. Use an action-oriented tone.

---

# Stage 4: Prioritise by Role

## CEO

> Act as a Strategic Advisor. Based on this workbook, recommend the top five analyses most useful for a CEO and explain the business decisions each analysis could support. Use a strategic tone.

---

## CFO

> Act as a Financial Analytics Advisor. Recommend the top five analyses most valuable for a CFO, highlighting financial insights, risks, and decision opportunities. Use a data-driven tone.

---

## COO

> Act as an Operations Advisor. Recommend the top five analyses most relevant to operational performance, efficiency, capacity, risk, and process improvement. Use a practical tone.

---

## CHRO

> Act as a Workforce Analytics Advisor. Recommend the top five analyses that would help a CHRO understand workforce capability, engagement, performance, and people-related risks. Use a professional tone.

---

## Sales Director

> Act as a Sales Strategy Advisor. Recommend the top five analyses that would support revenue growth, customer performance, pipeline management, and sales effectiveness. Use a commercial tone.

---

## Business Unit Head

> Act as a Business Unit Strategy Advisor. Recommend the top five analyses that would help improve growth, cost management, profitability, customer outcomes, and execution. Use a strategic tone.

---

## Regional Manager

> Act as a Regional Performance Advisor. Recommend the top five analyses that would help improve target achievement, customer performance, product mix, and regional growth. Use a results-focused tone.

---

# Stage 5: Select and Challenge the Analysis

## Select One Analysis

> Act as an Executive Decision Advisor. Review the recommended analyses and identify the single analysis most likely to deliver immediate business value. Explain why it should be prioritised. Use a strategic tone.

---

## Compare Top Three Analyses

> Act as an Executive Chief of Staff. Compare the top three recommended analyses and explain the business decision each supports, expected insights, and potential impact. Use a concise executive tone.

---

## Score the Analysis Options

> Act as an Executive Analytics Advisor. Score the recommended analyses based on business value, decision relevance, data readiness, and actionability. Recommend the highest-priority analysis. Use an objective tone.

---

## Check Assumptions

> Act as a Strategy Advisor. Explain what assumptions must be true for this analysis to be useful and identify any data gaps or risks that could affect the findings. Use an analytical tone.

---

## Devil's Advocate Review

> Act as a Devil's Advocate. Challenge the selected analysis and identify blind spots, limitations, alternative interpretations, and stakeholder concerns that leadership should consider. Use a constructive tone.

---

## Decision Readiness Check

> Act as an Executive Decision Advisor. Assess whether this analysis provides enough evidence to support the intended business decision and identify any additional information required. Use a risk-aware tone.

---

## Failure Test

> Act as a Strategic Risk Advisor. Assume this analysis leads to a poor decision. Explain the most likely reasons, warning signs, and preventive actions leadership should consider. Use a critical and forward-looking tone.

---

# Executive Quick Reference

> Understand the Data

> Validate the Data

> Discover Analysis Opportunities

> Prioritise by Role

> Select the Best Analysis

> Challenge Assumptions

> Generate RTCFCT Prompt

> Perform Analysis

> Verify Findings

---
---
---

# Executive Master Meta-Prompt

```text
Act as a Microsoft Copilot prompt expert specialising in executive productivity, business analytics, and responsible AI use.

I am a/an [Profile] working in [Company, Industry, Function, or Business Context].

I have an Excel workbook containing [Brief Description of Worksheets, Fields, Measures, and Time Coverage].

I want to perform [Selected Analysis].

The business objective is [Objective].

The decision to be supported is [Decision].

My audience is [Audience].

The required deliverable is [Deliverable].

Create a professional, detailed, and reusable Microsoft Copilot prompt using the RTCFCT framework.

The generated prompt must contain:

Role:
Assign Copilot the most relevant expert role or combination of roles for the analysis.

Task:
Define the exact analysis, calculations, comparisons, segmentation, trends, risks, opportunities, or recommendations required.

Context:
Include my role, business background, available data, objective, audience, and decision context. Use the workbook's actual field names where they are known.

Output Format:
Design a decision-ready structure appropriate to the analysis. Include only relevant elements from the following: executive summary, scope, metric definitions, methodology, findings, tables, trends, comparisons, drivers, risks, opportunities, recommendations, actions, visual suggestions, and verification notes.

Constraints:
Require Copilot to:
- Use only the supplied workbook and explicitly approved sources.
- Avoid inventing data, fields, dates, targets, benchmarks, causes, or probabilities.
- Define formulas and ranking criteria.
- State filters, periods, exclusions, missing values, and assumptions.
- Separate observed facts, calculations, interpretations, and recommendations.
- identify data-quality limitations and unsupported requests.
- Protect confidential, personal, regulated, and sensitive information.
- Cite supporting worksheets, fields, ranges, or source sections for material findings when possible.
- Recommend human verification for high-impact conclusions.

Tone:
Specify a tone that is professional, executive-level, concise, transparent, objective, and suitable for [Audience]. Add other tone requirements only when necessary.

Use square-bracket placeholders for any missing user inputs. Generate only the final RTCFCT prompt and do not perform the analysis.
```

---

---

# Executive Master Meta-Prompt [Simple Version Example]

Act as a Microsoft Copilot prompt expert.

I am a CFO.

I have a workbook containing sales, cost, product, and regional data.

I want to perform Product Profitability Analysis.

My objective is to identify investment opportunities.

My audience is the CEO and Executive Leadership Team.

Create a detailed RTCFCT prompt.

---