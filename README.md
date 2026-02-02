Case Study — Icarus  
This repository documents a security case study focused on client-side trust and server-side validation issues found in the game Icarus.

## Overview
- **Project:** Icarus  
- **Category:** Game with persistent progression  
- **Analysis type:** Independent technical analysis  
- **Role:** Identification and evaluation of a data validation vulnerability  

This case study documents the identification of an architectural flaw related to client-side validation of sensitive game data, with direct impact on data integrity and progression reliability.

## Context
During an exploratory analysis of the game’s local files, it was observed that critical player progression data was stored locally in `.json` format.
These files were located within the system’s temporary directory and were used by the game during session loading as a source of progression data.

## Technical Findings
The analysis revealed that:
- Sensitive progression data was stored locally on the client
- The data was readable and editable (`.json` format)
- There was no evidence of:
  - encryption
  - integrity validation
  - consistent server-side verification

The game accepted the values present in these files as valid without additional server-side validation.

## Proof of Concept (PoC)
Without the use of external tools or invasive techniques, it was possible to:
- Manually edit the local `.json` files using a basic text editor
- Modify values related to the in-game economy (multiple currency types)
- Alter achievement and progression states

The game accepted these changes without rollback, blocking, or server-side rejection.
> This case study intentionally avoids step-by-step instructions, following responsible disclosure practices. <

## Potential Impact
This type of vulnerability can lead to:
- Compromised in-game economy
- Illegitimate player progression
- Invalid rankings and achievements
- Reduced system credibility
- Risk of large-scale exploitation

From a system architecture perspective:
> Any critical data controlled by the client must be considered untrusted. <

## Responsible Disclosure
After confirming the issue, a technical and responsible communication was sent to the company responsible for the game, describing the vulnerability and its potential impact.
> No response or follow-up was received! <

## Mitigation Recommendations
Possible approaches to mitigate this vulnerability include:
- Server-side validation as the single source of truth
- Treat all client-side data as untrusted input
- Integrity checks for progression-related data
- Detection of inconsistent state between client and server

## Key Learnings
This case reinforced important concepts related to:
- Client-server architecture
- Data integrity and validation
- Security risks of local data storage
- Server-side trust boundaries
- Responsible technical communication

## Final Notes
This case study demonstrates an analytical and ethical approach to identifying architectural weaknesses, with a focus on system improvement rather than exploitation.

## Ethical and Legal Considerations
This case study is provided strictly for educational and analytical purposes.
No automation tools, exploitation scripts, or step-by-step instructions are included.  
The goal of this repository is to discuss architectural and validation risks, not to enable misuse.

## Author
> Luiz Maia <  
Independent Technical Analysis  
Focus on system architecture, validation, and data integrity
