# CST 3510 Memory Analysis Coursework 1 – Rubric Reference (extracted)

Sources: "CST 3510 Memory Analysis Coursework 1 Acquisition Marking Guide" and "CST 3510 Memory Analysis Coursework 1 Analysis Marking Guide" (tutor guides, PDF). This file is a structural extraction for retrieval. The PDF remains the authority. If this file and the PDF differ, the PDF wins and the marker must be told.
Total: 80 marks. Acquisition = 50 (Stages 1–5, 10 each). Analysis = 30 (student answers THREE of five questions, 10 each).

## General principles (both guides)
- Marks go to traceable evidence, successful outcomes and accurate explanation, not to the number of screenshots.
- A command without its output shows an attempt, not successful completion.
- One screenshot may support more than one criterion if it shows separate findings; do not count the same observation twice without additional analysis.
- Technically valid alternative commands, plugins, tools and routes receive equivalent credit where they give defensible evidence.
- A failed later stage must not erase marks earned for correct earlier or independent work.
- Acquisition: half marks (0.5) only where a substantive criterion is genuinely partly achieved. Analysis: 0.5 increments where a substantive criterion is genuinely partly achieved. Do not create half marks merely for granularity.

## Indicative bands – each 10-mark Acquisition stage
0 none/no assessable evidence | 1–2 relevant command attempted, little usable output, stage not completed | 3–4 some correct steps, substantial part missing | 5–6 most of process correct, outcome incomplete/weakly evidenced/not adequately verified | 7–8 completed with clear evidence and sound, if not fully developed, verification/explanation | 9–10 completed accurately and independently, traceable output, purposeful verification, clear explanation, no material overstatement.

## ACQUISITION (50). Every stage = 7 (practical process and output) + 3 (verification and explanation)

### Stage 1 – Prepare the clean VM and required software (10)
Definitive requirements: the Preparation Table supplied with the assessment (NOT in the files provided). Do not add package requirements not listed there.
Practical (7): Correct clean VM, started after assessment begins, usable authenticated session 1 | Package-source configuration (sources.list correct for the supplied OS) 2 | Package-information update (apt update succeeds, no material repository/signature/retrieval errors) 1 | Required package installation (all packages in the Preparation Table, incl. build tools, DWARF utility, headers for running kernel) 3.
Verification/explanation (3): Repository explanation (sources.list defines APT repositories; apt update retrieves package info; absence of material errors supports working configuration) 1 | Kernel identification (uname -r recorded accurately; explains it determines kernel-dependent components) 1 | Preparation explanation (why build packages and matching headers are needed before acquisition and profile building) 1.

### Stage 2 – Acquire the clean memory image using LiME (10)
Practical (7): LiME source obtained 1 | LiME build (correct source directory; sudo make succeeds) 2 | Compiled kernel module (.ko identified and connected to running kernel) 1 | Memory-acquisition command (technically correct sudo insmod, compiled module, valid output path, required LiME format) 3.
Verification/explanation (3): Memory-image evidence (separate check: file exists at intended location, non-empty, plausible size) 1 | Pre-transfer integrity baseline (MD5 of clean image recorded; filename and hash both shown) 1 | Acquisition explanation (LiME module acquires live memory; hash is a baseline for transfer verification; does not independently prove complete capture) 1.

### Stage 3 – Create the Volatility profile (10)
Practical (7): Profile-building source (correct Volatility repository) 1 | Working-directory ownership (sudo chown on Volatility directory) 1 | DWARF data creation (Linux-tools directory; make succeeds; module.dwarf) 2 | Kernel map selection (System.map matching running kernel) 1 | Profile packaging (appropriate zip; correctly named archive containing module.dwarf and matching System.map) 2.
Verification/explanation (3): Profile archive evidence (separate check: ZIP present, non-empty, readable) 1 | Pre-transfer integrity baseline (MD5 of profile ZIP; filename and hash shown) 1 | Profile construction explanation (profile is kernel-specific; why both DWARF data and matching System.map are required) 1.

### Stage 4 – Transfer the dump and profile to the analysis VM (10)
Profile is transferred here but installed into Volatility in Stage 5.
Practical (7, 1 each): VirtualBox preparation (clean VM shut down correctly; permitted shared folder configured; Guest Additions media made available) | Guest Additions media (VM restarted; disk mounted/accessed) | Guest Additions installation (appropriate command; evidence of successful install) | Group permissions (student added to shared-folder group via group config or equivalent) | Shared-folder access (accessible with suitable permissions) | Memory-image transfer (copied via shared folder; available in Kali) | Profile-archive transfer (ZIP copied via shared folder; available in Kali; not yet installed).
Verification/explanation (3): Destination evidence (both files present and accessible in Kali, identifiable filenames and paths) 1 | Post-transfer hash comparison (MD5 of image and ZIP recalculated in Kali; both match the pre-transfer values) 1 | Transfer explanation (matching hashes support byte-for-byte transfer consistency; do not prove the original acquisition or profile construction was complete or correct) 1.

### Stage 5 – Verify the profile against both memory samples (10)
Practical (7): Profile installation (ZIP copied from shared folder to the correct Volatility Linux-profile directory; installed filename and destination shown) 2 | Profile identification (volatility --info or another valid method; exact recognised profile name) 1 | Clean-image command (linux_pslist, identified profile, correct parameters) 1 | Clean-image output (usable process output) 1 | Infected-image command (linux_pslist, same profile, supplied infected sample) 1 | Infected-image output (usable process output) 1.
Verification/explanation (3): Profile-recognition verification (--info output shows Volatility found and loaded the profile, not merely that the ZIP exists) 1 | Compatibility conclusion (successful linux_pslist from both supports compatibility with both) 1 | Limitation (process enumeration shows profile usability and process parsing; does not prove complete acquisition or that any process is malicious) 1.

### Hash rule (Stage 2, 3, 4)
MD5 values for the clean image and profile ZIP are required before transfer and must be recalculated and compared after transfer into Kali. Award hash verification marks only where the hash is clearly associated with the intended file and before/after values are compared accurately.

### Tutor assistance and deductions (Acquisition)
Assistance affects only the specific process or command element helped. None: no deduction. Minor prompt (small syntax/path/parameter issue, no complete solution): deduct only from the affected criterion, usually 1 mark. Substantive guidance (explains missing method or supplies a substantial part of the command): credit independent parts, not the supplied reasoning or command element in full. Direct completion (tutor gives exact solution or performs the step): do not award the assisted process element; still credit later independent outputs, verification and explanation. The assistance record is not in the student's file: the marker must supply it. Do not infer it.

## ANALYSIS (30). Three questions from five, each marked independently out of 10
Model-answer values below are creditworthy evidence; students need not reproduce every finding where the principal investigation is complete, accurate and supported. Recovery marks (successful recovery, recovered content) only where the artefact is actually recovered; credit a valid evidenced attempt under method. Both samples should be examined; presence in the infected image and absence from the clean image does not by itself prove malice. Plugin execution without explanation earns method/identification marks, not interpretation/conclusion marks. Generic definitions earn no separate marks unless tied to the investigation. Reused identical screenshots/explanations across answers do not automatically satisfy different criteria. Material overstatement affects the interpretation/conclusion mark; minor terminology errors get a proportionate deduction. Show understanding to students whose plugins took a long time to process (no numeric rule given; see known issues).

Evidential boundaries students must not conflate: remote port 443 vs confirmed HTTPS | command issued vs proof it succeeded | suspicious vs proven malicious | concealed module vs proof of all its capabilities | local IRC vs external command and control | automated requests vs confirmed successful denial of service | history suppression vs complete erasure | likely file path vs path confirmed by file-system evidence.

Indicative bands per question: 0 none | 1–2 plugin/method attempted, some output, little accurate reporting | 3–4 relevant evidence, at least one accurate finding, basic interpretation | 5–6 competent investigation, mostly accurate, correlation/detail limited | 7–8 strong, principal evidence identified and interpreted, multiple artefacts correlated, supported conclusion | 9–10 complete, accurate, effective evidence selection, precise conclusion, limitations recognised.

### Q1 – Processes and privilege escalation (10)
Process enumeration and comparison (3): clean-sample enumeration (linux_pslist/pstree or equivalent) 1 | infected-sample enumeration 1 | meaningful comparison identifying client or surrounding activity (complete diff not required) 1.
Process ancestry (2): parent relationship bash PID 12306 -> client PID 12315, parent Bash associated with the rootkit user 1 | descendant chain, a substantial part of client 12315 -> sh 12316 -> sh 12317 -> bash 18616 (later wget/sleep children are context only) 1.
Credentials, arguments, environment (2): command line ./client givemerootprivileges recognised as suspicious but not alone proof of escalation 1 | parent context UID 1002/rootkit vs client 12315 and descendants UID 0; environment USER=rootkit, LOGNAME=rootkit, HOME=/home/rootkit, PWD=/vagrant 1.
Corroborating evidence (1): independent corroboration, e.g. fd 3 to /proc/lilyofthevalleyr00tkit, concealed module, Bash history showing compilation/loading, root-owned descendants 1.
Interpretation and conclusion (2): supported interpretation (combined user context, argument, UID change, root descendants, rootkit interface = strong evidence consistent with escalation) 1 | qualified conclusion (no claim of proven infection vector, reboot persistence, every capability, or successful escalation from the argument alone) 1.

### Q2 – Network and IRC activity (10)
Network enumeration and comparison (3): clean-sample network evidence (linux_netstat or equivalent) 1 | infected-sample 1 | meaningful comparison: IRC service/sockets as significant infected finding vs clean baseline (normal SSH/DHCP/DNS/local activity may vary) 1.
IRC service and listening sockets (2): ircd-hybrid PID 10114 1 | listeners on 0.0.0.0 ports 6665–6669; explains 0.0.0.0 = available IPv4 interfaces, listening = ready to accept connections 1.
Client-side process evidence (2): established 127.0.0.1:33842 <-> 127.0.0.1:6667, explained as local loopback communication 1 | IRC client command bash irc-bash -h localhost -p 6667 -n testMachine2 tied to client processes incl. PIDs 18298 or 18299 1.
Correlation and interpretation (2): client/server correlation (ircd-hybrid, Bash client, port 6667, loopback endpoints) 1 | supported interpretation (IRC server on infected system; local Bash IRC client via localhost, port 6667, nickname testMachine2) 1.
Evidential limitation (1): recognises evidence does not by itself establish external IRC connection, remote C2, communication with an external attacker, or malicious message content 1.

### Q3 – Kernel modules and rootkits (10)
Visible-module comparison (1): linux_lsmod or equivalent on both samples with meaningful comparison; 0.5 if only one sample 1.
Hidden-module detection and interpretation (3): hidden-module method (linux_hidden_modules or valid equivalent) on infected sample 1 | identifies lilyofthevalley at 0xffffffffa03cc140 1 | concealment interpretation (hidden-module detection plus absence from visible enumeration supports concealment) 1.
Module recovery (2): recovery method (module address with suitable linux_moddump and valid output directory; a substantially correct command may earn this even if extraction fails) 1 | successful recovery (module file actually produced) 1.
Examination of recovered module (2): structural examination (file/readelf/strings/xxd; accurate result e.g. ELF kernel module) 1 | functional interpretation (verified content in the recovered module, e.g. command strings, paths, symbols, control-interface references; credit only demonstrated content) 1.
Runtime corroboration and conclusion (2): at least one significant independent artefact (Bash history compile/insmod, /proc/lilyofthevalleyr00tkit, client holding the /proc entry, ./client givemerootprivileges, transition to UID 0) 1 | supported and qualified conclusion (concealed module with user-space interface and apparent privilege-related function; no claim of proven infection vector, reboot persistence, syscall-table hooking or every capability) 1.

### Q4 – File recovery and script behaviour (10)
Process identification and ancestry (2): bash PID 18616 running bash script.bash 1 | substantial part of client 12315 -> sh 12316 -> sh 12317 -> bash 18616 (wget/sleep children may be shown) 1.
Executing file and path (2): linux_lsof or equivalent shows /home/rootkit/script.bash for PID 18616, fd 255 1 | distinguishes executing path /home/rootkit/script.bash from history entry nano /vagrant/script.bash (editing/staging; not proof the files are identical) 1.
File recovery (2): file location (linux_find_file or equivalent; file address or inode obtained) 1 | successful extraction (script recovered; evidence of file or content; equivalent methods equal) 1.
Script behaviour (3): loop and effect of repetition 1 | wget activity (repeated requests to destinations such as Facebook, Ubuntu, Debian, Twitter; 0.5 if destinations listed without explaining the activity) 1 | delay (sleep 1 spaces iterations) 1.
Corroborated conclusion (1): runtime evidence (34 wget children, grouped start times, linux_psaux command lines, DNS activity, port 80/443 sockets, sleep child); concludes repeated automated web requests consistent with traffic-generation or DoS-like activity, without claiming confirmed disruption, distributed activity, or HTTPS from port 443 alone 1.

### Q5 – User activity and anti-forensics (10)
User process and file identification (2): secrets user, UID 1003, emacs PID 18612 (every value not required if clearly attributed) 1 | filename secretFile.txr from command-line evidence (mark against the filename confirmed in the assessment image; credit an accurate value in student evidence) 1.
User and session context (2): USER=secrets, LOGNAME=secrets, HOME=/home/secrets, PWD=/home/secrets, OLDPWD=/vagrant; likely path distinguished from path confirmed via file-system evidence 1 | SSH_CLIENT, SSH_TTY, SSH_CONNECTION, _=/usr/bin/emacs interpreted: editor started in an SSH session, inherited launching shell environment 1.
History-suppression evidence (2): HISTSIZE=0 and HISTFILE=/dev/null 1 | interpretation (consistent with suppressing Bash-history retention; Emacs inherited rather than created them; not proof of complete deletion as other evidence remains) 1.
File location and recovery (2): location or valid recovery attempt (linux_find_file, linux_enumerate_files, linux_recover_filesystem or other; plausible path e.g. /home/secrets/secretFile.txr) 1 | successful recovery (returned address/inode used; extracted output shown; if extraction fails, still award independent process/environment marks) 1.
Recovered content (1): accurately reports and interprets recovered content; a password only where actually present in the extracted file; no credit for invented content 1.
Conclusion and limitation (1): connects user, editor, filename, path, recovery result and history settings; separates confirmed evidence from inference; states material recovery limitation 1.

### Boundaries between questions
Same evidence may be credited in more than one answer only where it makes a distinct analytical contribution. Q1 principal focus: privilege escalation (script/web-request detail secondary). Q2: local IRC (wget detail secondary). Q3: concealed module detection, recovery, purpose (full script reconstruction secondary). Q4: script.bash recovery and behaviour (full privilege-transition investigation secondary). Q5: secrets user, edited file, history suppression (kernel-module/IRC analysis secondary).

## Known issues to flag to the human marker (not resolved by the agent)
1. The Stage 1 Preparation Table is the definitive requirement list but was not supplied. Without it, "Required package installation" (3 marks) cannot be fully verified. Ask the marker for it.
2. The guides say students answer three of five questions but do not say what to do if more than three are answered (first three? best three?). Do not choose; ask the marker.
3. No pass mark, grade boundaries, rounding rule, late penalty or percentage conversion is stated. Do not apply any. Report x/80.
4. Tutor assistance records are not in the student submission. Substantive guidance has no stated numeric deduction ("credit independent parts"): flag the marker's decision. Minor prompt is "usually 1 mark".
5. "Show understanding to students whose plugins took a long time to process" has no numeric rule. Do not adjust marks; note it for the marker.
6. The clean sample is created during the assessment and varies. Do not expect clean-image values to match the model answer; mark the comparison, not specific clean-image values.
7. Model-answer PIDs, addresses and filenames (e.g. 12315, 10114, 0xffffffffa03cc140, secretFile.txr) relate to the supplied infected sample. Mark against the evidence the student shows; for secretFile.txr the guide says to mark against the filename confirmed in the assessment image.
8. No marksheet (Excel) for CST 3510 was supplied; the marksheet mapping is therefore undefined.
