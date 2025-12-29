Required Plugins:

- Surge XT 

- Surge XT Effects (maybe not anymore? verify!)

- ToolChain


Required Builtins:

- Note Transpose

- Arpeggiator

- EQ-5



----------------------------------------------------------------------------------------------------
ToDo / Notes:

- The FilterBass patch was originally quite detuned and I retuned it by ear. 
  ToDo: Tune it properly and exactly. Maybe use a pitch detector plugin for that. Play a somewhat 
  higher note and then use the "Pitch" slider in Surge
  ...I'm currently at around -0.5 semitones...but it's just rough adjustment
  Maybe put a pitch-detector output on the pitch-shifter in ToolChain. But maybe I should make a 
  dedicated pitch-detector plugin with various algorithms (zero-crossings, autocorrelation, 
  frequency-domain, etc.). Or maybe use one of these:
  https://www.katjaas.nl/helmholtz/helmholtz.html
  https://github.com/orchidas/Pitch-Tracking
  
- After the "Pizzi Theme" marker, the pizzis are quite loud. Apparently, the limiter on the master 
  pulls the volume up quite a lot at this point - I think, a bit too much. Maybe that can be 
  counteracted but putting some low-freq bass-sound underneath. Maybe pizzis playing in low octaves 
  or maybe the filterbass or maybe the brass or maybe some additional sub-bass sound whose main 
  purpose is not to be actually very audible but rather to disengage the volume boosting by the 
  limiter. Or maybe automate the limiter. Or maybe put a multiband-compressor in front of it.
  
- The pizzis could benefit from a bit more transient and/or high-frequency content. At least, when  
  in the first part and when listening via loudspeakers. Maybe try to edit the amp-envelope and/or 
  filter envelope. Or maybe try layering them with some "clicky" sound. Maybe the 2nd "scene" in 
  Surge itself could be used for this. Or perhaps they could be rhythmically supported by some 
  HiHat. Or maybe try integrating a TransientShaper into Quadrifex and then create split-eq and use 
  that. And/or maybe try a harmonic exciter.
  
- Maybe at bar 99, remove the brass note - it's barely noticable and maybe just create mud  
  
- At bar 113 (until 177) - maybe use some sort of percussive sound like timpani or some other 
  epic "impact" sound - always on the 1 to do this question/answer thing with the brass on the 3.
  Maybe this can also be used a couple of times in the part starting at 17. Maybe also at 83 and 97.
  Or maybe at 93
  Maybe one of these could be a good fit:
  https://freesound.org/people/Quonux/sounds/734118/
  https://freesound.org/people/Micah10/sounds/791446/
  
- Check, if all plugins correctly receive the sample rate from he host. Maybe some plugin think 
  they are running at 44.1 and others at 48? That would explain the detuning. But I don't think, 
  it's that. The other Surge instances are not detuned. It may be an issue with the patch.
  
- The end is too abrupt. Maybe put a long reverb-tail on the final brass note. And or maybe hold it
  longer and pitchbend it down one ocatve at the end.
  
- Elektrobeat part needs snare or clap , maybe

- Try to invert the polarity of the bass to see if this fits better with the bassdrum. Maybe try to
  phase-align bass and bassdrum - maybe in Surge, we cand adjust the oscillator phase? ...but it 
  when it's aligned for one note, it may not be for another - so maybe using ducking and/or 
  highpassing the bass by the kick is better.
  
- Check the tuning of the bassdrum. It's actually rather atonal but maybe the tuning could still be 
  optimized? I'm letting it play on the note F because that sounded best but maybe it can still be 
  improved by fine-tuning? If doing so, check it also where it plays some other notes - that happens
  occasionally.

- Maybe in some parts, a HiHat would be nice. And/or a clap or snare.

- Check the stereo width and possibly adjust with mid/side tools (perhaps mid/side EQ). But maybe
  do this per track. The side signal seems to be rather weak.
  
- Maybe in the intro, the FilterBass should not be highpassed so much. Maybe automate the highpass 
  such that it is in full effect only when the bassdrum begins. Maybe use ToolChain with 
  LadderFilter in highpass mode and slowly ramp up the cutoff.
  
- Replace all equalizers with the one from ToolChain.
  
- Review the plugins and settings in the master channel. The adjustment of the final limiter is:
   Limit:         0.00 dB
   Attack:       10.00 ms 
   Release:    ~360.30 ms 
   LookAhead:    10.00 ms lookahead (should be the same as  attack, I think)
   InLevel:      +6.00 dB
   OutLevel:      0.00 dB
   Dry/Wet:     0/100
  This sound quite OK. The level meter in Bitwig (at the top of the GUI) turn occasionally red 
  (indicating clipping/overload) in the loudest part (from bar 177). I think, this is fine. Turning 
  up the InLevel further (up to 8 dB) makes it red most of the time. It still sounds fine I think, 
  so maybe we can push it 2 dB more. But maybe that's too much already. Maybe try using a multiband 
  compressor before the (wideband) limiter. Maybe also another wideband complresso (or leveler) 
  before the limiter. I think, they should work in MS-mode.

----------------------------------------------------------------------------------------------------
Done:

- Try to get rid of the "Note Transpose" effect on the Pizzi. Transpose all the MIDI data itself.
  Or: Let ToolChain have a MIDI-Transpose effect as well. ...maybe even an Arpeggiator.
  Or: Make a clap plugin suite that also contains a note transposer. It could also contain 
  equalizers to replace EQ-5. Maybe make an EQ4 and an EQ8. Or call them TwoPole4, TwoPole8. 
  Implement them as SVFs. Maybe they should be parametrized in terms of Q rather than bandwidth. 
  Look up how Bitwig, StudioOne and Cubase parametrize their EQs - if they all use Q, we should do 
  the same to make the transition from builtin -> plugin easier because values can be copied 
  directly without requiring a conversion formula - iff they use the same definition of Q, that is. 
  Verify that!
  
- It would be nice, if we could export the arpeggiator sequence for the FilterBass into a MIDI 
  sequence and then use the midi and get rid of the arp to make the sequence usable in the later 
  section to let it play together with the pizzis. For that, some notes need to be changed in the 
  sequence when it goes to E# and then to A#. The sequence as is works only on C. The arp doesn't 
  really support different sequences based on the root note - or does it? If not, it would be a 
  great feature for an arp plugin! It could be realized by letting the user enter notes from the 
  used scale rather than the 12 notes from the keyboard.
  Maybe it's possible to record arp output into a midi track?
  If not, transcribe the sequence manually. It's not too complicated
  OK - it's kinda solved. I use shorter MIDI notes such the the sequence is not played through 
  completely. 
  BUT: It would still be nice to have the MIDI - to make it work also in other DAWs. I suppose, such
  states of builtin processors cannot be transfered to other DAWs, even if they have similar 
  builtins.
  
- 303 pan spread could be wider

- The Pizzi seems to be too wide. The spectrum of the side channel is louder than the mid channel.
  They should be at most equally loud - and that is already rather wide.

- The pizzicatos in the high octave sound upleasant and EQing doesn't seem to help much. I think, 
  we should go into the synth patch and make the overall volume key-dependent such that it goes down
  for the higher keys
  
- Review the 303 automation data at the end (when it plays together with the pizzis)