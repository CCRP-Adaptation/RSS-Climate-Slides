# RSS Climate Slides – User Guide

This folder contains everything you need to generate a PowerPoint presentation of climate figures for a park unit using Quarto markdown.

## What this tool does

-   Automatically builds a PowerPoint deck from pre-generated climate figures
-   Organizes slides by climate variable
-   Includes a “Most Common Figures” section at the start
-   Uses a standard PowerPoint template for consistent formatting

⚠️ **Important:**\
This can only be run on climate futures from **CONUS** parks. The folder and file structure for Alaska parks is different and incompatible.

------------------------------------------------------------------------

## Step 1 – Install R and RStudio

> Note: You do **not** need to have previous R experience to run this markdown

💼 If you are on a **federal work computer**:

1.  Launch the Software Center app
2.  Search for and install the latest versions of:
    -   R

    -   RStudio

    -   RTools

💻 If you are on a **personal computer**:

1.  Download RStudio (it is free): <https://posit.co/download/rstudio-desktop/>

2.  Launch the installer

    | During setup it will ask if you want to install R, select yes – you will likely want the 64-bit version

------------------------------------------------------------------------

## Step 2 – Download park climate files

📥 Make sure you have already downloaded the project folder (where this README is located): [Climate Slides Markdown Training](https://doimspp.sharepoint.com/:f:/r/sites/nps-waso-ccrp/Shared%20Documents/01%20PROJECT%20Collaboration/Science,%20Adaptation,%20Planning/Climate%20Futures/Climate_Slides_Automation/Climate%20Slides%20Markdown%20Training). Download the folder itself ('Climate Slides Markdown Training'), not just the files inside – this will be your **project folder**.

1.  Go to: <https://cf-results.s3.us-west-2.amazonaws.com/index.html>
2.  Download the ZIP file for your park (example: `ISRO.zip`)
3.  **Extract** the ZIP file
4.  Place the extracted folder, *unchanged*, in the **same project folder** as the script, so the folder structure looks like this:

```         
README.md                               ← This 'read me' user guide
RSS-Climate-Slides.qmd                  ← The main markdown script
RSS-Climate-Slides-Template.pptx        ← Sets the default PowerPoint format
climate-metric-title.csv                ← Controls slide titles and ordering
ParkCode/                               ← The extracted park folder
└── ParkCode/
    ├── WarmWet_HotDry/
    │   └── figures/
    └── WarmDry_HotWet/
        └── figures/
```

5.  You may delete the ZIP file, if you want

**Important:**\
🚫 Do not delete or rename files or folders.\
🚫 Do not move files into subfolders.

------------------------------------------------------------------------

## Step 3 – Open the script

1.  Find the markdown file in your **project folder**: `RSS-Climate-Slides.qmd`

    | It is important to open it this way because it associates RStudio with the correct working directory (i.e., project folder)

2.  Double click it – this should launch **RStudio**

    | If your computer asks which app to open the file with, select RStudio and check the "Always use this app" option

------------------------------------------------------------------------

## Step 4 – Update user inputs (required)

At the top of the script, you will see a section that looks like this:

```         
params:
  ParkCode: "ISRO"
  LongName: "Isle Royale National Park"
  CF_selected: "WarmWet_HotDry"
```

Change the following:

-   **ParkCode**\
    Change `"ISRO"` to the park you will be running
-   **LongName**\
    Change this to the full park name you are presenting
-   **CF_selected**\
    Choose your CF pair – it must be one or the other, not both\
    `Options: "WarmWet_HotDry" or "WarmDry_HotWet"`

> ℹ️ **Note:**\
> Under the section titled **\# LIBRARIES**, you will see a line of code with the command "install.packages". If this is your first time running the script, either 1) delete the `#` in front of the command and run *just that line* (Ctrl + Enter), then add the `#` back before rendering the PowerPoint, or 2) paste the line without the `#` in the Console and run it there (Enter). If this is not your first time running the script, you can leave the line as is.
>
> 🚫 Do not change anything else in the file.

**SAVE** the file‼️\
If you do not save it, the file will Render with its previous parameters

------------------------------------------------------------------------

## Step 5 – Render the PowerPoint

> ⚠️ It is recommended to have the latest version of Microsoft PowerPoint installed

While in the newly saved `RSS-Climate-Slides.qmd` file:

1.  Click the ➡️**Render** button at the top of the editor

2.  Wait until the process completes

    | ✅ You will know it is done when the Background Job completes and returns you to the Console

A PowerPoint file will be created in your **project folder**. It may also download the PowerPoint file to your browser – this is a duplicate copy, do with it as you please.

### Output

📊 You will get a PowerPoint file named something like: `RSS-Climate-Slides.pptx`

This file is ready to:

-   Present directly *(see Troubleshooting note below about PowerPoint "repairs")*

-   Copy slides into another presentation

    | When pasting the slides, right click and select the "**Keep Source Formatting**" paste option

ℹ️ **Note:\
**The 'Most Common Figures' section is [*copies*]{.underline} of slides found in the sections below

⚠️ **Important:\
**If you click Render again, this PowerPoint file with be overwritten. If you do not want this to happen, either rename the file or move it to a different folder, or do both (recommended).

------------------------------------------------------------------------

## Troubleshooting

### ❌ “Figures folder not found”

-   Make sure the ZIP file was **extracted**
-   Make sure the folder structure was not changed
-   Make sure you **saved** your edits to the markdown file

### ❌ Only one slide is created

-   Make sure the ZIP file was **extracted**
-   Make sure the folder structure was not changed
-   Check that `CF_selected` is spelled correctly and matches the figures folder name exactly
-   Make sure you **saved** your edits to the markdown file

### ❌ Titles look wrong or a figure is missing

-   Check `climate-metric-title.csv` *(see section below)*
    -   Make sure names of figures match the 'file_name' column exactly

### ❌ It is stuck in the Rendering stage with no output

-   Make sure you have the latest version of Microsoft PowerPoint
-   Click on Background Jobs and press the red stop sign 🛑 to cancel the job, then try again
-   Save your files and restart RStudio

### ❌ The rendered PowerPoint says it needs to be "repaired"

-   Make sure you have the latest version of Microsoft PowerPoint
-   There are a myriad of things that can cause this, but the important point is that [*no content was lost*]{.underline} and the file is not corrupted, it is just missing some XML components. My position ended before I was able to find a failsafe for this, so I recommend just clicking Repair each time and copying the slides you need to your park unit presentation slide deck before you make edits or share with someone else.
-   If someone wants to try to fix this, here are some resources to get you started: [Quarto PowerPoint Repair Problem.docx](https://doimspp.sharepoint.com/:w:/r/sites/nps-waso-ccrp/Shared%20Documents/01%20PROJECT%20Collaboration/Science,%20Adaptation,%20Planning/Climate%20Futures/Climate_Slides_Automation/Quarto%20PowerPoint%20Repair%20Problem.docx?d=w17d37deb78d64034a71f89da79bf211b&csf=1&web=1&e=iet6LI)

### What NOT to do

-   🚫 Do not delete or rename files or folders
-   🚫 Do not move files into subfolders
-   🚫 Do not edit code outside the “params” section
-   🚫 Do not delete the CSV or PPT template

------------------------------------------------------------------------

## Need help?

If something doesn’t work:

1.  Take a screenshot of the error
2.  Confirm your folder structure and spelling of things under "params"
3.  Confirm you saved your edits to the markdown file before Rendering
4.  Reach out to the project lead

------------------------------------------------------------------------

## 📝 GitHub Repository

This project was not built for advanced R users, however, a GitHub repository does exist for it. If anybody wants to maintain a global, consistent version of the project, this would be the place to do so.

> <https://github.com/CCRP-Adaptation/RSS-Climate-Slides>

Contact Brecken Robb, [brecken.robb\@gmail.com]{.underline}, to get added to the repository as a collaborator.

------------------------------------------------------------------------

## (Optional) To globally update slide contents

It is recommended to update slide titles and body text within the PowerPoint itself, however, if you want to make a global change to a slide, do so in the `climate-metric-title.csv`.

Open `climate-metric-title.csv` in Excel.

You may edit:

-   `slide_title:` The title of the slide

-   `slide_subheading:` The body text of the slide

-   `common_figure:` If the figure appears in the Most Common Figures section (yes/no)

-   `climate_variable:` The climate variable section the figure falls under

-   `slide_sort:` The order of the figures in the slide deck

    | This also reorders the Most Common Figures section, but these are *copies* of the slides below, so they will not conflict with each other, they will simply follow the same slide structure

🚫 Do not:

-   Rename columns
-   Delete columns
-   Change the file name

**Save** the file when finished.

------------------------------------------------------------------------

## (Optional) To globally update the PowerPoint format

Do not do this unless you have worked with the Slide Master feature before.

1.  Open `RSS-Climate-Slides-Template.pptx`
2.  Go to the **View** tab
3.  Click on **Slide Master**

Make the necessary edits and **save** the file when finished.
