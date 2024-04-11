# StyleTalker

The rapid advancement of large language models (LLMs) has significantly propelled the development of text-based chatbots, demonstrating their capability to engage in coherent and contextually relevant dialogues. However, extending these advancements to enable end-to-end speech-to-speech conversation bots remains a formidable challenge, primarily due to the extensive dataset and computational resources required. The conventional approach of cascading automatic speech recognition (ASR), LLM, and text-to-speech (TTS) models in a pipeline, while effective, suffers from unnatural prosody because it lacks direct interactions between the input audio and its transcribed text and the output audio. These systems are also limited by their inherent latency from the ASR process for real-time applications. This paper introduces StyleTalker, an innovative framework that fine-tunes an audio LLM alongside a style-based TTS model for fast spoken dialog generation. StyleTalker takes user input audio and uses transcribed chat history and speech styles to generate both the speaking style and text for the response. Subsequently, the TTS model synthesizes the speech, which is then played back to the user. While the response speech is being played, the input speech undergoes ASR processing to extract the transcription and speaking style, serving as the context for the ensuing dialogue turn. This novel pipeline accelerates the traditional cascade ASR-LLM-TTS systems while integrating rich paralinguistic information from input speech. Our experimental results show that StyleTalker significantly outperforms the conventional cascade and speech-to-speech baselines in terms of both dialogue naturalness and coherence while being nearly 2 times faster.
---

## DailyTalk Dataset

For a fair comparison to the baseline models, all audios are downsampled to 16k Hz. 

**All utterances are completely unseen during training, and the results are uncurated (NOT cherry-picked) unless otherwise specified**.


**Sample 1**

**Context:**


|              | Sample 1 (p294 → p326)
|:------------:|:-------:|:-------:|
|    **Context**    |    <audio controls="controls">  <source type="audio/wav" src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/demo/source/55.wav"></source> </audio>   |    <audio controls="controls">  <source type="audio/wav" src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/demo/source/76.wav"></source> </audio>  |
|    **AGAIN-VC**   |     <audio controls="controls">  <source type="audio/wav" src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/demo/againvc/55.wav"></source> </audio>    |     <audio controls="controls">  <source type="audio/wav" src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/demo/againvc/76.wav"></source> </audio>     |
|    **VQMIVC-VC**   |     <audio controls="controls">  <source type="audio/wav" src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/demo/vqmivc/55.wav"></source> </audio>    |     <audio controls="controls">  <source type="audio/wav" src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/demo/vqmivc/76.wav"></source> </audio>     |
| **YourTTS** |    <audio controls="controls">  <source type="audio/wav" src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/demo/yourtts/55.wav"></source> </audio>     |    <audio controls="controls">  <source type="audio/wav" src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/demo/yourtts/76.wav"></source> </audio>      |
| **StyleTTS-VC (Proposed)** |    <audio controls="controls">  <source type="audio/wav" src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/demo/stylettsvc/55.wav"></source> </audio>     |    <audio controls="controls">  <source type="audio/wav" src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/demo/stylettsvc/76.wav"></source> </audio>      |

