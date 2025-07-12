Required Plugins:

- Surge XT 

- Surge XT Effects (maybe not anymore? verify!)

- ToolChain


Required Builtins:

- Note Transpose

- Arpeggiator

- EQ-5




Notes:

- The FilterBass patch was originally quite detuned and I retuned it by ear. 
  ToDo: Tune it properly and exactly. Maybe use a pitch detector plugin for that. Play a somewhat 
  higher note and then use the "Pitch" slider in Surge
  ...I'm currently at around -0.5 semitones...but it's just rough adjustment
  
- Check, if all plugins correctly receive the sample rate from he host. Maybe some plugin think 
  they are running at 44.1 and others at 48? That would explain the detuning. But I don't think, 
  it's that. The other Surge instances are not detuned. It may be an issue with the patch.
  
- The end is too abrupt. Maybe put a long reverb-tail on the final brass note.  
  
- Elektrobeat part needs snare or clap , maybe

- Maybe in some parts, a HiHat would be nice. And/or a clap or snare.

- Check the stereo width and possibly adjust with mid/side tools (perhaps mid/side EQ). But maybe
  do this per channel.
  
- It would be nice, if we could export the arpeggiator sequence for the FilterBass into a MIDI 
  sequence and then use the midi and get rid of the arp to make the sequence usable in the later 
  section to let it play together with the pizzis. For that, some notes need to be changed in the 
  sequence when it goes to E# and then to A#. The sequence as is works only on C. The arp doesn't 
  really support different sequences based on the root note - or does it? If not, it would be a 
  great feature for an arp plugin! It could be realized by letting the user enter notes from the 
  used scale rather than the 12 notes from the keyboard.
  Maybe it's possible to record arp output into a midi track?
  If not, write the sequence off manually. It's not too complicated
  OK - it's kinda solved. I use shorter MIDI notes such the the sequence is not played through 
  completely. 
  BUT: It would still be nice to have the MIDI - to make it work also in other DAWs
  
- Maybe in the intro, the FilterBass should not be highpassed so much. Maybe automate the highpass 
  such that it is in full effect only when the bassdrum begins
  
- Try to get rid of the "Note Transpose" effect on the Pizzi. Transpose all the MIDI data itself.
  Or: Let ToolChain have a MIDI-Transpose effect as well. ...maybe even an Arpeggiator.
  Or: Make a clap plugin suite that also contains a note transposer. It could also contain 
  equalizers to replace EQ-5. Maybe make an EQ4 and an EQ8. Or call them TwoPole4, TwoPole8. 
  Implement them as SVFs. Maybe they should be parametrized in terms of Q rather than bandwidth. 
  Look up how Bitwig, StudioOne and Cubase parametrize their EQs - if they all use Q, we should do 
  the same to make the transition from builtin -> plugin easier because values can be copied 
  directly without requiring a conversion formula - iff they use the same definition of Q, that is. 
  Verify that!



- Done.
  303 pan spread could be wider

- Done.
  The Pizzi seems to be too wide. The spectrum of the side channel is louder than the mid channel.
  They should be at most equally loud - and that is already rather wide.

- Done.
  The pizzicatos in the high octave sound upleasant and EQing doesn't seem to help much. I think, 
  we should go into the synth patch and make the overall volume key-dependent such that it goes down
  for the higher keys
  
- Done.
  Review the 303 automation data at the end (when it plays together with the pizzis)