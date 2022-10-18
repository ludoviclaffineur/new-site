---
title: "Granular Synthesiser"
header:
  overlay_image: /assets/images/granular_synth.png
  og_image: /assets/images/granular_synth.png
tagline: "Deep explaination of granular synthesiser developper with OpenFrameworks."
last_modified_at:  2020-03-17 9:21:20 +0200
related: false
---

When I worked for [Laras](http://laras.be), I had the opportunity for my sonification project to model and code my own granular synthesiser.
## How it works

> Granular synthesis is a basic sound synthesis method that operates on the microsound time scale.
> It is based on the same principle as sampling. However, the samples are not played back conventionally, but are instead split into small pieces of around 1 to 50 ms. These small pieces are called grains. Multiple grains may be layered on top of each other, and may play at different speeds, phases, volume, and frequency, among other parameters.

*[Source wikipedia](https://en.wikipedia.org/wiki/Granular_synthesis)*

## Creation of grains
We first have to load a wave form in order to pick some samples to create our grains. Those grains are randomly selected within a window (subset) of the whole waveform as you can see on the figure 1. Having a window can be convenient if you want to select only certain parts of the waveform and move this window to modify the generated grains.

<p align="center">
<img src="/assets/images/sample_selection.png" alt="Grain selection"/>
</p>
<p align="center">
Figure 1: Sample selection
</p>

A grain is composed of selected samples (within an envelope) and some blank at the end. Reducing the blank will accelerate the succession and the production of grains.

**Grain = (Selected samples x Envelope) + Blank**

In order to select a grain we pass the pointer of the waveform `float* audioFile` with a duration `int mDuration` and a position `int mInitPosition`. The initial position is randomly set in the window and has to make sure the grain can be read (i.e.: that the grain is included in the waveform)

```cpp
class Grain{
public:
    Grain(
      float* audioFile,
      int duration,
      int blank,
      int initPos,
      int channels,
      int musicSize
    );
    samples getSample();

    int mEnvelope;
    int mDuration;
    int mCurrentPostion;
    int mInitPostion;

    float* mAudioFile;
    bool isDone(){
        return done;
    }
    bool done;
    int mBlank;
    int mWindowSize;
    int mChannels;
    int mMusicSize;
};
```
## Playing the grains


If you play the selected sample without envelope you will face jumps in your resulting waveform and you will hear clicks. An envelope that does not affect too much the harmonics of the signal is chosen and will smoothen the beginning and the end of the samples.

>Most references to the Hanning window come from the signal processing literature, where it is used as one of many windowing functions for smoothing values. It is also known as an apodization (which means “removing the foot”, i.e. smoothing discontinuities at the beginning and end of the sampled signal) or tapering function."
*[Source scipy doc](https://docs.scipy.org/doc/numpy/reference/generated/numpy.hanning.html)*

```cpp
float hanningCoeff = 0.5 - 0.5* cosf(2*M_PI *(float)mCurrentPostion/(float)(mDuration));
```

Everytime that a sample is needed from a grain  `Grain::getSample()` is called. This returns the current value of the sample and moves to the next sample.


```cpp
samples Grain::getSample(){
    samples current_sample;
    float sample = 0.0f;
    if (mCurrentPostion <mDuration) {
        float hanningCoeff = 0.5 - 0.5* cosf(2*M_PI *(float)mCurrentPostion/(float)(mDuration));
        if(mChannels == 1){
            current_sample.right = mAudioFile[mInitPostion+mCurrentPostion]*hanningCoeff;
            current_sample.left  = mAudioFile[mInitPostion+mCurrentPostion]*hanningCoeff;
        }
        else if(mChannels == 2){
            current_sample.left = mAudioFile[mInitPostion+mCurrentPostion*mChannels    ]*hanningCoeff;
            current_sample.right  = mAudioFile[mInitPostion+mCurrentPostion*mChannels + 1]*hanningCoeff;
        }

    }
    else if(mCurrentPostion< mDuration+ mBlank){
        current_sample.left = 0.0f;
        current_sample.right = 0.0f;
    }
    else{
        done = true;
    }
    mCurrentPostion++;
    return current_sample;
```
<p align="center">
<img src="/assets/images/grain_play.png" alt="Grains player"/>
</p>
<p align="center">
Figure 2: Grains player
</p>

```cpp
samples ofxGranularSynth::getSample(){
    samples sampleResult;

    // this condition is there to add a new grain in the vector.
    if(mGrains.size()==0 || mPosition++ > (mGrains[mGrains.size()-1]->mDuration
      + mGrains[mGrains.size()-1]->mBlank - mOverlap)){
        if(mDuration >mOverlap){
          mGrains.push_back(
            new Grain(
              music,
              mDuration,
              mBlank,
              mInitPos,
              mChannel,
              musicSize
            )
          );
        }
        mPosition = 0.0f;
    }
    // check that the grain is not empty otherwise it means that the result should be 0
    if (mGrains.size()!=0) {
        if (mGrains[0]->isDone()){
            delete *mGrains.begin();
            mGrains.erase(mGrains.begin());
        }
        for(int i =0; i<mGrains.size();i++) {
            samples retour = mGrains[i]->getSample();
            sampleResult.right += retour.right;
            sampleResult.left += retour.left;
        }
    }
    else{
        sampleResult.right = sampleResult.left = 0.0f;
    }
    return sampleResult;
}

```

## Result

<iframe src="https://player.vimeo.com/video/130955655" width="640" height="479" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>
<p><a href="https://vimeo.com/130955655">ofxGranularSynth</a> from <a href="https://vimeo.com/user41154273">Ludovic Laffineur</a> on <a href="https://vimeo.com">Vimeo</a>.</p>
### Code Source
[Github -- ofxAudioGen](https://github.com/ludoviclaffineur/ofxAudioGen)

If you want to run this example you only have to build [this example](https://github.com/ludoviclaffineur/ofxAudioGen/tree/master/GranularSynth)

## Improvements

To improve this part of the project, we should add support for different audio input file. For the moment it's only .wav.
