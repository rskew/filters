NoisyGen noise generator
===

What
---
A simple low pass filter that runs on the command line.

Takes white noise from /dev/urandom, processes it with a low pass filter and outputs a byte stream for playing with aplay.

Why
---
I use this noise generator when I need to concentrate in a noisy environment. Changing the filter parameters allows masking of different sounds in different environments.

How
---
A 'forgetful integrator' filter is implemented by adding the next sample to the previous filter state multiplied by a 'memory' factor. This gives a geometric sequence impulse response with the response dictated by the 'memory' parameter.

By tweaking the **Response** and **Poles** variables in the NoisyGen.sh script you can vary the quality of the noise from thunderous waterfall to harsh white hiss.

**Response** dictates the 'memory' of the filter. The larger the memory, the larger the averaging window and the less high frequency content in the output, ie Reponse is inversely related to the filter cutoff.

**Poles** dictates the number of filter stages. With a high number of poles, the frequency spectrum cuts of more sharply around the cutoff frequency.

For a more in-depth and mathematical treatment of digital filters, I like [Julius O Smith III's online books on digital signal processing](https://ccrma.stanford.edu/~jos/filters/filters.html).

Building
---
Currently a very primitive script compiles the few existing files. To be extended to an Ant/Mavem/Gradle build system as it grows.

Running
---
The script NoisyGen.sh runs the noise generator by passing in white noise from /dev/urandom and outputting the filtered signal to aplay in stereo. On Windows these will beed to be substituded with appropriate white noise generation and sound playback programs.