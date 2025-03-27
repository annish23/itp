#README.md

## Work Progress

### 1. Initial Setup with Single Audio File
   - First, I copy and paste the code in code alone to p5.js and I uploaded a sound file (`coin.wav`) and tested it with a key press ('C').
   - The `loadSound()` function successfully loaded the audio file, and pressing the 'C' key played the `coin.wav` sound.

### 2. Adding More Sounds and Facing Issues
   - To expand the project, I added two more audio files: `fuzz.wav` and `explosion.wav`.
   - I created new `preload()` and `keyPressed()` functions for each additional sound. However, I encountered a problem where the second `preload()` function and the second `keyPressed()` function were overwriting the first ones. This resulted in only the last sound being loaded and triggered correctly.

### 3. Troubleshooting and Combining Functions
   - I realized that having multiple `preload()` and `keyPressed()` functions caused the first ones to be ignored, so I combined them into a single function for each.
   - The combined `preload()` function now loads all three sound files, and the combined `keyPressed()` function listens for key presses and triggers the corresponding sound.

### 4. Final Working Solution
   - I rewrote the code so that all three sounds are loaded and mapped to different key presses ('C' for `coin.wav`, 'F' for `fuzz.wav`, and 'S' for `explosion.wav`).
   - This solution ensures that all sound files are loaded correctly, and key presses are handled without overwriting the previous functions.

## Final Working Code
Here is the hyperlink https://editor.p5js.org/annish23/sketches/tlrAPEAVX
Here is the final working version of the code after combining the functions:

`
let SoundC, SoundF, SoundS; 

function preload() { 
  soundFormats('wav', 'mp3'); 
  SoundC = loadSound('coin.wav', soundLoaded); 
  SoundF = loadSound('fuzz.wav', soundLoaded); 
  Souns = loadSound('sp.wav', soundLoaded); 
} 

function setup() { 
  createCanvas(400, 200); 
  textSize(20); 
  textAlign(CENTER, CENTER); 
  text("Move your cursor to the 'Preview' section\nPress 'C', 'F', or 'S' to play sound", width / 2, height / 2); } 

function soundLoaded() { 
  console.log("Sound successfully loaded!"); } 

function keyPressed() { 
  console.log("Key pressed:", key); 
  
  if (key.toLowerCase() === 'c') { 
    playCustomSound(SoundC); 
  } else if (key.toLowerCase() === 'f') { 
    playCustomSound(SoundF); 
  } else if (key.toLowerCase() === 's') { 
    playCustomSound(SoundS); 
  } 
} 

function playCustomSound(sound) { 
  if (sound.isLoaded()) { 
    sound.play(); 
    console.log("Sound played."); 
  } else { 
    console.log("Sound not loaded yet."); 
  } 
}
`