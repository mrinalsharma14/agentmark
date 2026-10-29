# 2580 Coursework 1 Lab Test – Rubric Reference (extracted)

Source: "2580 Coursework 1 Lab Test Marking Guide" (PDF). This file is a faithful structural extraction for retrieval. The PDF remains the authority. If this file and the PDF differ, the PDF wins and the marker must be told.
Total: 80 marks. Acquisition subtotal (A1–A4) = 45. Analysis subtotal (B1–B4) = 35.

## A1 – Acquisition Form (10)
Consider: all fields completed; information accurate and valid; legible; no errors or overwriting; student number (not name) in "Collected By" and similar fields.
Deductions stated in the guide:
- Case/Evidence number given must match the required values, otherwise -1.
- Student has given their name: -2.
- Additional device information should include at least colour/markings (bottom info section only needs "n/a"): otherwise -1.
- Form completed in lower-case characters: -1.
- Watch for false values (e.g. capacity given in bytes). Address given as a location should be full.
- Go easy on errors in hash values; one overwritten value carries no penalty.

## A2 – Standard Operating Procedure (20)
Open to interpretation; be flexible on style. Higher marks need more than the process steps: Title, Purpose, Date, Author, Approver, Relevant standards (specific ISO standards or ACPO principles score higher), competence level. Image parameters (step 6) expected. Order matters: small penalty for steps out of order. 18 fields/steps are a guide, not a mark-per-item scheme. Full marks: all steps and fields present and detailed.
Expected main steps: 1 start acquisition form (general info, location); 2 connect write blocker to host and power on; 3 check lights, write-block indicator active; 4 insert USB, verify connected and write blocking still active; 5 use write blocker to get device information into form; 6 FTK Imager: (a) create disk image (b) physical drive (c) raw (dd) (d) case/evidence info (e) fragment size = 0 (f) verify images option selected; 7 check results; 8 open image summary file; 9 verify hashes match and "verified" present; 10 complete acquisition form with imaging details; 11 unplug evidence and power down.

## A3 – Image Verification (8)
- 1 working image (did not request one from tutor for Analysis stage)
- 1 screenshot of image summary
- 1 explains the hashes match
- up to 2 explains in detail how hashes are calculated (computed hash = source evidence; image hash = image)
- 2 case details on image summary match the acquisition form
- 1 marked-up screenshot to assist explanation

## A4 – Imaging Question (7)
- 1 definition of an image (duplicate, bit-for-bit copy etc.)
- 1 uses the term evidential integrity / integrity of evidence
- 2 how well evidential integrity is explained
- 1 relevant ACPO principle or ISO standard
- 2 explains how integrity is achieved

## B1 – Master Boot Record (6)
Two parts (a) partition size in bytes (3) and (b) byte offset to first partition (3). Each part: 1 calculations, 1 correct answer, 1 verification.
(a) steps: bytes 12–15, reverse endian, decimal, answer x bytes per sector. (b) same method with bytes 8–11.
If mmls not used to verify, maximum is 4/6.

## B2 – Volume Boot Record (15)
Five parts, 3 marks each: (a) bytes per sector (b) sectors per cluster (c) reserved sectors (d) number of FATs (e) sectors per FAT.
Each part: 1 calculations, 1 correct answer, 1 verification with fsstat. Answers should be clearly stated with units (sectors, bytes) and 0x prefix on hex values.
- fsstat used only generally: maximum 2 marks for using it across the section (not the available 5). Each value must be verified uniquely for full marks.
- FTK Imager verification of some values: 1 mark available (not if used only to obtain the answer).
- If fsstat not used to verify, each part is worth only 2 marks. FTK Imager does not earn the same credit as Sleuth Kit tools.

## B3 – Root Directory (8)
(a) (4) locate root directory and give offset: 1 values entered in diagram or clearly written (Reserved + FAT1 + FAT2 = start of RD); 1 mapping out sector values; 1 correct offset address; 1 full calculations; plus 1 for verification (hex screenshot of RD or fsstat sector addresses). Note: the guide lists the verification mark in addition to the items above; marker to confirm that (a) totals 4.
(b) (4) identify a file in root directory: (i) size (ii) filename (iii) starting cluster. 1 mark each (1/2 calculation + 1/2 answer) plus 1 additional mark for verifying with istat.

## B4 – File Extraction (6) – ONE method only
No marks for completing two methods (e.g. FTK + istat does not gain 6; only the marks for the best-completed single method).
- FTK Imager (max 2): explain process (right-click file, Export Files) 1; verify 1.
- icat (max 4): correct inode from fls 1; correct redirect operator > 1; command executed successfully with screenshot 1; verify 1. Command form: icat -o [offset] [image] [inode] > [output].
- dd (max 6): apply starting-cluster formula (Starting cluster - 2) x sectors per cluster + sector no. of cluster 2 = 2 marks; convert to byte address using BPS and add offset 1; correct command 2 (dd bs=1 skip=[byte offset] count=[file size] if=[image] of=[file]); verify 1. Sector-based dd (includes slack) = one mark less than the correct byte-based command.

## Known issues to flag to the human marker (not resolved by the agent)
1. B3(a) sub-items listed in the guide add up to 5 against a stated 4.
2. Guide states Case Number MDX00025 and a 50-minute write-blocker window; the student submission sheet shows MDX00026 and 20 minutes. Confirm the cohort's correct values before applying the A1 case-number deduction.
3. The Excel marksheet's percentage columns appear to divide by 75, not 80 (e.g. 40 marks shows 53.3%, which is 40/75; 40/80 = 50.0%). Do not compute percentages; report raw marks /80 and flag.
4. No pass mark, grade boundaries, rounding rule or late penalty is stated in the supplied guide. Do not apply any.
