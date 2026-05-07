## **MSI Elective Explorer**

## **Current Version Built By:** Lena Choi, MSI Peer Advisor 2025-2026
**Last Updated:** May 2026

**Contact:** lenachoi@umich.edu // choi.lena98@gmail.com

## **Purpose**
The MSI Elective Explorer is an interactive website that helps MSI students figure out what electives to take. Instead of guessing or asking around, students can see real data on what their peers from previous years actually chose — broken down by their pathway.
It was built using five years of graduating cohort data (2022–2026) and lives at a shareable link.

**Students can use it to:**
- See the most popular electives for their specific pathway (BDA, UX, UCAD, or LAKES)
- Browse courses taken across all pathways
- Discover what students took outside of UMSI
- Read peer advisor tips written specifically for each track

## **Where to Find Everything**
This folder (also known as a "repository") contains all the files that make the tool work:
- ``` msi-elective-explorer.html``` = Actual Tool/Website
- ``` README.md``` = This Document
- ```msi_electives_2022.ipynb``` - ```msi_electives_2026.ipynb``` = Data Analysis Files for Each Graduating Year
- ```csv files``` = Raw Student Enrollment Data from the Registrar

*Note: There is no need to open or understand most of these files. The only file that will need to be edited is msi-elective-explorer.html, and this README provides a walkthrough of exactly how to do that.*

## **How to Access the Live Tool**
The tool is hosted at a public link through a free service called Netlify. Anyone with the link can open it in a browser — no login required.
- *To Share:* Copy + Paste the Netlify Link
- *To Update:* Follow the steps in the "Updating the Tool" section below.

## **Updating the Tool Each Year**
When a new cohort graduates, the tool should be updated to include their data. Here is the full process, step by step. No coding experience required.
### **STEP 1:** Retrieve New Data File from the Registrar
Request the graduating cohort's course enrollment data from the registrar office. If in an Excel format, convert to csv file. It should look similar to the files already in this folder. Make sure the file has these columns:
- Student ID (UM 8 digit #)
- Declared Pathway (e.g. "Big Data Analytics MSI")
- Course Subject (e.g. "SI")
- Course Number (e.g. "564")
### **STEP 2:** Open the Live Tool and go to the Admin Panel
1. Open the tool link in your browser
2. Click ⚙ Admin in the navigation at the top
3. A password prompt will appear — enter the admin password
    *Note:* The admin password is kept separate for security. Ask your supervisor or the previous peer advisor for it.
4. The Admin Panel will open
### **STEP 3:** Upload the New CSV File
1. In the Admin Panel, find the section that says **Upload New Cohort**
2. Click the upload box and select the CSV file you got from the registrar
3. The tool will automatically read the file and update the course list
4. You will see a summary of what changed — new courses added, existing courses updated
### **STEP 4:** Fix Any Course Name Abbreviations, if applicable
The registrar data sometimes uses shortened course names that aren't student-friendly or consistent with Atlas. Cross-reference course names with Atlas or the UMSI Course Guide
1. Scroll down in the Admin Panel to the Edit Course Names section
2. Search for any course that looks abbreviated or unclear
3. Click Edit next to it, type the full correct name, and press Enter
4. Repeat for any other names that need fixing
### **STEP 5:** Save Changes
1. Click the button that says Copy updated allCourses array
    A pop-up will confirm that it was copied to your clipboard
2. Open the file called msi-elective-explorer.html in a text editor
    On a Mac, you can use TextEdit. On Windows, use Notepad. Or use VS Code if you have it.
3. Use Edit → Find (or Cmd+F / Ctrl+F) to search for: ```const allCourses = [```
4. Select everything from that line all the way down to the line that just says ```];```
5. Delete the selected text
6. Paste what you copied in Step 1
7. Save the file
### **STEP 6:** Upload the Updated File to GitHub
GitHub is where all the files are stored. Uploading here keeps everything backed up and automatically updates the live tool.
1. Open your terminal (on Mac, search "Terminal" in Spotlight)
2. Type these commands one at a time, pressing Enter after each:
    ```git add .```
    ```git commit -m "Updated for 2027 cohort"```
    ```git push origin main```
The live tool will update automatically within a minute or two. No other steps needed.

## **Admin Password**
The admin password is not written in this document for security reasons. It is stored in the HTML file itself — but only someone who opens the file in a text editor would be able to find it.
**To Get the Password:** Contact an Academic Advisor (Allie Prough or Natalie Drobny) or the peer advisor who last updated the tool.
**To Change the Password:**
1. Open ```msi-elective-explorer.html``` in a text editor
2. Use Find (Cmd+F / Ctrl+F) to search for the current password
3. Replace it with the new one
4. Save the file and push to GitHub (see Step 6 above)

## **How the Data Works**
The tool shows what electives MSI students took, organized by their pathway. Here's how that data was put together:
**For the 2025 and 2026 cohorts** (and all future cohorts), each student's pathway comes directly from the registrar — it's the pathway they officially declared. This is straightforward and reliable.
**For the 2022–2024 cohorts**, pathway data wasn't available from the registrar, so it was inferred from which required courses each student took. For example, a student who took a lot of BDA-required courses was assigned to BDA. This process is documented in the Jupyter notebook files if anyone wants to understand it in more detail.
In all cases, the following were excluded from the elective analysis:
- Core required courses that every MSI student takes
- Internship credits
- Thesis and capstone courses
- Students in the MTOP program (separate track)

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
5. **Update the CSV Upload Logic:** This way, the Admin Panel can recognize the new pathway name when uploading a registrar file. Check the registrar CSV's pathway column for the exact wording.
6. **Add Required Courses to Exclude:** List all required courses for the new pathway so they're excluded from the elective analysis
    - The HTML file has comments marked with ```// TO ADD A NEW TRACK``` at each location that needs to be changed. Search for that phrase in the file to find them quickly.

### **Frequently Asked Questions**
- **Do I need to know how to code to update this?**

    No. The Admin Panel handles the technical parts. The only manual step is copying and pasting, which this README walks you through.

- **What if the CSV file from the registrar looks different from past years?**

    The tool expects certain column names. If something looks off, reach out to whoever built or last updated the tool — they can adjust the code to handle the new format.

- **What if I accidentally break something?**

    Don't worry — GitHub keeps a history of every version of the file. You can always go back to a previous version by clicking on the file in GitHub, then clicking History.

- **Can students access the Admin Panel?**

    Only if they have the password, which isn't shared publicly. The Admin tab is visible in the nav bar but password-protected.

- **How often should the tool be updated?**

    Ideally once per year, after the new cohort graduates (typically after Winter term ends).

### **Questions or Issues?**
Contact the UMSI Academic Advising office or the peer advisor who last updated this tool.