# Course audit and fix log

November 22, 2026 · Local working copy of `version_2`

Reviewed the 72 tracked course notebooks and the 72 public course pages, including the landing page. Followed rendered course links and images, checked URLs in notebook source, and proofread prompts and lesson text. [Published course](https://ahaberlie.github.io/python_programming_geosciences/)

## Links, images, and downloads

| Area | Finding and update |
| --- | --- |
| Course index and cross-references | The **4.2 Imports** entry led to **4.1 Classes**. It now points to the importing notebook. Course cross-references use relative notebook paths so MyST can resolve them in a local build. Added index links for Chapter 9.6 and Labs 13–15, with lab names drawn from the notebooks. Identified listed topics and assignments that lack a linked notebook. |
| Figures | The published site requested `build/undefined` for images on 13 pages. Restored the affected illustrations from their original sources and recovered six course images from the existing MyST cache whose Nimbus source URLs returned 404. The recovered assets now use repository-relative paths. Added alternate text and source, author, and license credits for the Wikimedia and NOAA figures where available. |
| Exercises and homework images | EX1 showed an unavailable copy of the Huskies logo. The prompt now gives editable image syntax, and the key links to a working official team logo. The thunderstorm photo is packaged with the course. HW4 now provides labeled places to add three source images, replacing the repeated university-logo placeholders. |
| Reading links | Linked the NIU computer science program to its department page. Updated GridRad references to the NCAR archive, corrected the truncated Parker and Johnson citation link in Lab 13, and linked to author- or university-hosted copies of the assigned articles. [GridRad archive](https://gdex.ucar.edu/datasets/d841000/) · [Parker publications](https://sites.google.com/ncsu.edu/mdparker/publications) |
| Radar examples | The original May 8, 2009 reflectivity PNG returned 404 on Nimbus. Chapters 8.1 and 9.1–9.3 and Lab 10 now retrieve the same named PNG from the instructor's Unidata workshop. Confirmed that its 3,661 × 1,837 dimensions and pixel values support the existing 400 × 400 crop. [Radar source](https://github.com/ahaberlie/unidata-workshop-2018/blob/master/workshop/data/radar_data/BREF_090508_1300.png) |
| Aerial imagery | The two Nimbus TIFF URLs returned 404. Chapter 9.1 uses a 256 × 256 USGS NAIP extract at the original coordinates. Labs 9 and 10 use a 1,024 × 1,024 Mount Rainier extract with forest and snow. Updated Lab 9's starter crop and refreshed the saved source-image previews. The new extracts can produce different pixel values. [USGS NAIP image service](https://imagery.nationalmap.gov/arcgis/rest/services/USGSNAIPImagery/ImageServer) |
| Lab 4 PRISM data | Changed the monthly precipitation normals download host to the PRISM archive. Verified that the January ZIP opens and contains the expected TIFF. [Monthly archive](https://ftp.prism.oregonstate.edu/normals/us/4km/ppt/monthly/) |
| Exam 1 | The original `exam1.csv` URL returned 404. The instructor's related public workshop data matched the notebook's ten displayed rows by value, but the original order could not be reproduced. The exam assigns seeded years in row order, so its setup now tells students to use the original instructor-provided CSV and reports a missing file. |

## Wording and correctness

- Fixed spelling, capitalization, Markdown formatting, and Python terminology across lessons and labs. Clarified how notebook cells and the kernel execute code, distinguished pandas attributes from methods, and aligned the tornado dataset year range with the bundled CSV.
- Clarified how random forests sample rows, choose candidate features at each split, and combine class probabilities in scikit-learn. Corrected the RGB raster dimensions and distinguished run-length encoding from the compression used by PNG. [RandomForestClassifier reference](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html)
- **EX1–EX9** now give clearer directions on Markdown, expression output, Boolean operands, dictionary keys, loop boundaries, function parameters, and units. EX7 now specifies that CAPE categories use the original value and the displayed number uses `int(CAPE)`. EX8 defines the supported conversion pairs for all three units and closes the unbalanced Markdown fence.
- **EX10–EX14** now distinguish filtering from grouping, describe EX10 Problem 7 as a sample standard deviation, specify `__str__` behavior for EX12, and align EX13's row and column numbers with its grader. Fixed the EX13 and EX14 submission filenames and added the missing Matplotlib import in EX14.
- **HW1–HW3** now direct students to run dependent cells from top to bottom. Corrected the Kelvin symbols in the humidity equations, clarified what qualifies a calendar month in HW2, and reconciled HW3's required helpers with the supplied tests and variable names.
- **HW4–HW5** now specify direct image URLs and source credits for plots, use the repository's actual tornado CSV name, and clarify season names, time windows, units, and table requirements. The HW5 grader checks every magnitude 0–5 in the two table answers before awarding credit. EX10, EX11, and HW5 can locate a bundled CSV or download it from GitHub using Python. Added pandas to the course requirements.

## Answer keys

Created a worked notebook for each of [Homework 1–5 and Exercise 1–14](answer_keys/answer-keys.md). The keys include sample Markdown responses, code for each computational task, and 13 generated plots across the plotting assignments. The Jupyter Book sidebar now includes an **Answer Keys** section with an overview and separate homework and exercise groups. The notebooks are available for Git tracking and are included in the website build.

## Verification and limits

- Built the local HTML with the GitHub Pages base path and checked all generated course pages for internal link targets, fragments, and image files.
- Validated all 19 answer notebooks and ran their 150 Python cells. EX10, EX11, and EX13 each scored 5/5, and HW5 scored 10/10. Checked all four of HW1's published cases and the seasonal and time-of-day totals in HW5.
- Confirmed the replacement radar PNG, both NAIP GeoTIFFs, and the January PRISM archive. Some external sites rate-limited or blocked automated requests. Exam 1 still requires its original CSV. Advanced labs and chapters were checked for links and assets rather than executed end to end.
- All changes and verification outputs were created locally.

## Preview deployment follow-up

- The preview deployment reached the HTML renderer. Its Node.js 18 runtime rejected the renderer's `--env-file` flag. Updated the Pages workflow to Node.js 24 and verified a 72-page local HTML build with the preview repository's base path. [Node.js CLI reference](https://nodejs.org/api/cli.html#--env-fileconfig)
- Fixed the blank netCDF link in Lab 4 and the empty AWS link text in Chapter 3.3, both flagged in the preview build log.
