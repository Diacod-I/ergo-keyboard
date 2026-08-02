# My Ergonomic Keyboard

I have a ton of cramps and metacarpal pain due to typing on small keyboards like the Macbook keyboard (small relative to my larger-than-average hands). I'm going to solve that with an ergonomic keyboard. <br/>

Some guidelines for what I want:
- Keep it simple and go with QWERTY.
- Linear over staggered, but I need to aptly position the column based on my hand measurements.
- Split, so that I can position my arms more freely on a table.

I'm going to add all my work related to this here.

## Build Log
### 2/8/2026 (Newest update!)

#### Did today
1) Manually measured my hands to understand and evaluate an ideal finger placement (since I didn't have a touch screen to test using 
<div align="center">
<img width="360" height="480" alt="BEB380F8-2C89-42DD-A3A0-69BD96AF3945_4_5005_c" src="https://github.com/user-attachments/assets/e6a3e43c-fdf8-47f3-8472-830c761ccba8" />
<p>Figure 1. Manual calculations</p><br/>
</div>

2) Filled the MCU pin map: matrix on P2–P10 (cols P2–P6, rows P7–P10), split data on P1, VCC/GND on the rails. Same pads on both halves (identical firmware; QMK handles the split). Left P0 + P14 -> P21 free for the OLED SPI bus / shift-registers later.

3) Started assigning nets directly on the controller pads in KiCad.

4) Wired the split link: typed a new data net onto each controller's P1 and each TRRS jack, plus VCC/GND. Both jacks assigned identically so the cable ties the halves together correctly.
Set up git for the project + .gitignore.
<div align="center">
<img width="907" height="348" alt="Screenshot 2026-08-02 at 9 38 25 PM" src="https://github.com/user-attachments/assets/c15b96da-4430-4539-8922-d74f60c38193" />
<p>Figure 2. Ergogen Key Layout</p><br/>
</div>

<div align="center">
<img width="1102" height="772" alt="Screenshot 2026-08-02 at 9 37 22 PM" src="https://github.com/user-attachments/assets/b9c308fd-fe34-4728-bc07-9b32113005e6" />
<p>Figure 3. KiCAD PCB layout before net assignment</p><br/>
</div>

#### Learned

- Blue ratsnest lines = connections that exist but aren't copper yet. Routing = turning every blue line into a trace. When they're all gone, it's routed.
- A net only exists once a pad uses it. I had to type data into existence (it wasn't in the dropdown).
- TRRS: exact pad doesn't matter, but data/VCC/GND must be on matching contacts on both jacks or the split won't talk. Sleeve = GND by convention.
Important: board.kicad_pcb now has hand edits (outline curves + net assignments) that are NOT in config.yaml.

#### Still open

- Finish assigning all controller pads -> route the matrix -> ground pour -> DRC -> Gerbers -> order.
- Keymap dry-run (flash the Corne keymap.c, settle hold-vs-toggle) - not started.
- OLED v2: scaffolded + commented out, parked until a test rig.

### 13/3/2026
- Nevermind, we stick to QWERTY

### 12/3/2026
- I'm considering the layout amongst DVORAK and Coleman-DH from [the Knucklehead layout](https://github.com/minusfive/knucklehead/blob/main/README.md)

### 11/3/2026
- Making the plan for what I wanna make in my keyboard. Following is some ideas that I am considering
    1) Corne style split keyboard (easy to carry around) 
    2) Ortholinear columns with a slightly wider gap between each other for my big hands.
    3) VIM focused key layout 
    4) LED backlight 
    5) Arm rest????
    6) Check out bluetooth connection across the split keyboard along with the cable option just in case.
- I am considering Ergogen but there should be other ways to make the design.
- Roadmap would something like the following:
    1) Design PCB and key layout
    2) Make the PCB connections
    3) Buy the microcontrollers and extra parts
    4) Get the PCB made
    5) Get Soldering kit and solder everything
    6) Fix everything together
    7) Code the microcontroller logic and key mapping logic

