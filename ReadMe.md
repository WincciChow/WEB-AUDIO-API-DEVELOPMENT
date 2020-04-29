# Project for musicianship
The AudioContext interface is extremely powerful letting you chain together various effects. For our purposes we are using only the OscillatorNode (represents a periodic waveform) and gainNode (a change in volume) to create our sounds.
```javascript
  // Create your AudioContext
    var audioCtx = new AudioContext();
    // Create a Oscillator
    var oscillator = audioCtx.createOscillator();
    // Controlled object
    var gainNode = audioCtx.createGain();
    // relate them
    oscillator.connect(gainNode);
    // connect with your device
    gainNode.connect(audioCtx.destination);
    // Set oscillator type as Sine wave 
    oscillator.type = 'sine';
    // set frequency
    oscillator.frequency.value = 496.00;
    // Volumn at the moment 0
    gainNode.gain.setValueAtTime(0, audioCtx.currentTime);
    // Volume from 1 to 0.001 with one second linear
    gainNode.gain.linearRampToValueAtTime(1, audioCtx.currentTime + 0.01);
    // music start
    oscillator.start(audioCtx.currentTime);
    // Volume from 1 to 0.001 with one second exponential
    gainNode.gain.exponentialRampToValueAtTime(0.001, audioCtx.currentTime + 1);
    // stop playing after 1s
    oscillator.stop(audioCtx.currentTime + 1);
```

