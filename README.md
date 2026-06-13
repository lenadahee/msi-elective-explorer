## **MSI Elective Explorer**
*Live Tool:* [MSI Elective Explorer](https://msi-elective-explorer.netlify.app)

## **Current Version Built By:** 
Lena Choi, MSI Peer Advisor 2025-2026
**Last Updated:** June 2026

**Contact:** lenachoi@umich.edu // choi.lena98@gmail.com

## **Purpose**
The MSI Elective Explorer is an interactive website that helps MSI students figure out what electives to take. Instead of guessing or asking around, students can see real data on what their peers from previous years actually chose — broken down by their pathway.
It was built using five years of graduating cohort data (2022–2026) and lives at a shareable link. No login required.

**Students can use it to:**
- See the most popular electives for their specific pathway (BDA, UX, UCAD, or LAKES)
- Browse courses taken across all pathways
- Discover what students took outside of UMSI
- Read peer advisor tips written specifically for each track

## **Where to Find Everything**
This folder (also known as a "repository") contains all the files that make the tool work:
- ``` index.html``` = Actual Tool/Website (Only tool that needs to be edited)
- ``` README.md``` = This Document
- ```msi_electives_2022.ipynb``` - ```msi_electives_2026.ipynb``` = Data Analysis Files for Each Graduating Year
- ```csv files``` = Raw Student Enrollment Data from the Registrar

*Note: There is no need to open or understand most of these files. The only file that will need to be edited is index.html, and this README provides a walkthrough of exactly how to do that. Everything else is for reference or future data analysis.*

## **How to Access the Live Tool**
The tool is hosted at a public link through a free service called Netlify. Anyone with the link can open it in a browser — no login required.
- *To Share:* Copy + Paste the Netlify Link
- *To Update:* Follow the steps in the "Updating the Tool" section below.

## **Updating the Tool Each Year**
When a new cohort graduates, the tool should be updated to include their data. Here is the full process, step by step. No coding experience required.
*NOTE:* This process is two-fold: (1) Run the data analysis & (2) Update the website

*When To Do This:* Ideally, once per year, after the Winter term graduating cohort data is available from the Registrar (most likely May or June)

### **PART 1: ANALYZE THE NEW COHORT'S DATA**
#### **STEP 1:** Retrieve New Data File from the Registrar
Request the graduating cohort's course enrollment data from the registrar office. If in an Excel format, convert to csv file. It should look similar to the files already in this folder. Make sure the file has these columns:
- Student ID (UM 8 digit #)
- Declared Pathway (e.g. "Big Data Analytics MSI")
- Course Subject (e.g. "SI")
- Course Number (e.g. "564")
Save the file into this repository folder and name it following the same pattern as the existing files (e.g. 'Emplid_And_Crse2027.csv').
#### **STEP 2:** Run the Data Analysis Notebook
Each year has its own Jupyter notebook (e.g. msi_electives_2026.ipynb). To add a new year:
1. Make a copy of the most recent notebook (e.g. duplicate msi_electives_2026.ipynb)
2. Rename it to match the new year (e.g. msi_electives_2027.ipynb)
3. Open it in VS Code or Jupyter Notebook
4. At the top of the notebook, update the file name to point to the new CSV file
5. Run all cells (in VS Code: click ```Run All`` at the top)
6. The output will show the top electives and percentages for each pathway — write these down or take a screenshot, you'll need them in Part 2
*Note:* If you're not comfortable running the notebook yourself, share the CSV file with whoever is maintaining the technical side and ask them to run it and give you the output numbers.

### **PART 2:** Update the Website
This part takes the numbers from Part 1 and puts them into the website
#### **STEP 3:** Open the File in VS Code
1. Open VS Code
2. Open the project folder (File → Open Folder → select the repository folder)
3. Click on index.html in the left sidebar
### **STEP 4:** Find the Section to Update
In VS Code, press Cmd+F (Mac) or Ctrl+F (Windows) to open the search bar. Search for:
```const tracks = {```
This is where all the pathway data lives — the percentages, descriptions, and peer advisor tips for BDA, UX, UCAD, and LAKES.
#### **STEP 5:** Update the Numbers and Text
Each pathway block looks like this:
```
bda: {
  title: 'Big Data Analytics',
  highlight: '...one key stat or insight...',
  desc: '...one or two sentence description...',
  tip: '...peer advisor tip...',
  electives: [
    { name: 'SI 564 — SQL & Databases', pct: 69 },
    ...
  ],
  outside: ['ENTR 500 — Intro to Innovation', ...]
},
```
For each pathway, update:
- **pct** — the percentage from the new notebook output (just the number, no % sign)
- **highlight** — update the stat if it has changed
- **tip** — update if the advice has changed based on new trends
- **electives** — reorder or swap courses if the top picks have changed

*Tip:* Only change what has actually shifted. If a course has been in the top picks for several years, it's fine to leave it as-is.
#### **STEP 6:** Update the Footer Date
Search for ```Last updated:``` and change the month and year to today's date.
#### **STEP 7:** Save the File
Press Cmd+S (Mac) or Ctrl+S (Windows).
#### **STEP 8:** Commit and push to GitHub
Open Terminal (on Mac: search "Terminal" in Spotlight. On Windows: search "Command Prompt"). Type these three commands one at a time, pressing Enter after each:
```
git add index.html
git commit -m "Update elective data for 2027 cohort"
git push origin main
```
The live tool will update automatically within a minute or two. You can refresh the Netlify link to confirm.

## **How the Data Works**
The tool shows what electives MSI students took, organized by their declared pathway.
**For the 2025 and 2026 cohorts** (and all future cohorts), each student's pathway comes directly from the Registrar — it's the pathway they officially declared.
**For the 2022–2024 cohorts**, pathway data wasn't available from the Registrar, so it was inferred from which required courses each student took. This process is documented in the Jupyter notebooks.
In all cases, the following were excluded from the elective analysis:
- Core required courses that every MSI student takes
- Select requirements (courses students had to choose from a list)
- Internship credits
- Thesis and capstone courses
- Students in the MTOP program (separate track)

Percentages represent the share of students in a given pathway who took that course in a given year. The tool shows averages across all available cohorts.

## **Adding a New Pathway**
If (and when) UMSI ever introduces a new MSI pathway, the tool will need to be updated. This requires someone with basic web development experience to edit the HTML file in a few places.

### **What Needs to Change**
1. **Choose a color for the new track.** Each pathway has its own color — blue for BDA, green for UX, purple for UCAD, and coral for LAKES. You will need to pick a new color for the new pathway.
You will need three versions of your chosen color:
- A light version for backgrounds (very pale)
- A mid version for borders and bars (the main color)
- A dark version for text (deep/saturated)
*Note: A good free tool for this is coolors.co — pick a color and it will generate light, mid, and dark versions automatically. Once you have your three color codes (they look like #378ADD), share them with whoever is making the code changes.*
2. **Add the Pathway Button:** A new clickable button needs to be added to the pathway selector
3. **Add a Filter Button:** A new filter needs to be added to the All Courses tab
4. **Add the Pathway Data:**  Fill in the title, highlight stat, description, peer advisor tip, top electives with percentages, and popular outside UMSI courses
5. **Add Required Courses to Exclude:** List all required courses for the new pathway so they're excluded from the elective analysis
    - The HTML file has comments marked with ```// TO ADD A NEW TRACK``` at each location that needs to be changed. Search for that phrase in the file to find them quickly.

### **Frequently Asked Questions**
- **What if the CSV file from the registrar looks different from past years?**

    The tool expects certain column names. If something looks off, reach out to whoever built or last updated the tool — they can adjust the code to handle the new format.

- **What if I accidentally break something?**

    Don't worry — GitHub keeps a history of every version of the file. You can always go back to a previous version by clicking on the file in GitHub, then clicking History.

- **What if I don't have Git set up on my computer?**

    You can edit and upload the file directly on github.com without any terminal. Navigate to index.html in the repository → click the pencil (Edit) icon → make your changes → click Commit changes. Netlify will update automatically.

- **How often should the tool be updated?**

    Ideally once per year, after the new cohort graduates (typically after Winter term ends).

### **Questions or Issues?**
Contact the UMSI Academic Advising office or the peer advisor who last updated this tool.