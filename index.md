# StyleTalker

The rapid advancement of large language models (LLMs) has significantly propelled the development of text-based chatbots, demonstrating their capability to engage in coherent and contextually relevant dialogues. However, extending these advancements to enable end-to-end speech-to-speech conversation bots remains a formidable challenge, primarily due to the extensive dataset and computational resources required. The conventional approach of cascading automatic speech recognition (ASR), LLM, and text-to-speech (TTS) models in a pipeline, while effective, suffers from unnatural prosody because it lacks direct interactions between the input audio and its transcribed text and the output audio. These systems are also limited by their inherent latency from the ASR process for real-time applications. This paper introduces StyleTalker, an innovative framework that fine-tunes an audio LLM alongside a style-based TTS model for fast spoken dialog generation. StyleTalker takes user input audio and uses transcribed chat history and speech styles to generate both the speaking style and text for the response. Subsequently, the TTS model synthesizes the speech, which is then played back to the user. While the response speech is being played, the input speech undergoes ASR processing to extract the transcription and speaking style, serving as the context for the ensuing dialogue turn. This novel pipeline accelerates the traditional cascade ASR-LLM-TTS systems while integrating rich paralinguistic information from input speech. Our experimental results show that StyleTalker significantly outperforms the conventional cascade and speech-to-speech baselines in terms of both dialogue naturalness and coherence while being nearly 2 times faster.

---

## DailyTalk Dataset

For a fair comparison to the baseline models, all audios are downsampled to 16k Hz. 

**All utterances are completely unseen during training, and the results are uncurated (NOT cherry-picked) unless otherwise specified**.


**Sample 1**


<table>
  <tbody><tr>
    <th>Context</th>
    <th>Next Turn</th>
  </tr>
  <tr>
    <td>
      <ul>
        <p>A: 'You're from New York, aren't you?'</p>
<p>B: 'Yes, that's right.'</p>
<p>A: 'What do you suggest I should see in New York?'</p>
          <audio controls="">
            <source src="">
              Your browser does not support the audio element.
          </audio>
      </ul>
    </td>
    <td>
      <ul>
        <li><b>Ground Truth: </b></li>
          <audio controls="">
            <source src="" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>SpeechGPT: </b></li>
          <audio controls="">
            <source src="" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>Cascade: </b></li>
          <audio controls="">
            <source src="" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>StyleTalker: </b></li>
          <audio controls="">
            <source src="" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
      </ul>
    </td>
  </tr>
</tbody></table>


