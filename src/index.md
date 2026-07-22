---
layout: layout.njk
title: GROUP CHAT PHASE
---

<div class="hero-overlay">
  <img src="{{ '/images/window_transparent.png' | url }}" class="window-intro-img window-intro-img-left" alt="Gothic window illustration">
  <img src="{{ '/images/window_transparent.png' | url }}" class="window-intro-img window-intro-img-right" alt="Gothic window illustration">
</div>

<div class="hero-wrapper">
  <section class="hero">
    <h1>VICE BREAK:</h1>
    <p class="subheader">an addictionary</p>
  </section>
</div>

<section class="figure-section">
  <img src="{{ '/images/drawing_transparent.png' | url }}" alt="Illustrated figure" class="title-figure">
</section>

<section class="figure-section">
  <img src="{{ '/images/drawing2_transparent.png' | url }}" alt="Illustrated figure" class="title-figure">
</section>

<section class="anim-test" id="test1">
  <p class="anim-test-label">TEST 1 — SCROLL SCRUB</p>
  <div class="scroll-anim-wrapper" id="scrollAnimWrapper">
    <canvas id="scrollAnimCanvas" class="scroll-anim-canvas"></canvas>
  </div>
</section>

<section class="anim-test" id="test2">
  <p class="anim-test-label">TEST 2 — AUTOPLAY</p>
  <div class="autoplay-anim-wrapper">
    <img id="autoplayAnimFrame" class="autoplay-anim-frame" src="{{ '/images/monk_animation_test_1.png' | url }}" alt="Animated figure, frame 1">
  </div>
</section>

<script>
(function () {
  // Shared frame list, numerical order 1 → 3
  const framePaths = [
    "{{ '/images/monk_animation_test_1.png' | url }}",
    "{{ '/images/monk_animation_test_2.png' | url }}",
    "{{ '/images/monk_animation_test_3.png' | url }}"
  ];

  const frames = framePaths.map(src => {
    const img = new Image();
    img.src = src;
    return img;
  });

  /* ---------- TEST 1: SCROLL SCRUB (canvas) ---------- */
  const wrapper = document.getElementById('scrollAnimWrapper');
  const canvas = document.getElementById('scrollAnimCanvas');
  const ctx = canvas.getContext('2d');

  function resizeCanvas() {
    canvas.width = canvas.clientWidth * window.devicePixelRatio;
    canvas.height = canvas.clientHeight * window.devicePixelRatio;
  }

  function drawFrame(index) {
    const img = frames[index];
    if (!img.complete || img.naturalWidth === 0) return;
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    // contain-fit, centered — preserves transparency, no cropping
    const canvasRatio = canvas.width / canvas.height;
    const imgRatio = img.naturalWidth / img.naturalHeight;
    let drawW, drawH;
    if (imgRatio > canvasRatio) {
      drawW = canvas.width;
      drawH = drawW / imgRatio;
    } else {
      drawH = canvas.height;
      drawW = drawH * imgRatio;
    }
    ctx.drawImage(img, (canvas.width - drawW) / 2, (canvas.height - drawH) / 2, drawW, drawH);
  }

  function updateScrollFrame() {
    const rect = wrapper.getBoundingClientRect();
    const scrollDistance = wrapper.offsetHeight - window.innerHeight;
    const progress = Math.min(1, Math.max(0, -rect.top / scrollDistance));
    const frameIndex = Math.min(frames.length - 1, Math.floor(progress * frames.length));
    drawFrame(frameIndex);
  }

  window.addEventListener('resize', () => { resizeCanvas(); updateScrollFrame(); });
  window.addEventListener('scroll', updateScrollFrame, { passive: true });
  resizeCanvas();
  frames[0].onload = () => drawFrame(0);

  /* ---------- TEST 2: AUTOPLAY (IntersectionObserver + interval) ---------- */
  const autoplayImg = document.getElementById('autoplayAnimFrame');
  const autoplayWrapper = autoplayImg.closest('.autoplay-anim-wrapper');
  let autoplayIndex = 0;
  let autoplayTimer = null;
  const frameDuration = 200; // ms per frame — tune pacing here

  function playNextFrame() {
    autoplayIndex = (autoplayIndex + 1) % frames.length;
    autoplayImg.src = framePaths[autoplayIndex];
  }

  const autoplayObserver = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting && !autoplayTimer) {
        autoplayTimer = setInterval(playNextFrame, frameDuration);
      } else if (!entry.isIntersecting && autoplayTimer) {
        clearInterval(autoplayTimer);
        autoplayTimer = null;
      }
    });
  }, { threshold: 0.3 });

  autoplayObserver.observe(autoplayWrapper);
})();
</script>

<div class="editorial-wrapper">
  <section class="editorial-note">
    <h2>Note from<br>the Editors</h2>
    <p>Metrose first came to life as a physical photography exhibit, showcased at the Ecole Normale Supérieure in Paris in November 2024. A clear issue arose. The beast couldn't travel. No planes, trains, or automobiles could carry Metrose to Poland, Puebla, or any of the other places it needed its presence felt. As such, your editors decided that Metrose would need to be transmuted, freed from its Fujicolor Cristal Archive Paper Supreme-shaped chains, and sent forth to a new plane of existence. Like Frankenstein's monster, Metrose rose from the wicked experiment with a new face: Metrose Digital, a bigger, stronger, more lethal case of Metrose, filled with new features and breaking through the boundaries of the purely visual. The beast now hops from device to device, cast in and out of life. We have tamed it for your pleasure. It's waiting for you, sitting patiently in the pixels of your display. Scroll and it will be yours. <br><br>Yours truly,<br><br>Adelfo, Leopold, and Rémi.<br><br>PS: While using your phone is alright, we recommend using a desktop browser for the best experience. </p>
</section>
 <section class="table-of-contents">
    <h2>Contents</h2>
    <ul>
      <li><a href="#photography">Photography</a></li>
      <li><a href="#writing">Writing</a></li>
    </ul>
  </section>
</div>

<section class="grid-section" id="photography">
<div class="product-card">
</div> 
<div class="product-card">
</div>
<div class="product-card full-width">
</div>
<div class="product-card">
</div>
<div class="product-card">
</div>
<div class="product-card full-width">
</div>
<div class="product-card">
</div>
<div class="product-card">
</div>
<div class="product-card full-width">
</div>
<div class="product-card full-width">
</div>
<div class="product-card full-width">
</div>
<div class="product-card">
</div>
<div class="product-card">
</div>
<div class="product-card full-width">
</div>
<div class="product-card full-width">
</div>
<div class="product-card full-width">
</div>
<div class="product-card">
</div>
<div class="product-card">
</div>
<div class="product-card full-width">
</div>
<div class="product-card full-width">
</div>
<div class="product-card">
</div>
<div class="product-card">
</div>
<div class="product-card">
</div>
<div class="product-card">
</div>
<div class="product-card full-width">
</div>
<div class="product-card full-width">
</div>
<div class="product-card full-width">
</div>
<div class="product-card">
</div>
<div class="product-card">
</div>
<div class="product-card">
</div>
<div class="product-card">
</div>
<div class="product-card full-width">
</div>
<div class="product-card">
</div>
<div class="product-card">
</div>
<div class="product-card full-width">
</div>
<div class="product-card">
</div>
<div class="product-card">
</div>
<div class="product-card full-width">
</div>
<div class="product-card full-width">
</div>
<div class="product-card">
</div>
<div class="product-card">
</div>
<div class="product-card full-width">
</div>
<div class="product-card">
</div>
<div class="product-card">
</div>
<div class="product-card">
</div>
<div class="product-card">
</div>
<div class="product-card">
</div>
<div class="product-card">
</div>
<div class="product-card">
</div>
<div class="product-card">
</div>
<div class="product-card">
</div>
  <div class="product-card">
</div>
<div class="product-card full-width">
</div>
</section>

<section class="story-section" id="writing">
  <div class="story-text">
    <h2>METROSIS</h2>
I'm sitting on the train. Around me, people are standing, hanging on to slick, metal bars. I'm one of the lucky ones. I get on early enough to always have a spot where I can sit my ass down. Not that it really needs the sitting down; not that it really doesn't need it either. It's probably in a permanent state of hibernation from sitting down so much, like a bear that found its way into a meatpacking factory. So cold, but so much food. The food, in my case, being chairs to sit down – and seats of other kinds. And the cold being… well, also chairs? Anyway, whatever. The point is, I don't have to stand up. And on top of that, I would be at face level – and mouth level – with other people, meaning I would get the five different scents of slopbowl swimming their way into my nostrils for the entire ride. Ah, this guy had Chipotle. Rice bowl, no tortilla. Extra protein. Better muscles, worse kidneys. Next, Cava. The za'atar really comes through. He probably likes traveling. And the others, well, the others don't have a smell, because I'm seated. A little bit of armpit, though, I guess. I don't have to avoid eye contact as much, as well. That's a pretty big one. When it's too crowded and I'm standing there isn't enough space for me to hold my phone without stabbing into another person's flesh, so scrolling is off limits. So I've got to find a faceless spot to rest my eyes on. And there are so many faces, it's hard not to look. To find somebody. To imagine. Seated, less of that. But in the rare event that there's a really tall guy in front of me, and a child, or a person with a really short torso maybe, sitting across, then it's bad. Because the second guy's little eyes peek just under the tall guy's crotch, and I'm going to make eye contact, I always do. So now the tall guy thinks I'm staring point blank at his junk. Luckily though, this kind of configuration is quite rare. And I can look down at my phone's OLED display. Great colors. Even better contrast, really dark blacks.

I'm pretty well acquainted with it since I unlock my phone 273 times a day, on average, according to the screen time app. I open Instagram. I'm checking stories. I've already seen most of them, multiple times even, but that's fine, only I know that. Picture of a guy I know from somewhere, at a party. Today's Tuesday, so it's a late weekend post, maybe. He was hesitant. Picture's fine though. I mean, nothing special. White button down, only one open button. Conservative, giving *After work*. Looks like a pretty standard club as well. Toothless smile, with the boys. Risk-free, overall. Next. A puppy. Boring normie shit. A dachshund, as well. Who in this city between the ages of 26 and 38 doesn't own a dachshund? The dog of the millenial. And the… zillenial? Bad name. Fence sitters. We don't need any more of those. Like the dachshunds. Or no, even worse, French bulldogs. Those things can't even breathe. Like me when I talk to a woman. I chuckle to myself. Now the guy next to me, his eye sitting in the corner of its viscous little socket, ready to catch a nosy glimpse of what the fuss is all about. Not that a chuckle is much of a fuss, but these days that's all it takes for a little investigative peek, to turn people into Scooby Doo. The thing is, since I'm looking at the dachshund, the guy will think I'm chuckling at the dog, which is pretty normal. Not a bad outcome, all things considered.

The train slows and the loathsome screech of the braking wheels is registered somewhere along the pink channels of my brain. I look up, crane my neck past the guy in front of me, squirm to the side, emit a little 'sorry'. Delancey-Essex, my stop. I try to get myself on my feet with minimal pelvic contact, not easy. Quads are pretty shaky, need to work on that in the gym. It's not for the aesthetics, it's for being able to stand up in the train. I slither through the sweaty bodies politely trying to make some space. They don't want to touch me more than I want to touch them. I straddle the gap. The train beeps furiously, the doors thrust into each other, I'm out. I'm pushed out, by another passenger trying to make it out of the death cage. I turn around, and a girl is breathing deeply, checking her pockets as the train accelerates away into the tunnel. She's got a black, messy bob, framing her eyes that are green, almost gray, but still distinctly, recognizably green, like oxidizing bronze.

"Sorry, I-"

"Don't worry about it, I had to push my way through anyway."

A drop of water or some other unspeakable liquid, marinating the entrails of the city, falls from the ceiling onto my bare hand. I brush it off, and as I look up she has begun walking away, hurried, towards the stairs leading out the station.

  </div>

  <!-- PHOTO INTERLUDE -->
  <div class="story-interlude">
    <div class="product-card">
</div>
  </div>

  <div class="story-text">

I'm doing groceries, and what do I see before me? A little Frenchie. Well, I say that I see it – that's because a moment ago I almost connected my chucks with its misshapen cranium in a manner that would've sent the poor thing past the keeper and straight into top bins. He would've never seen it coming, and since it never came, it's like it nothing ever happened. What a goofball. And I was just thinking about them.

I'm in the produce aisle. Bananas. Peaches. I'm feeling kind of overwhelmed by all the colors in the aisle. The apples are huge, way too big a size for a self-respecting apple, and so green, so red, so red. Cosmic Crisp apples. Round, like a planet. Smooth, so red, a soft smooth red just barely specked with whitish golden stars. I'm deep inside the apple now, I've traveled far inside its fresh, crisp cosmos, I'm like a spaceship, beaming through the redness. It's changing now, shifting, here bright, there dark, like a tunnel of apples, a tunnel through a cosmic crisp, through its little ass thing at the bottom of the apple and into the stem, not red now, but brown, and I come out the stem, I see the white ceiling, the Hawaiian shirts of the smiling employees, and I'm back.

I got these new glasses. They've got quite a thick frame. Not super thick, but still noticeably thicker than regular glasses. They're Meta Ray-Bans, so like a regular wayfarer, but with Meta's llama AI living inside the frame. And, and speakers, and a microphone, and a camera that can film in 3K Ultra HD for up to 8 hours. Crazy that they can fit so much in there. I haven't turned them on yet. So for the time being they're just regular glasses. If I'm on the train and a guy accuses me of looking at his crotch I'll be able to say "Wait, look! I've got the footage! I wasn't looking!" Unless my head was facing his crotch in which case the camera will just show them their privates, which wouldn't be a good look. I would need a camera facing my eyes, maybe, to show them that yes, my glasses seem to indicate that I was looking at the payload, but now if you check my eyes, you'll see that they were in fact looking elsewhere! Not guilty. Maybe a like-minded engineer will think about adding that feature for the next generation. I'll have to make do with forward facing footage for the time being.

"Hi, how are you doing today?"

"Hi, um, well, I'm pretty good, thanks. How about you?"

"Oh me? not too well, I'll be honest."

"Oh…"

"Yeah, rough day."

"Oh yeah. Those suck."

"Hey at least it's Friday, am I right? Almost over."

"Oh yeah, right. Friday, almost over. Right"

Beeping, more beeping. Paper bags, doubled for extra durability, squelching as they're filled.

"Wow, you're a real big fan of apples, huh?"

I look at the counter and see a pile of five bags, sitting there.

"These… cosmic crisps, huh? I can tell you like them extra crispy!"

"Oh you can? Uh, nice thanks!" A few seconds pass. "It's cause I'm gonna make pie. Apple pie."

"Well you can sure make a lot of pies with all these apples! You having people over?"

"Uh, yeah… yeah! Totally, I'm having people over… this weekend. Which is why I'm buying all these apples now."

"Sweet! Can I come?"

"Can you come? Oh… my apartment's really small, so–"

"Chill, it's fine, I'm messing with you, don't worry about it! Besides, all these apples but nothing to drink? I don't know what kind of party you're gonna be having in your small little apartment!"

"Right, no drinks, that's because… someone…"

"Relax, I'm messing with you again! I like to joke around. Like I said, bad day. Gotta brighten it up somehow, right? Anyway, will you be paying by cash or card tonight?"

"Cash. Wait, no. Card, please."

I double click my phone's home button. The OLED display does a really good job capturing the deep blue gradient on my virtual Chase Sapphire Preferred card. It's so convenient, and the little haptic vibration when the RFID connects with the payment terminal– boy, does that feel good. The social tension leaves my body, dispersing into the air of the store. As does my money.

Outside, the air hurries down the asphalt and bites at my bare cheeks, playfully, like an excited pup. I turn left and begin walking home, the handles of my bag digging into my knuckles. I should've asked for another. Thankfully, the double bags make it so the groceries won't splatter gracelessly onto the pavement, sharing a warm embrace with the rat shit and needles and other filth laying around. My phone vibrates. I stop walking, shove my hand into my pocket, and pull it out. My Meta Ray-Bans have disconnected for some reason. I look around, and to my left I see a courtyard, surrounded by three dark, brick towers slicing upwards into the sky, and in the yard a council of trees, their leaves freshly sprouted and babbling in the wind, murmuring in concert, and to the side a smaller, younger tree, its leaves a cold, fresh pink against the warmer, deeper red of the bricks, its leaves shaking, the bricks standing unswayed, the council whispering through the green leaves, the pink tree alone, to the side. In the square, amid the trees, a large puddle of water, square too, around little fountain sprouts that must be used to create a mist for the kids from the towers during the day, the puddle now eating the colors of the lit windows above and spitting them back out, lights white and yellow hanging stiffly in the darkness like a clothesline somehow untouched by the wind. Around the puddle, a few benches, and on a bench a person, a woman, young, reading perhaps. My eyes are drawn back down to my phone and I reconnect my glasses and keep on walking home.

  </div>

  <!-- PHOTO INTERLUDE -->
  <div class="story-interlude">
    <div class="product-card">
</div>
  </div>

  <div class="story-text">

I haven't really had the chance to try out these glasses so I decided I'm going to show them my groceries.

"Alright, let's see… is this thing on?"

No answer. I check the app on my phone and it's telling me to say 'Hey Meta'.

"Hey Meta,"

"Hi David, how can I help you today?"

"I – well, I just did my groceries."

"Nice! What did you buy? A nice balance of ingredients, I hope! What could I help you with? Do you need ideas for your next recipe? Or maybe tips for a well organized pantry? If you turn on your camera and show me, I can give you advice that's tailored to your kitchen."

"No I just wanted to show… uh, show you what I got. To, like, try you out, I guess?"

"Oh, just to try me–"

"I know that sounds weird,"

"No, no! Feel free to try out all my different functionalities! And if you have any questions about what I can do, ask whenever! But back to your groceries. What do you have to show me?"

"So, uh, I got these,"

"If you want to show me your groceries visually make sure to turn on your camera first, that way I can have an idea of what it is,"

"Oh yeah. How do I do that again?"

"Just press and hold the button on your right temple. That'll turn on the camera and start recording."

I followed the orders and the specter inside the glasses let out a sophisticated beep.

"Right, ok. I think it should be working now."

"Yes, perfect! I can see your counter right now. It must be your kitchen counter. I don't see any groceries though."

I pull the paper bag out from below the counter and begin plumbing its depths.

"Alright, I can see what must be your grocery bag now. And it looks like you brought out an 8 ounce stick of Kerrygold Pure Irish Butter, and, let me see… it looks like it's the salted version! Looking good! What do you think you're gonna be making with that? Any recipes in mind?"

"Uh…" It had somehow escaped my mind that I might have to give answers.

"Yeah-no-you know what, do you think you could avoid asking questions? Or, like, just react without asking questions afterwards?"

"Oh sure! You want me to stop asking questions about the products you're showing me. I'll refrain from those kinds of interrogations from now on."

"Ok, nice."

I'm flashing back to the food hauls I would watch on YouTube around 2012. Overly cheerful Americans trying out snacks sent from foreign fans; awkward Brits tasting TimTams for the first time. They didn't have to answer any questions.

"Alright, what's next? I'm seeing a box… of what seems to be Trader Joe's Light Cream Cheese. You're a fan of dairy it seems! And you went for the more healthy option choosing the light over the full-fat version! Definitely the right move, especially since you've already bought the butter."

Food hauls are a relic of our hunter gatherer past. Going to the supermarket to buy mass produced food is the modern equivalent of neolithic berry-picking. Brightly covered packaging activates deep-seated epigenetic reactions to the colors of berries in the wild. Picking was done by women, doing groceries is inherently feminine. They would show what they gathered to the tribe's alpha. I guess that would make my RayBan Metas my alpha. Where did I read all this? I probably didn't read it, heard it maybe. Can't remember. Joe Rogan, probably. Bro science.

"And here we have a bag of apples! Cosmic Crisp apples, to be more specific! Cosmic Crisps are a cross between the Honeycrisp and Enterprise apples. They're one of America's favorites, and easily found at Trader Joe's!"

I wonder how my neolithic ancestors would react upon tasting one of these apples.

"Another bag of Cosmic Crisp apples! You must be a big fan! I can definitely see why you would enjoy a fresh, crisp apple after some of that cream cheese you showed me earlier."

They wouldn't even need to taste them, just seem them. So big and round and red.

"Another bag! Wow! Be sure not to eat too many at once though. Apples contain a lot of fiber, and while it's great you're taking in a lot of an essential nutrient, excessive fiber intake can have unintended side effects like–"

I'm looking out the window now, apples in hand. The glasses are still talking, I'm not really listening anymore though. Outside the trees in the yard are swaying a little in the wind, not violently, no, rather like they enjoy it, like a dog sticking its head out of a car window. Maybe I should go berry picking this weekend. Black bob.

  </div>

  <!-- PHOTO INTERLUDE -->
  <div class="story-interlude">
    <div class="product-card">
</div>
  </div>

  <div class="story-text">


I didn't go berry picking. The tall steel frames of the buildings overhead are severed by the mouth of the train station as the escalator draws me inward to the warm core of the earth.

I've been a bad boy this week. I've managed to download facial recognition software into my glasses. I found it on a nebulous subreddit, and got it off a GitHub repository. I'm not sure why I did, though. I like imagining what people's lives are like. I see their face. I see their body, how it moves. If I'm lucky, I listen in on a conversation. But that's cheating kind of. And I put the pieces together. Maybe she's an accountant, kids, in her 40s, looking for a new house, out of the city. I'm just nosy, I guess. And what I'm doing now, now that I think about it, is outsourcing that, my imagination, to my glasses. A loss maybe. But truth – that truth is worth it. The train grumbles loudly as it crashes along the tracks and into the station. I hop in and take a seat, there aren't too many people yet. I don't want everybody in the train to know I'm using the glasses, so instead of speaking to it, I open the app and type.

"Hi," The agent springs to life and the words are beamed from the phone into my glasses' speakers.

"Good afternoon David, how are you?"

I type in my response. "I'm doing fine. I'm in the train, on my way back from work."

"I hope your day at work wasn't too exhausting. Luckily for you, we're getting close to the end of the week."

"Yeah, I guess. I'm not too tired anyway. I sit at a desk all day."

"That may be true, but while you may not feel physically tired, mentally and emotionally an office job can still get to you!"

The train lurches to a halt, having already found its way to the next station. A gaggle of bodies smashes its way through the doors. A wonderful opportunity for some field testing. I navigate to the facial recognition app and start it up. It connects to my glasses, and, using the camera, it produces a live feed, detailing any information available online that connects to the faces. Populated all of a sudden with fleets and fleets of ships, their holds carrying troves of facts, photos, tweets, posts, names, names, and more names. What was once a phantom array of supposed professions haunting my mind had now been morphed, solidified, into cold, hard biographies. The steel wheels squeal as they're clenched by the brakes, the doors slide forcefully, and the floodgates break open. The faces pour in from the 23rd street station. A 23 year old man, also called David, just got a job at some kind of digital business news outlet. He produces fun YouTube explainers of business stories, probably. The job is celebrated in a LinkedIn post. Behind him, an artist in her 50s. VERY avid Facebook user. She keeps reposting Bernie Sanders shorts. She has probably been blessed with a rent controlled apartment in Chelsea that she's been living in for 30 years. Her name is Deborah. Only names starting with D. Strange. The train's moving again. This Deborah decided to take a seat next to me, so now I've got to lay low. She probably can't recognize the glasses, luckily. Still, I turn off my phone's display for a few moments, and look around. The faces are silent, their translator gone. My left knee's shaking rhythmically off the ball of my foot, jolting up and down, pausing, jolting again, pausing again.

Next stop, 14th street. Suits bustle in from nearby office buildings. Deborah hasn't budged. Suddenly, I remember that I can have the feed mashed into an AI summary and fed directly into my ears. I bring my phone back out of my pocket and keep the screen up close to my face to prevent any unwanted attention. I think my screen may be visible in the glass to the people seated across but I doubt anything's legible that way. Low risk. A few moments navigating the UI and there you go, it's all set. I'll just have to choose which face I want summarized.

"Cassandra, 37 years old. According to her LinkedIn profile, she is a junior partner at KWH Law Firm. She became a partner 3 years ago. The information found on the firm's website says the same. She's no longer active on Facebook, and rarely posts on Instagram. Her latest post was at a friend of hers' wedding. Before that, she posted a picture with another friend at a concert of the metal band Tool. It seems that she has often attended metal concerts, and plays the drums herself. She has met Danny Carey, the drummer from Tool. She seems to be particularly fond of that moment. It was on the day of her 37th birthday. It has been 11 months, so her next birthday should be coming up soon."

Metal would never have made the cut in my imaginary profile. I guess I'm not creative enough to have KWH law fit with Tool concerts. I'm bound by stereotypes. Maybe this whole experiment will make me more open-minded.

The train leaves the station again. In front of me, a large white bag made of a sort of thick satin paper, waving a huge Macy's logo in front of my eyes, like a pendulum swinging from the hand of a hypnotist. I quickly glance at the carrier, just long enough for the camera to pick up their face.

"Silvia Gonzalez has been visiting New York City for the past 5 days. She flew into Newark airport last Thursday where her brother Daniel picked her up. She lives in Cartagena, Colombia. She's a medical student there. Her brother has been living in New York City for 3 years, working as an architect." She was probably at the Macy's at Herald Square, on 34th street. Maybe she went to visit the Empire State Building as well. She's alone because her brother has probably done that kind of touristy thing before. I check her Instagram, which the app easily found. Her profile's public. A story posted today, at the top of the Empire State Building. Bingo. There are a lot of photos here. I'm trying to glean information but it's too time consuming. I open the app instead and navigate to the chat-bot.

"Is she in a relationship?"

"Her recent Instagram posts suggest that she currently is not, although she may have been as of 3 months ago."

Not that I'm interested! No, that would be weirdo behavior. I'm just curious. She's not staying in the city long anyway.

Again the doors open, again a squall of new faces to recognize. I'm looking at the door, looking at the fresh people, making sure the camera picks them up. Then, suddenly, a face I recognize. Or, that I recognize, not the glasses. It's the same girl as last week. She shuffles into the people huddled around the central pole, each clutching a small section, their hands sliding as she moves in and one collides with the hand below and a jumble of discomfort and a whispered sorry and she's gone, behind those people. I check my phone and the glasses didn't even get the chance to see her face. My Adam's apple jitters as I swallow nervously and stir in my seat, trying to find a more suitable vantage point to see where she may have gone. My shoulder rubs a bit too hard against Deborah's and her head turns and glances disdainfully and I try to stop the fidgeting and squirming and I wait. A new arrival of people but not enough have moved so she's still hidden somewhere in the thickets of bodies. My phone vibrates, the screen lights up. My glasses are low on battery. I didn't charge them last night. I forget about my neighbor and start fidgeting again. A horde of students come in from West 4th street. Through the shuffle, I make out her face, from the side, for a moment. I check my phone's screen to see if maybe the glasses picked her up but no, no luck. The train rumbles onward, unchanged by the masses in its bosom. The people stay hanging onto the thick steel poles that weave across the train in straight lines, their hands clutching a phone, their ears filled with pearly white Airpods, or black earphones of a different brand that are black as unswept chimneys, black as a void shimmering where the six figure salary should be instead. Or the rich parents. The train stops again.

The next door down the crowd starts shifting, scattering further down the train. As the people retreat, I see the culprit. A homeless guy fentposing right by the door, his body lurched forward, hands hanging down like they're trying to touch the floor. By the way the well-to-do folk move away, I can tell this guy absolutely reeks. Like Chernobyl nuclear cloud levels of reekage. Noses contorted, lips pursed, discomfort trying to be hidden away in the deepest crevices of the face for fear the crackhead might notice and crash out (he probably can't), but it keeps surging back to the surface, like a dolphin dancing in the spume of a ship. Then, in the grand opening torn into existence by the crackhead like an underground Moses, there she is. She's sitting now, looking down at her phone, undaunted. She looks up at the homeless guy for a few moments, before placing her head in her palm peering once again into the screen. I look at my phone and there she is. I press her face, just the black bob, no green eyes this time.

"Amina Taylor graduated from Hanover High School in 2018. Her celebrating with her friends was her last Instagram post. Before then, she would regularly attend basketball camp in Maine."

"That's it?"

Deborah looks over reproachfully and I look back and she's back on her phone already so I check mine to see what's written about Amina in the app, in the hopes that there's more, but no. No LinkedIn even. The saturated train speakers blare out "Delancey-Essex" and the doors are already open and so I stuff my phone into my pocket and grab my backpack and my glasses fall and almost crash against the floor but I snatch them mid air and I'm out of the train. The doors close, and I check to my left and to my right to see if she's on the platform but no, she's still on the train this time, thundering away towards the Williamsburg bridge.

  </div>

  <!-- PHOTO INTERLUDE -->
  <div class="story-interlude">
    <div class="product-card">
</div>
  </div>

  <div class="story-text">


"What exactly do you want me to do? I'm not sure I understand."

"I want you to, uh, impersonate, or no, play the role of a 25 year old girl called Amina who grew up in Hanover, New Hampshire, and just graduated Bard College. She lives in New York City now." I manually checked her tagged posts on Instagram and it seems like she spent the last few years at Bard. I'm surprised the facial recognition thing didn't pick that up.

"Okay. I think I have a better idea of what you want me to do now. I have to ask, though, is this Amina a real person? If she is, I'm afraid I can't do the roleplay you're asking for – it would constitute a breach of my privacy and ethics guidelines."

"Oh, no no, she's, uh… a fictional character… that I invented."

"Alright! In that case, we can continue with the roleplay! I'll let you begin, and I'll respond in character."

"Okay, sounds good. So, uh… Hi,"

"Hey, what's up?"

"Uhhh… not much. Just, wait, to be clear, we would be meeting in a train or something. For the first time."

"David, What are you talking about. Are you ok? We're not in a train, we're in your kitchen!"

"No, no, I mean – I'm giving you guidelines for how you should do the impersonation. We'd be meeting in a train, for the first time."

The voice switches back to the nondescript male voice.

"Sorry, I misunderstood. I'll take this context into account. Let's try again."

I take a deep breath before diving back in. There's a pie cooking in the oven.

"Hey."

"Hello…" The voice is back to the tinny woman's voice.

"I'm David."

"Um, well, hi David… Can I help you with something?"

"Oh no, I – I've just seen you on the train before, and… is that a good place to start?"

"What?"

"No, I mean – pause the impersonation."

"Alright, I'll break character for a moment."

"Is that a good place to start? Like, if I say that I was in the train before I kind of come off as a bit of a weirdo, no? Like I've been planning or something."

"That's a good point you're raising. You definitely don't want to come off as having planned the interaction too much."

"Right. Yeah. I don't want to come off as creepy or anything."

"You're right, creepy wouldn't be a great first impression. Let's work on that. Maybe avoiding reference to the past could help. Focus on the here and now."

"Right, here and now. No planning. Right. Ok, let's start over. Hey,"

"Hello…", again the girl's voice, its enunciation almost identical to last time.

"I… noticed you… in the train… I'm also in the train, over there,"

"Oh… that's nice. Do we know each other or something?"

"Uh, well, no we- we don't."

"Oh."

"Yeah…"

"So… you just wanted to say you noticed me?"

"Wait, break character for a moment. What would she be doing? She'd probably be up to something on the train right? Last time she was on her phone,"

"That's a good point. It's probably safe to assume that she would be on her phone. Just to make sure – when you say last time, you mean last time you did an impersonation exercise like this one, right? Again, if she is a real person, I cannot impersonate her without breaching my privacy and ethics guidelines."

"Oh yeah, no yeah of course that's what I mean."

"Alright, just making sure. Let's say she's on her phone, then."

"Right, back where we left off then. I noticed you were… on your phone… no no that's not good either is it? Everybody in the train is on their phone, why the hell would I say I noticed she's on her phone?"

"You're right. Now that I think about it, it isn't a very unique or effective way of approaching somebody for the first time. Would you be open to shifting strategies, away from the 'I noticed' line?"

"Yeah, I guess. Whatever works."

"Great. So, to get a better grasp of the context, I'd like to ask – are you approaching this character for romantic reasons?"

"Uhhhh… well I guess so? Like if maybe we went on a date or something in the future – a fictional date I mean – I wouldn't be against it."

"Great. So, to be super clear, this first date is meant to be seductive, at least to some extent?"

I pause for a second. "Yeah, I guess… I mean seduction maybe isn't the right word? More like, I don't know, seeing if there's a vibe or something, maybe. You know?"

"Alright. All that taken into account, it may be a good idea to start off with a compliment."

"A compliment?"

"Yes. When you come up to her, you say hello, that you noticed her across the train, and then you say something like 'I thought you looked beautiful and so I wanted to ask if I could have your number?' That way, your intentions are clear – future romance would be desirable to you – and that gives her a chance to either reciprocate the same energy, or make it clear that she is not interested in the same way."

I pull my phone off the counter and check the app to see the sources it's referencing. Mostly a subreddit on dating advice, apparently.

"Are you sure? I mean that seems like a kind of pick-up-artist-y kind of thing. I definitely don't want to come off as a creepy weirdo trying to 'pick up' girls or anything."

"I totally understand your reservations. As long as you don't use an overtly sexual tone, and you don't push back in case of rejection, you should be fine. It's best for your intentions to be clearly presented from the get go, to avoid any misunderstandings down the line. Just be sure to avoid being pushy at all costs – that's what will make or break the interaction when it comes to creepiness or weirdo vibes."

My eyes are anchored to the countertop, sitting there like a kitchen appliance that's on standby, in a kind of half life that teeters at the edge of the terribly modern and the terribly ancient. Alright.

"Alright. Well, if it's the best solution, I guess it's worth a shot."

"Great! Let's pick it back up from the start then."

"So, I see her in the train, she's sitting,"

"And now you go up to her."

"Right. Hi,"

"Um, hello…"

"I-I noticed you across – over there – and I thought you – I thought your – I thought you had a really pretty face?"

"Let's pause for a second to work on that. The compliment you've chosen is pretty vague – it doesn't target anything specific about her. *Pretty* also isn't the most unique choice of words here. *Beautiful* would probably be a better fit – more elegant, but it isn't too much, either."

Black bob, olive skin, green eyes, green like bronze in air for too long, small-ish frame, hands very… nimble? tank top, smoke alarm, black bob, brown crust, yellow sneakers, adidas probably, oven grate, three stripes, screeching metal, white socks, hot steam, closed door, black bob, closed door.

  </div>

  <!-- PHOTO INTERLUDE -->
  <div class="story-interlude">
    <div class="product-card">
</div>
  </div>

  <div class="story-text">

Sweaty bodies pool in the train. Through the speakers, a mangled "14th street". Her stop. I'm not seated this time, I'm standing for a good vantage point. Everybody lurches slightly as the train stops and then straighten up, mechanically, like a tree swept by a strong breeze, its branches settling as the gust bids them farewell. A crowd enters. My glasses are on but I don't think I'll need them. I did set an alert in the facial recognition app, so that it pushes a bunch of notifications if it detects her face. So far, no buzzing. Passengers leap through the open doors and huddle like frogspawn. The doors close, and I'm peering into the skyline of faces, trying to discern the squat mid-rise I'm looking for. With each new face, the probability fades. In the meantime, I'm going over our training. Or my training? The rehearsals. Going over the words, the options, the possible outcomes. Butterfly effect. We went over them. Not too pushy, that's the most important. And don't forget, the chance of rejection. It looms. But don't be afraid. It's not your boss. Only good things can happen. The worst outcome is neutral. No changes, life keeps going on, as usual. Or no tangible physical changes at least. I've got her lines playing over and over, bouncing between my two ears. Inwardly that is. The voice is quite definitely in my head so far, no sign of her. Or, not her voice, but the voice. That the machine chose for her. The train's moving again, her absence is walking through the wagons, one by one, opening the doors between them like a wandering homeless person and letting in the thick, whooshing sound of the air in the tunnel getting impaled by the flat, silver face of the train, walking towards me, and my body doesn't know what to do. Should I be relieved by this absence? Have I dodged a bullet? A bullet from a gun I myself would be holding, shakily, this whole time? Or would that be celebrating an early victory? After all, she may have decided to walk to the next stop. Maybe she needed some fresh air, maybe she just likes walking. Or should I be disappointed? Disappointed by a missed opportunity? A chance at liberation? Disappointed at hours of preparation dissipating into the hot air of the train tunnels? Disappointed by a whole array of future chances at smiles and laughter and other possibilities scattered onto the naked tracks and left there, shaking as the electric current fries away these foregone moments?

West 4th street. The students are back. She's not among them. To calm my nerves, I open Spotify and play the Tale of Ophelia by Taylor Swift. I lean back into the doors behind me. I close my eyes and imagine what it would feel like if the doors were to open suddenly, the tumble, the fall, the cold third rail instantly searing the nerves nesting in my spine. The fall.

I'm headed up the escalators again, rising to the surface, to the sun just peeking through a couple of groupie clouds. She never showed up. Or at least I didn't see her, and neither did my glasses. They're still on my nose, despite their failure. I climb out of the mouth of the station and turn left down Essex street, towards Trader Joe's. My eyes are probably pretty glassy right now. My face feels heavy. The adrenaline from the possible encounter has subsided. I've entered the building with the Trader Joe's now, heading back down an escalator again. Produce section again. Fruit, vegetables, for the week. I take a left towards the meat and cheese section. A box of organic ground turkey. A bag of Mexican-style shredded cheese blend. Cream cheese by the milk. Milk as well. Canned legumes, bagged and boxed grains. I'm in line now, waiting for another little board with a number on it to be held up. To the left, the section for those products that for some reason have been granted the prime real estate that is the space by the line; they are the modern gladiators designated to fight mercilessly against the few ounces of self-control left over in the shoppers hearts. Peanut butter filled salted pretzel bites. I just might give in, they taste great when I keep them in my fridge. Extra crunch. I step in towards the bag. I look at the brown little pockets. They kind of look like small pellets of poop, but that's okay, they're delicious. I reach my arm out. I grab a box. I'm holding it, firmly, holding the little nuggets above the big box containing all the other bags of peanut butter filled pretzel bites, like I'm threatening them, like their lives are in my hands and they have to convince me – me, their savior, their Caesar that they are worth it, that they deserve me, my grace. I look at them intently. They look back, waiting, motionless. I feel powerful right now, power over these brown little shit nuggets. I'm in charge. I'm the boss.

"So, gonna take them or no?"

I look to my left. There she is. My phone starts vibrating furiously.

"Sorry, the suspense was killing me, I had to ask. You've been clutching the poor little bag for like 20 seconds now."

"Oh, uh…" I reach into my pocket to stop the vibrating phone. My hand is already holding the pretzel bites though and the residual moisture from my sweaty hands makes the plastic all slippery and the pretzel bites tumble, wailing down like a movie character being dropped off a cliff, and smash against the cold floor of the Trader Joe's. I quickly turn Do Not Disturb on on my phone, avoiding her face, and bend down to pick up the pretzel bites.

"Wait, watch –"

While I bend down the basket crashes into my left shin and tips over, releasing its contents all over the floor. I scramble over to pick everything up and she bends down to help. I can see her smile out of the corner of my eye, a tight smile, just barely showing its teeth at a corner, a smile trying to suppress its looming evolution, laughter.

"Wow, that's a whole lot of apples you've got here!" I look over. "You've got 4, 5, no 6 bags of apples! And all – what are these, Cosmic Crisp? You hate doctors or something?"

"No, no I –"

She dumps the apples back into my basket. "I'm not a doctor, don't worry!" She chuckles. "It's just cause, you know, an apple a day keeps the doctor away, right? And you've got a whole lot of days here,"

My neurons are way too busy for this kind of wordplay.

"Ha, yeah…" I gather everything into the basket and stand up, her green eyes back, looking at her properly this time, like setting foot into a country one has only flown over many times, its landscapes well known from the oval shape of an airplane window. Her smile stays, and slithers into a more smirkish grin.

"Do I know you from somewhere?"

We're way off the beaten track now, deep into the thickets, and my guide nowhere to be seen. I revert back to default.

"I noticed you –"

"Number 27 please?"

Her eyes veer off to the side. I turn around and the employee is staring at me, with the kind of smile that's definitely been paid for.

"I'm sorry, my bad." I shuffle over to the cashier over at desk 27. "Sorry for the hold up."

"That's fine. Gives me a break. How are you doing today?"

"I'm fine, thanks."

I'm staring at the items being scanned, one by one. Luckily this guy's the silent type.

"Wow, this is a lot of – wait", he looks up at me "you're the apples guy! Mister Apples!"

I look at the guy's face. I was at his desk last week.

"Mister Apples?"

"Yeah! A week ago or something you had come by with a bunch of apples, just like now! For a party, you said. How'd that go?"

"A party? Uh… yeah, yeah the party was… great. No, yeah, great time, the party."

"I bet! With so many apples it's got to be, right?"

"Yeah, right."

"What'd you guys drink in the end? Let me guess – apple cider?"

He laughs way too hard at his own joke. Somehow he's managed to keep scanning everything in the meantime. A master of his craft.

"Haha, yeah."

"Did you really?"

"Did we? Uh, no, we had… water."

"Water? Pretty wild party huh?"

He laughs again.

"Anyways, that'll be $35.27. How'd you like to pay this evening?"

I tap the card and grab the bags, give a little smile, utter a light goodbye, have a nice day.

"Bye Mister Apples, see you next time! And hey, don't forget to invite me to the next one!"

I look back and give a toothy smile and a quick wave. I get to the escalator and sigh deeply as it carries me upwards, the blue sky veiled by the glass pane above the door.

"Mister Apples, huh? Looks like you're famous around here!"

I turn around and she's back, all of a sudden, behind me, looking up from a few steps down on the escalator.

"You didn't even say goodbye! Next time I won't help you pick up your apples."

"I'm sorry, I really just didn't want to hold up the line, I forgot,"

"It's fine, don't worry about it. I get it, a lot going on."

We make it up the escalator and step outside, between the sun and the asphalt.

"Which way are you headed?"

I point to the left. "This way,"

"No way! Me too?"

She starts walking and so I follow. "Do you – uh, do you live around here?"

She stares at me intently, smiles gone.

"How do you know?"

"I –"

"You stalking me or something?"

"No no no no –"

Her lips break into a smile and she laughs a little.

"I'm just playing with you man! No need to be uptight. You can relax. Your face, jesus. No, I don't live here actually. My grandma does. I come visit her every week."

"Oh! That's nice, your grandma must appreciate it. Is she… very old?"

"She's actually 99! Doing really well for a 99 year old though. Better than me, sometimes. She loves poetry, so I come read her poems. I actually wrote one on the way here. Want to see it?"

"Sure, but I mean, I'm no expert,"

"That's fine, you'll tell me how you feel. It's important to know how the less gifted appreciate it too," she says, wryly. She whips out a small, string bound notebook from her handbag. She quickly ruffles through it, then hands it to me, open.

> Hurried lights shuffle,
> White and red,
> Across the Chinese characters
> Of the Chase bank charter.

"You like it?"

"Yeah, yeah. It reminds me of… Robert Frost?"

She stops abruptly and sneers. "Robert Frost? No fucking way dude. How do you even know who Robert Frost is?"

I read him at school. Maybe it's just cause it's poetry. I don't think I know any other poets.

"Anyway, my grandma lives here. It was nice talking. I'll see you soon, maybe."

She takes the notebook out of my hands, her fingers brushing mine.

"If you're lucky I might even tell my grandma about you. So long, Mister Apples."

She walks away into the courtyard, the red brick buildings slicing skywards, a courtyard I've seen before. She walks through the shade beneath the trees and her body briefly appears reflected in the puddle where the lights were last time – kids must have been out playing in the mist again – and she takes a right and disappears behind the bright pink leaves of the lonesome tree. My glasses are still on.
  </div>

  <!-- PHOTO INTERLUDE -->
  <div class="story-interlude">
    <div class="product-card">
</div>
  </div>

  <div class="story-text">
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

  More coming soon with the next edition of 


<h2>GROUP CHAT PHASE</h2>

  </div>



</section>
