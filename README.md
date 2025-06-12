LabanLite ASCII Notation Specification (v0.1)
Purpose
LabanLite ASCII is a compact, ASCII-safe format inspired by Labanotation. It represents movement in a linear, human-readable, and machine-parseable format.
Goal
Enable choreography, motion analysis, and training using short, memory-friendly tokens.
Each token is a series of characters that describe one unit of movement.
Token Format
BodyPart Duration Direction Flow Space Level Time Weight Special
Example:
lA3FR52M17twist
Field Breakdown
1. BodyPart (1-2 letters)
Format: {side}{part}
Common codes:
    • lA = Left Arm
    • rA = Right Arm
    • lL = Left Leg
    • rL = Right Leg
    • lF = Left Foot
    • rF = Right Foot
    • lH = Left Hand
    • rH = Right Hand
    • H = Head
    • C = Chest
    • T = Torso
    • P = Pelvis
2. Duration (digits)
Movement duration in counts (default). May use other units as specified by the setter string.
3. Direction (1–3 letters)
    • F = Forward
    • B = Backward
    • L = Left
    • R = Right
    • U = Up
    • D = Down
    • I = Inwards
Combinations: FL, FR, BL, DBR, FUR, BU, etc.
4. Flow (1 digit)
Effort quality (0–9)
E.g., Free ↔ Bound
5. Space (1 digit)
Spatial focus (0–9)
E.g., Indirect ↔ Direct
6. Level (1 letter)
    • H = High
    • M = Middle
    • L = Low
7. Time (1 digit)
Timing quality (0–9)
E.g., Sustained ↔ Sudden
8. Weight (1 digit)
Physical effort (0–9)
E.g., Light ↔ Strong
9. Special (optional)
Word tag for gesture type, shape, or intent
Examples: punch, twist, jump, hold
Token Examples
    1. lA3FR52M17twist
→ Left Arm, 3 counts, Forward-Right, Flow 5, Space 2, Middle, Time 1, Weight 7, Special: twist
    2. rT1BL43L89
→ Right Torso, 1 count, Back-Left, Flow 4, Space 3, Low, Time 8, Weight 9
    3. H2FU87H95hold
→ Head, 2 counts, Forward-Up, Flow 8, Space 7, High, Time 9, Weight 5, Special: hold
Special Characters
    • , = tokens begin simultaneously
    • . = 1 unit of time passes
    • : = 1/2 unit of time
    • :: = 1/4, ::: = 1/8 etc
    • ! = end of part
    • !! = end of choreography
    • x[] = repeat token(s) x times (return directly to token beginning position for repeat)
    • xr[] = repeat token(s) x times (retrograde through token to beginning position for repeat)
    • x() = dancer x performs these tokens
Chaining Movements
Simultaneous Actions:
lA3F52M17punch,rA3F52M17punch
→ Both arms punch forward together for 3 counts.
Staggered Start:
lA3F52M17punch.rA3F52M17punch
→ Right arm starts one count after left.
Delayed Sequence:
lA3F52M17punch...rA3F52M17punch
→ Right arm starts three counts after left.
Partial Count Timing:
lA1F52M17punch:rA1F52M17punch
→ Right arm begins halfway through left's 1-count punch.
lA1F52M17punch::rA1F52M17punch
→ Right arm begins a quarter-count into left's movement.
Note: Full stops (.) come AFTER the token on their count.
Setter Strings
The first line of choreography should begin with a setter string followed by a semi-colon (;). This sets global parameters.
Examples:
    • 4T135bpmGLAMOROUS; → 4 dancers, tempo 135 BPM, glitter-covered
    • 1S10dWET; → Solo, 10 seconds duration, underwater
Optional Starting Positions:
lHBR,rAR,PU → Left Hand Back-Right, Right Arm Right, Pelvis Up
Duet Example
2T90FRANTIC1(lhU,TRB,PD)2(HD,PU);
1(
2[T4FL56M86coil],P1I33L21tuck...rH3U12H07raise
3[lH2D44L33].C3F25M41bend....C4B83M52,
rF2FR42L27step,lH3U11H43reach....rH1D35M06drop,
P3BU54M19tilt...2[T2FU23H20extend]..
lL4BR71L38kick,rL2BL41L14kick....
lA1L24M07swipe.rA1R21M06swipe,H2U63H18look!
)
2(
5[P1B33L21tuck]...2r[rH3U12H07].......
rA1R21M06swipe,H2U63H18look!
)!!
Code Order Reasoning
    • Starts with body and timing info — most useful when scanning movement
    • Alternating letters and numbers aid readability
    • 0–9 values are ordered: Flow - Space - Level - Time - Weight
    • Think of the structure: flow-SPACE-level-TIME-weight
Use Cases
    • Choreographic sketching
    • Digital motion capture markup
    • Dataset compression
    • Creative generative dance systems
Future Features?
    • Expanded body taxonomy
    • Symmetry/reflection notation
    • Floor plans, perhaps using a grid navigation system to represent the dancer's pathway
Example: URULLDURLDDLRUDURLLDDLDLL
Author
Developed by Jake Bradnock, 2025.
LabanLite is freely shareable and extensible. Use it in dance, robotics, animation, or beyond.
­
