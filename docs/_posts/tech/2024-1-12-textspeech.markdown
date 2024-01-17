---
layout: post
title:  "Converting Text to Speech and Speech to Text using gTTS and Vosk"
date:   2024-1-12 06:25:17 -0800
categories: jekyll update technology
---
# Introduction 

In this blog post, we'll explore how to convert text to speech and then convert that speech back to text using Python. We'll utilize the `gTTS` library for text-to-speech conversion and the `vosk` library for speech-to-text conversion. The entire process involves saving the generated speech as an MP3 file, converting it to a WAV file, and finally using the Vosk library for speech recognition.

## Installing Required Packages

Before we proceed, let's make sure we have the necessary packages installed:

```bash
!pip install gtts pydub vosk &>/dev/null
```

This will install the `gTTS`, `pydub`, and `vosk` packages, which are essential for our text-to-speech and speech-to-text tasks.

## Text to Speech with gTTS

To get started, we'll use the `gTTS` library, a Python wrapper for Google Text-to-Speech (gTTS) API. This library allows us to convert text into speech easily. Here's a simple example:

```python
from gtts import gTTS
from pydub import AudioSegment

# Text to be converted to speech
text = "Hello, this is a test. One two three four five. Ten nine eight seven."

# Create a gTTS object
tts = gTTS(text=text, lang='en')

# Save the speech as an mp3 file
tts.save('test.mp3')
```

In this example, we generate an MP3 file named `test.mp3` containing the synthesized speech from the given text.

## Converting MP3 to WAV

Next, we need to convert the MP3 file to a WAV file with a RIFF header, as Vosk requires input audio in this format. We can use the `pydub` library for this task:

```python
from pydub import AudioSegment

# Convert the mp3 file to a wave file with the RIFF header
mp3_audio = AudioSegment.from_file("test.mp3", format="mp3")
wave_audio = mp3_audio.set_frame_rate(16000).set_sample_width(2).set_channels(1)

# Save the wave file
wave_audio.export("test.wav", format="wav")
```

This code takes the `test.mp3` file, sets the appropriate parameters for Vosk, and saves the resulting WAV file as `test.wav`.

## Speech to Text with Vosk

Now that we have our WAV file, we can use the Vosk library for speech-to-text conversion:

```python
from vosk import Model, KaldiRecognizer
import wave

# Load Vosk model for English
model = Model(lang="en-us")

# Open the WAV file
wf = wave.open('test.wav', 'rb')

# Initialize the recognizer with the WAV file's frame rate
rec = KaldiRecognizer(model, wf.getframerate())

# Process the audio data in chunks
while True:
    data = wf.readframes(40)  # Adjust the chunk size as needed
    if len(data) == 0:
        break
    if rec.AcceptWaveform(data):
        pass

# Get the final result
result = rec.FinalResult()
print(result)
```

In this code snippet, we use the Vosk library to create a speech recognizer and process the audio file in chunks. The final result is then printed, providing the text representation of the speech.

## Displaying the Resulting Audio

Lastly, let's display the resulting audio using the `IPython.display` module:

```python
from IPython.display import Audio
display(Audio('test.wav', autoplay=True))
```

This line of code will play the audio directly in your Jupyter notebook, allowing you to hear the synthesized speech and confirm the accuracy of the text-to-speech conversion.