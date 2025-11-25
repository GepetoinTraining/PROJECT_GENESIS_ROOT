Markdown

# PROJECT GENESIS: OPERATOR'S MANUAL

**Status:** ACTIVE
**Compiler Requirement:** XeLaTeX (Required for `fontspec`)
**Version:** 1.0 "Speed x Resolution"

---

## 1. SYSTEM ARCHITECTURE

This project is modular. Do not write logic in `main.tex`. 
Use the dedicated sub-systems.

```text
/root
  ├── main.tex              # The Controller (Page.tsx)
  ├── /fonts                # .ttf storage (Fira Sans/Code)
  ├── /images               # Visual assets
  ├── /styles               # The DNA (Colors, Type)
  │     ├── colors.sty
  │     └── typography.sty
  ├── /components           # The Bricks (Bubbles, Terminal)
  │     ├── bubbles.sty
  │     └── terminal.sty
  └── /content              # The Soul (Text & Logic)
  
## 2. COLOR PROTOCOL (styles/colors.sty)
We use a semantic color system. Do not use hex codes in the document. Use the variable names to ensure "Light/Dark" logic holds.

Core Variables:

mit_cardinal: The official Red.

enigma_bakelite: Deep brown/black background.

term_green: The phosphor glow.

UI Variables (Use these for layout):

\color{ui_dark_bg}: The main background for Dark Mode.

\color{ui_light_bg}: The main background for Light Mode.

\color{ui_dark_text_primary}: Readable text on dark.

Derivatives: You can mix colors on the fly: \color{mit_cardinal!50!black} (50% Red, 50% Black).

3. TYPOGRAPHY PROTOCOL (styles/typography.sty)
Font Loading: The system automatically looks in the /fonts folder. Do not install fonts on the system; just drop the .ttf files there.

The "Gate" Title: Use this command for all major headers. It handles the fallback logic automatically.

Code snippet

\GenesisTitle{THE HUNTER}
Effect: Renders in Fira Sans ExtraBold with cinematic tracking.

4. COMPONENT: CHAT BUBBLES (components/bubbles.sty)
The conversation interface.

The System Bubble (Left Aligned):

Code snippet

\begin{systemchat}
    Operational Directive Confirmed.
\end{systemchat}
The Hunter Bubble (Right Aligned):

Code snippet

\begin{userchat}
    Initiate sequence.
\end{userchat}
Advanced Usage (Light Mode Override): To force a bubble to look correct in the "Light Mode" OCG layer, pass the semantic overrides:

Code snippet

\begin{systemchat}[colback=ui_light_bubble_sys, coltext=ui_light_text_primary]
    System is compatible with Light Mode.
\end{systemchat}
5. COMPONENT: TERMINAL (components/terminal.sty)
The high-fidelity code display.

Basic Usage:

Code snippet

\begin{genesisblock}{filename.js}
const logic = "Speed x Resolution";
\end{genesisblock}
Effect: Creates a dark terminal window with traffic lights, title bar, line numbers, and syntax highlighting.

6. INTERFACE: OCG LAYERS (Dark/Light Mode)
The Switch: Located in main.tex. Uses \switchocg to toggle visibility.

Code snippet

\switchocg{darklayer lightlayer}{ TOGGLE BUTTON TEXT }
The Logic: Wrap content in environments:

Code snippet

\begin{ocg}{DarkLayer}{darklayer}{1} % 1 = Visible by default
   % Content for Dark Mode
\end{ocg}

\begin{ocg}{LightLayer}{lightlayer}{0} % 0 = Hidden by default
   % Content for Light Mode
\end{ocg}
7. DEPLOYMENT CHECKLIST
[ ] Upload Fonts: Ensure FiraSans-*.ttf and FiraCode-*.ttf are in /fonts.

[ ] Set Compiler: Menu > Compiler > XeLaTeX.

[ ] Compile: CTRL+Enter.


**Ready for the next component?** We still need the **Manifest** (Image Router) before we build the Main Controller.