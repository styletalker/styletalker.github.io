# StyleTalker
---

## Abstract
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
		<p><i>You can super-size your meal for only thirty nine cents extra.</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/gt/2.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>SpeechGPT: </b></li>
		<p><i>Why you don't have anything else?</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/speechgpt/2.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>Cascade: </b></li>
		<p><i>Here they are.</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/cascade/2.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>StyleTalker: </b></li>
		<p><i>How do you want your burgers done?</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/styletalker/2.wav" type="audio/wav">
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
        <p>A: 'Where does it go wrong?'</p>
<p>B: 'Let me stop my car for check. Oh, my god. I got a flat tyre.'</p>
<p>A: 'Can it keep going?'</p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/context/3.wav">
              Your browser does not support the audio element.
          </audio>
      </ul>
    </td>
    <td>
      <ul>
        <li><b>Ground Truth: </b></li>
		<p><i>Sorry. You'd better get off for taking another taxi.</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/gt/3.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>SpeechGPT: </b></li>
		<p><i>No. It can't keep going.</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/speechgpt/3.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>Cascade: </b></li>
		<p><i>I think so.</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/cascade/3.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>StyleTalker: </b></li>
		<p><i>No, I think it's flat. I think I have a nail in it.</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/styletalker/3.wav" type="audio/wav">
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
        <p>A: 'Yes, I like using chopsticks.'</p>
<p>B: 'Do you like some soup?'</p>
<p>A: 'Yes, but I don't know what soup you have.'</p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/context/4.wav">
              Your browser does not support the audio element.
          </audio>
      </ul>
    </td>
    <td>
      <ul>
        <li><b>Ground Truth: </b></li>
		<p><i>Umm we have beef soup and tomato soup.</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/gt/4.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>SpeechGPT: </b></li>
		<p><i>I have tomato soup.</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/speechgpt/4.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>Cascade: </b></li>
		<p><i>Well, umm... We've got egg drop soup.</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/cascade/4.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>StyleTalker: </b></li>
		<p><i>I have roast beef soup.</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/styletalker/4.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
      </ul>
    </td>
  </tr>
</tbody></table>

**Sample 4**

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
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/context/1.wav">
              Your browser does not support the audio element.
          </audio>
      </ul>
    </td>
    <td>
      <ul>
        <li><b>Ground Truth: </b></li>
		<p><i>It's not too late. Go to buy some now.</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/gt/1.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>SpeechGPT: </b></li>
		<p><i>Why haven't you had it?</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/speechgpt/1.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>Cascade: </b></li>
		<p><i>I think you can use any flowers in place of roses.</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/cascade/1.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>StyleTalker: </b></li>
		<p><i>You can still get them today. But you have to hurry.</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/dailytalk/styletalker/1.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
      </ul>
    </td>
  </tr>
</tbody></table>

---
## PodcastFillers Dataset

**Sample 1**

<table>
  <tbody><tr>
    <th>Context</th>
    <th>Next Turn</th>
  </tr>
  <tr>
    <td>
      <ul>
<p>A: 'You know, it teaches yourself. You just install it and you magically. know how to use it, but it's better to have a guide. How else, what, where else can the good people who are listening to this show or watching it on YouTube connect with you? and connect with you and, and learn more about how you can help them.'</p>
<p>B: 'So I'm actually gonna take the opposite approach. Considering I do have, like, the podcast and YouTube channel. No, I'll, I'll take the opposite approach and just point people to the hump bitch. I think I do a pretty good job at like siloing people off into kinda what they wanna learn more about or listen to or that sort of stuff, so. DoomBlow.com, man.'</p>
<p>A: 'That's awesome. Well, Pete, thank you for coming on the show. I feel like I could have Joe Rogan'd on you and gone for three hours, but thank you for, uh, sharing an hour of your time with us here, and I hope you have a great rest of your day, and we'll see you around the interwebs.'</p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/podcast/context/2.wav">
              Your browser does not support the audio element.
          </audio>
      </ul>
    </td>
    <td>
      <ul>
        <li><b>Ground Truth: </b></li>
		<p><i>Yeah, thank you, Chris. I really do appreciate it. And I also, I, I, I didn't tell you this. Yeah, but I also appreciate- ... your product and everything that you guys work on. It's been extremely helpful. as a creator. So thanks for having me on. I appreciate it.</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/podcast/gt/2.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>Cascade: </b></li>
		<p><i>Thanks for having me.</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/podcast/cascade/2.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>StyleTalker: </b></li>
		<p><i>You know, I appreciate you saying that. I mean, you know, like, I don't know if I'm gonna be doing this for another 10 years or whatever, but I, I really enjoy doing it and I really enjoy the feedback that I get from people. So, you know, if I'm doing it, I'm doing it. And if I'm not doing it, I'm not doing it. But, you know, I'm gonna do it for as long as I can.</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/podcast/styletalker/2.wav" type="audio/wav">
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
<p>A: 'Nicely done. You can't go wrong with an answer. Number two, you mentioned that you have a cat and a dog before. One, what are their names?'</p>
<p>B: 'Uh, the cat is Adelina. The dog is Meriwether.'</p>
<p>A: 'That's incredible. I just love animals, as you can tell. Um, what- What is the- ... or most mischievous thing they've got up to in your house during isolation.'</p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/podcast/context/4.wav">
              Your browser does not support the audio element.
          </audio>
      </ul>
    </td>
    <td>
      <ul>
        <li><b>Ground Truth: </b></li>
		<p><i>Oh my goodness. Um, she is truly the kindest animal I've ever met, and there is not a mischievous bone in her body. So she's done nothing but be a precious dog. Um, the cat, the cat will kill you in your sleep if you're not careful, and she's definitely mischievous.</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/podcast/gt/4.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>Cascade: </b></li>
		<p><i>Well, I think the whole time for them has been kind of entertaining to me because, uh... Uh, my husband works from home and he was in the office all week, so it was just me with the cats and the dogs and having this 90-day challenge of trying to cook everything from scratch.</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/podcast/cascade/4.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>StyleTalker: </b></li>
		<p><i>Oh, my goodness. I mean, it's been a whole new world of, of, of things. Um, but I would say the most mischievous thing they've done, I think, is that they've learned how to get into the trash. So, um, they've been getting into the trash, um, at night. And they, they leave their little paw prints all over the trash and they pull things out and, um-</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/podcast/styletalker/4.wav" type="audio/wav">
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
<p>A: 'Right, and it's, it's largely based on, you know, the last 40 or 50 years, like, what just sort of caught on.'</p>
<p>B: 'A lot of it is very arbitrary. Even- Even the design, and this is, this scares some people. I don't know why. Even the design of- ... architectures, right? We're using the von Neumann architecture sometimes, right, where you have the same data bus. for instructions and for data, but it didn't have to go that way either. You could have had a different way for the computer to have been architected.'</p>
<p>A: 'Well, I mean, uh ...'</p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/podcast/context/1.wav">
              Your browser does not support the audio element.
          </audio>
      </ul>
    </td>
    <td>
      <ul>
        <li><b>Ground Truth: </b></li>
		<p><i>We're not advocating for you to know how to design your own computer, even though that's part of- That's a course I wanna have. But you don't have to. It's, it's almost, it's just that you're aware of it. And you understand that you don't have to be scared, that you don't have to follow these things as if it was science. human made decisions to sort of deal with computers in a way that helped that person's psychology or help that person's.</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/podcast/gt/1.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>Cascade: </b></li>
		<p><i>And we could've done it in many other ways as well.</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/podcast/cascade/1.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>StyleTalker: </b></li>
		<p><i>Right, so, you know, it's, it's just the way that people have designed it. And, and so, you know, we can imagine, like, the, the, the, the kind of, you know, the idea of the Von Neumann architecture. ... that's just a particular way of, of doing things, and we can imagine different ways of doing things.</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/podcast/styletalker/1.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
      </ul>
    </td>
  </tr>
</tbody></table>



**Sample 4**

<table>
  <tbody><tr>
    <th>Context</th>
    <th>Next Turn</th>
  </tr>
  <tr>
    <td>
      <ul>
<p>A: 'It makes me feel really old, but I'm like, "How do I do this?"'</p>
<p>B: 'I just have too many apps. I'm trying to live that minimal life.'</p>
<p>A: 'With every end of every interview. I just threw a few quick popcorn questions. Um- Normally they're questions that a fan might have for you. ... questions that I have off the top of my head that I'm just curious about that have no context. My first one is... Uh, if you could perform with any musician living or dead, who would it be and why?'</p>

          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/podcast/context/3.wav">
              Your browser does not support the audio element.
          </audio>
      </ul>
    </td>
    <td>
      <ul>
        <li><b>Ground Truth: </b></li>
		<p><i>Stevie Wonder. because he has been probably my greatest musical inspiration.</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/podcast/gt/3.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>Cascade: </b></li>
		<p><i>Um, when I was younger, not when I was young. Um- Was in high school. And basically wanted to be a singer. She's always been someone that's like so very talented.</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/podcast/cascade/3.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
        <li><b>StyleTalker: </b></li>
		<p><i>I'm not gonna say the name, but it's someone I'm pretty close to.</i></p>
          <audio controls="">
            <source src="https://raw.githubusercontent.com/styletalker/styletalker.github.io/main/wav/podcast/styletalker/3.wav" type="audio/wav">
              Your browser does not support the audio element.
          </audio>
      </ul>
    </td>
  </tr>
</tbody></table>
