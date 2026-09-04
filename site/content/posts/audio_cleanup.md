---
title: "Audio Cleanup"
date: 2026-09-03
subtitle: "This post is for those who like to tinker with audio cleanup."
tags: ["Music", "Audio Cleanup"]
# featured: true
# mood: "Focused"
---

First and foremost, please note that I'm an amateur on this kind of thing, I think the end result was pretty good but I'm not gonna say it's the best it could be.

I started this project in the context of my folk group field recordings, containing interviews, songs and sometimes teachings on how to dance these songs. These are 30+ years amateur tape recordings, usually recorded without a proper microphone, as a result of aging as well as the recording conditions these tapes had a lot, and when I say a lot, is really a **Lot** of noise.

So if you have a similar case of old recordings to clean, buckle up, open Audacity and embark on this small journey with me.

## Recording the tape
Be careful with the volume on the tape recorder, too much and it becomes with too much noise. Best to keep somewhere in the middle. You can add a bit more gain after the audio is cleaned up.

## Noise Reduction
This is the main thing that I did, since the noise was pretty constant through out the tapes, I could actually just get a profile on a spot that has nothing but the actual noise, and then apply it to the tape, or part of the tape.

These are the steps:
1. Select sample of the recording with only noise;
2. Go the "Effect" window and click the Noise Reduction option;
3. Click on Step 1 button "Get Noise Profile";
4. Select portion of the tape you want to apply;
5. Go the "Effect" window and click the Noise Reduction option again;
6. Click "OK".

For the Step 2 options, I ended up with these values, but this is what worked best for my use case and it could change from tape to tape:

Noise Reduction: 18db
Sensitivity: 13

Note: This won't make all the noise disappear, since that would mean take those frequencies from the actual recording would vanish. That can be pretty bad since it also means the recording without those frequencies can sound pretty weird. You want balance.

## Low Pass Filter

With these being old recordings in mind, and basically no usable audio exists above the 10k frequencies, I just decided to run a Low Pass Filter to filter out everything above this 10k frequency.

The result is that any high pitched ring/noise will cease to exist without compromising none of the audio.

Steps:
1. Select portion of the tape you want to apply;
2. Go the "Effect" window and click select the plugin 1-15 -> Low Pass Filter;
3. Write the frequency of your threshold (in my case I chose 10k);
4. Select 48db;
5. Click OK.

You'll want to apply this only if you know your audio doesn't have any usable data above that frequency.

## Noise Gate
Ahhh, Noise Gate, do you know those background noises of a fan, cars in the street, wind? Yeah, it's pretty distracting especially when nobody is saying anything. Luckily Noise Gate exists to help us, It removes everything below a certain volume meter threshold.

Do you see the playback meter on the top? Good. You want to be looking at it and see the level it hits on the silence parts of the recording. Then follow these steps.

1. Select portion of the tape you want to apply;
2. Go the "Effect" window and click select the plugin 1-15 -> Low Pass Filter;
3. Choose the Gate threshold, the number you recorded previously;
4. Change the attack to 1ms;
5. Click OK.

## Spectral Edit
This is for those occasional sounds that appear in the recording, not constant background noise, so like a bird chirping, or a bark of a dog.

For this you want to change the view to the spectral view.

There are quite a few spectral edit tools on audacity:

### Spectral delete
This one is self-explanatory, it does just that, it deletes fully the selected frequencies, it does a good job at eliminating the noise, but if it happens during a conversation it might kill frequencies that you want to keep.

Use with caution

### Spectral edit multi tool
Best one for a quick cleanup, it is automatic. Just select the unwanted frequencies and select the effect. It will reduce the unwanted noise by a lot. It will reduce the noise by the midle outward, more in the middle, less in the outer regions of the selection

### Spectral edit parametric-EQ and shelves
This effects let you select by how much you want the selection to be reduced or increased.

The parametric-EQ will allow you to modify the tone quality using a gain control. Which basically means, it will reduce or increase the selection and the frequencies outside the selection may be adjusted as well like with an EQ curve.

The shelves one is almost the same as the parametric-EQ, but without the EQ curve, use this when you want a less aggressive low pass or high pass filter.

They all are powerful tools and they all have specific use cases, I recommend testing them out and see which one is best for the specific selection.

## EQ
The EQ can be really terrifying, and I'm not gonna lie and pretend it isn't a little bit. 

### A quick guide to the frequency spectrum
 
- 50-75Hz
    - Boost to beef up kick drums and sub bass lines. Cut to reduce excessive low-end weight.
- 80-200Hz
    - Boost to add body to snares and guitars, punch to kick drums, roundness to bass, and general warmth. Cut to reduce low-end mud.
- 200-500Hz
    - Boost to ‘warm up’ vocals, guitars and synths, and add presence to basses. Cut to reduce muddiness.
- 500-800Hz
    - Boost (with care!) to bring out the tone of almost any instrument. Cut to reduce ‘honk’.
- 2-5kHz
    - Boost to give vocals, guitars, synths and strings clarity, definition and impact. Cut to reduce harshness.
- 5-10kHz
    - Boost to add presence and sheen to drums, cymbals and guitars. Cut to reduce scratchiness and sibilance.
- 16kHz+
    - Boost for brightness and ‘air’. Cut to reduce high-end fizz.

I found this on a post online. Although the EQ is really dependent on the source material, your tapes or whatever recording you're trying to clean, and it may or may not have these instruments, this gives you an idea where all the frequencies sit on the spectrum. Now you know for example, that the most impact you can do on voice is around the 500-2k.

With this, what I found best was just to mess around and try to understand what changed when I dialed down certain frequencies on this spectrums, try big changes, the recording will sound odd, but it will give you a better idea of what happened.

For my needs, since the voice was way to nasal and the sound not bright in the slightest, I decided to diminish mids and boost the highs, so diminish from like 800hz until the 4k or 5khz and boost anywhere from 5k to 16khz.

## Clipping
For this problem you can use a lot of things, you can just repair a specific clip if it's an isolated incident, you can just amplify with a negative number to bring the whole thing down or use a compressor and then normalize the recording.

Bear in mind that once there's clipping, being because of damage or because the way it was recorded, the distortion will always be there, you can't make up data where there is none, these are ways to minimize the problem.

When it comes to really damaged parts, like "pops" and "clicks", caused by scratches on the tape or something else, we can try the click removal.

## Compressor
Compressor, a cool little effect to even out the dynamic range, loudest parts become quieter and quiet parts become louder.
You will want to use this for a couple of reasons, one of them is clipping, yes, but the main one is, in this setting the person that is being interviewed won't be always facing the same direction, they will not always be talking loud (or quiet).

## Normalize
After the compression is always a good idea to normalize the tape. What does this mean? Bring the whole thing up to a healthy and consistent volume, since the compression will make things quieter at times, the normalization will bring those parts back up but now using an even dynamic range.

## Order
This is the order I usually used these tools:
1. Noise Reduction;
2. Low pass filter;
3. EQ;
4. Noise Gate;
5. Compress;
6. Normalize.

**Note:** The spectral effects were not always needed, but when when they were needed, I usually did them between step 2 and 3.

## Closing thoughts
After doing this project I did learn something about sound in general, and what I learned was enough for my needs, but make no mistake, this is a big world to explore. For now I was able to clean only one tape of 13 (I think), So we'll see how many challenges will arise when I pick this up again and if I learn something new, I'll be sure to update this post or do a new one to share.