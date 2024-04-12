# StyleTalker

The rapid advancement of large language models (LLMs) has significantly propelled the development of text-based chatbots, demonstrating their capability to engage in coherent and contextually relevant dialogues. However, extending these advancements to enable end-to-end speech-to-speech conversation bots remains a formidable challenge, primarily due to the extensive dataset and computational resources required. The conventional approach of cascading automatic speech recognition (ASR), LLM, and text-to-speech (TTS) models in a pipeline, while effective, suffers from unnatural prosody because it lacks direct interactions between the input audio and its transcribed text and the output audio. These systems are also limited by their inherent latency from the ASR process for real-time applications. This paper introduces StyleTalker, an innovative framework that fine-tunes an audio LLM alongside a style-based TTS model for fast spoken dialog generation. StyleTalker takes user input audio and uses transcribed chat history and speech styles to generate both the speaking style and text for the response. Subsequently, the TTS model synthesizes the speech, which is then played back to the user. While the response speech is being played, the input speech undergoes ASR processing to extract the transcription and speaking style, serving as the context for the ensuing dialogue turn. This novel pipeline accelerates the traditional cascade ASR-LLM-TTS systems while integrating rich paralinguistic information from input speech. Our experimental results show that StyleTalker significantly outperforms the conventional cascade and speech-to-speech baselines in terms of both dialogue naturalness and coherence while being nearly 2 times faster.

---

## DailyTalk Dataset

For a fair comparison to the baseline models, all audios are downsampled to 16k Hz. 


**Sample 1**


<table>
  <tbody><tr>
    <th>Context</th>
    <th>Next Turn</th>
  </tr>
  <tr>
    <td>
      <ul>
<<<<<<< HEAD
        <p>A: 'Where does it go wrong?'</p>
<p>B: 'Let me stop my car for check. Oh, my god. I got a flat tyre.'</p>
<p>A: 'Can it keep going?'</p>
=======
        <p>A: 'Didn't you notice the roses everywhere?'</p>
<p>B: 'I hear it's Chinese Valentine's Day! Don't you know?'</p>
<p>A: 'Oh, God. I just forgot it. I should have brought roses for my boyfriend.'</p>
>>>>>>> c3507b28756e6abf3f3f4c0c2e26cb735e1fa743
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/context/3.wav">
              Your browser does not support the audio element.
          </audio>
      </ul>
    </td>
    <td>
      <ul>
        <li><b>Ground Truth: </b></li>
<<<<<<< HEAD
		<p>'Sorry. You'd better get off for taking another taxi.'</p>
=======
		<p>'It's not too late. Go to buy some now.'</p>
>>>>>>> c3507b28756e6abf3f3f4c0c2e26cb735e1fa743
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/gt/3.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>SpeechGPT: </b></li>
<<<<<<< HEAD
		<p>'No. It can't keep going.'</p>
=======
		<p>'Why haven't you had it? '</p>
>>>>>>> c3507b28756e6abf3f3f4c0c2e26cb735e1fa743
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/speechgpt/3.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>Cascade: </b></li>
<<<<<<< HEAD
		<p>'I think so.'</p>
=======
		<p>'I think you can use any flowers in place of roses.'</p>
>>>>>>> c3507b28756e6abf3f3f4c0c2e26cb735e1fa743
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/cascade/3.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>StyleTalker: </b></li>
<<<<<<< HEAD
		<p>'No, I think it's flat. I think I have a nail in it.'</p>
=======
		<p>'You can still get them today. But you have to hurry.'</p>
>>>>>>> c3507b28756e6abf3f3f4c0c2e26cb735e1fa743
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/styletalker/3.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
      </ul>
    </td>
  </tr>
</tbody></table>


**Sample 2**


<table>
  <tbody><tr>
    <th>Context</th>
    <th>Next Turn</th>
  </tr>
  <tr>
    <td>
      <ul>
        <p>A: 'I'll take two value meals.'</p>
<p>B: 'What kind of drink do you want with those?'</p>
<p>A: 'One Coke and the other a Sprite, please.'</p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/context/2.wav">
              Your browser does not support the audio element.
          </audio>
      </ul>
    </td>
    <td>
      <ul>
        <li><b>Ground Truth: </b></li>
		<p>'You can super-size your meal for only thirty nine cents extra.'</p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/gt/2.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>SpeechGPT: </b></li>
		<p>'Why you don't have anything else?'</p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/speechgpt/2.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>Cascade: </b></li>
		<p>'Here they are.'</p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/cascade/2.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>StyleTalker: </b></li>
		<p>'How do you want your burgers done?'</p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/styletalker/2.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
      </ul>
    </td>
  </tr>
</tbody></table>


**Sample 3**


<table>
  <tbody><tr>
    <th>Context</th>
    <th>Next Turn</th>
  </tr>
  <tr>
    <td>
      <ul>
        <p>A: 'Didn't you notice the roses everywhere?'</p>
<p>B: 'I hear it's Chinese Valentine's Day! Don't you know?'</p>
<p>A: 'Oh, God. I just forgot it. I should have brought roses for my boyfriend.'</p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/context/2.wav">
              Your browser does not support the audio element.
          </audio>
      </ul>
    </td>
    <td>
      <ul>
        <li><b>Ground Truth: </b></li>
		<p>'It's not too late. Go to buy some now.'</p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/gt/1.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>SpeechGPT: </b></li>
		<p>'Why haven't you had it?'</p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/speechgpt/1.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>Cascade: </b></li>
		<p>'I think you can use any flowers in place of roses.'</p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/cascade/1.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>StyleTalker: </b></li>
		<p>'You can still get them today. But you have to hurry.'</p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/styletalker/1.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
      </ul>
    </td>
  </tr>
</tbody></table>
