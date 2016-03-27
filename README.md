# neuralman
Playing with neural networks to generate MegaMan music.

Yet another work in progress that may or may not turn into something
interesting.


## NES Audio Processing Unit (APU)

Two good references:
  * [http://wiki.nesdev.com/w/index.php/APU](http://wiki.nesdev.com/w/index.php/APU)
  * [http://nesdev.com/apu_ref.txt](http://nesdev.com/apu_ref.txt)


### Memory-mapped Registers

To create sound on the NES, assembly code writes to addresses `$4000` through
`$4017` of the 2a03 CPU. The sound is actually produced by the CPU reading
instructions that have been placed in these registers.

A trained neural network would seem more likely able to develop its own idea
of what kind of sound should be output by the APU, rather than how 6502
assembly itself works. After all, the former is the nonsemantic musical output
we seek, and the latter is the expressive and grammatical semantic tool that we
use. Let's target the output!

The problem arises, however: NSF files contain assembly code to be executed,
not actual performances. We want to train against the raw words, and develop
code to produce NEW performances. This means we'll need to build (or find) a
way to record the NES APU performance, and a way to programmatically generate
(unoptimized) assembly code to reproduce register states.
