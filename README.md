# Foundation Model Comparison

## Table of Contents

- [Result Summary](#result-summary)
- [Full Results](#full-results)
- [Prompt](#prompt)

---

## Introduction

This repository contains the results of an experiment which aims to evaluate the performance of Apple’s [Foundation Model](https://developer.apple.com/documentation/foundationmodels) (available in iOS 26, macOS 26, watchOS 26, tvOS 26, and visionOS 26) against comparably sized open-source models running in [LM Studio](https://lmstudio.ai/) and popular hosted LLM services (which are _far_ larger and should be more capable).

The prompt is a text summarisation task. It requires the model to condense a lengthy journal entry into a single paragraph under 50 words, written in first person without meta-commentary.

The prompt is designed to be a real-world test of a prompt that might be useful in mobile applications. It tests whether the model can follow strict formatting constraints, maintain conciseness for UI display, and preserve narrative voice. This type of summarisation could be valuable for apps that need to digest long content (emails, articles, documents) into digestible snippets while respecting character limits and maintaining readability.

The full write-up of this experiment is available in [iOS Dev Weekly - Issue 719](https://iosdevweekly.com/issues/719/#start).

## Result Summary

| Model                               | Word Count | Rating |
| ----------------------------------- | ---------- | ------ |
| Apple - Foundation Model            | 49         | 🟢     |
| Anthropic - Claude Sonnet 4         | 86         | 🔴 ¹   |
| Google - Gemini 2.5 Flash           | 100        | 🔴 ²   |
| Google - Gemini 2.5 Pro             | 46         | 🟢     |
| LM Studio - gemma-3n-e4b-it-mlx     | 63         | 🟠     |
| LM Studio - qwen2.5-3b-instruct-mlx | 76         | 🟠     |
| OpenAI - ChatGPT 4o                 | 51         | 🟢     |
| OpenAI - ChatGPT o3                 | 47         | 🟢     |
| OpenAI - ChatGPT o4-mini            | 45         | 🟢     |

**Notes:**

1. Claude Sonnet 4 consistently ignored the word limit, often going over 80 characters.
2. Gemini 2.5 Flash ignored the single paragraph requirement, and _also_ the word limit. 😬

## Full Results

### Anthropic - Claude Sonnet 4

```
I woke late and spent the morning reading my Spanish book about Rome at the
office. At noon I went to the Hall where I heard news of Monk's letter to
Parliament, then dined on roasted chicken with Chetwind near Temple Bar. We
visited Guildhall expecting Monk, went to taverns, and I met with Lock who
explained Monk's complaints to Parliament. The evening brought extraordinary
celebrations throughout London with bonfires, bell-ringing, and people roasting
"rumps" in the streets before I returned home with my wife.
```

### Apple - Foundation Model

```
I spent the day at my office reading and then went to a meeting with colleagues,
where I heard exciting news about Monk's plans. We visited shops, dined at
Temple Bar, and met friends in the city. The streets were filled with bonfires
and celebrations as we returned home.
```

### Google - Gemini 2.5 Flash

```
I read in my office, then learned of Monk's letter and dined with Mr. Chetwind.
I sang in his study, then we went to Guildhall and drank at taverns, witnessing
Monk's return. Later, I dined again, and showed my wife the joyful bonfires
before we returned home.

I spent the morning reading my Spanish book of Rome, then went to the Hall,
where news of Monk’s letter brought sudden joy. I lunched with Chetwind,
visited Guildhall, and saw Monk greeted with cheers. The city erupted in
bonfires, bells, and celebrations, which I enjoyed with my wife before heading
to bed.
```

### Google - Gemini 2.5 Pro

```
This morning I read my Spanish book before heading into the city. I dined with
Mr. Chetwind and witnessed the great public joy over General Monk's actions,
with celebratory bells and bonfires everywhere. I wrote some letters and later
showed the amazing fires to my wife.
```

### LM Studio - gemma-3n-e4b-it-mlx

```
I spent the day traveling between offices, meeting with friends, and observing
the city's jubilant reaction to a letter from Monk. We dined, visited various
locations including Guildhall and taverns, and witnessed widespread celebrations
with bonfires, ringing bells, and people displaying symbolic "rumps." I wrote
letters throughout the day, eventually returning home with my wife after
witnessing the extraordinary displays of public celebration.
```

### LM Studio - qwen2.5-3b-instruct-mlx

```
Today, I slept late then went to my office where I read Spanish. In the Hall,
men changed from joy to anger upon hearing letters. I attended meetings and
dined at various places due to no food availability. At Temple Bar, we dined
then drank wine and ale before going to Guildhall. There, Monk's arrival
triggered a joyous response from the crowd. We dined further at various taverns
and witnessed numerous bonfires along our journey home.
```

### OpenAI - ChatGPT 4o

```
I spent the day reading, visiting Westminster Hall, and joining Chetwind on a
trip into the City, where we dined, visited offices, and followed news of
General Monk’s letter to Parliament. The day ended with widespread celebrations,
bonfires, and public joy, which I shared with my wife before heading to bed.
```

### OpenAI - ChatGPT o3

```
I lingered in bed, studied my Spanish book, visited Westminster Hall to witness
Monk’s momentous letter, lunched on a roasted pullet with Chetwind, trailed
cheering crowds to Guildhall, drank at several taverns, wrote letters, then
walked amid jubilant bonfires with my wife before posting mail and retiring.
```

### OpenAI - ChatGPT o4-mini

```
I read my Spanish book, walked to the Hall to hear Monk’s letter, dined with
Chetwind at Temple Bar, visited the lawyers’ offices, awaited Monk’s triumphant
return at Guildhall, wrote letters and dined again, and wandered home with my
wife amid London’s bonfires and celebrations.
```

## Prompt

```
The text below is an entire journal entry for a person's day. Please summarise
the entry, focusing the summary on what the person did that day. Keep the
summary to a single paragraph of less than 50 words. Write the summary in the
first person. Do not introduce the summary as a summary, just go straight into
it.

---

This morning I lay long abed, and then to my office, where I read all the
morning my Spanish book of Rome. At noon I walked in the Hall, where I heard the
news of a letter from Monk, who was now gone into the City again, and did
resolve to stand for the sudden filling up of the House, and it was very strange
how the countenance of men in the Hall was all changed with joy in half an
hour’s time. So I went up to the lobby, where I saw the Speaker reading of the
letter; and after it was read, Sir A. Haselrigge came out very angry, and
Billing--[The quaker mentioned before on the 7th of this month.]--standing at
the door, took him by the arm, and cried, “Thou man, will thy beast carry thee
no longer? thou must fall!” The House presently after rose, and appointed to
meet again at three o’clock. I went then down into the Hall, where I met with
Mr. Chetwind, who had not dined no more than myself, and so we went toward
London, in our way calling at two or three shops, but could have no dinner. At
last, within Temple Bar, we found a pullet ready roasted, and there we dined.
After that he went to his office in Chancery Lane, calling at the Rolls, where I
saw the lawyers pleading. Then to his office, where I sat in his study singing,
while he was with his man (Mr. Powell’s son) looking after his business. Thence
we took coach for the City to Guildhall, where the Hall was full of people
expecting Monk and Lord Mayor to come thither, and all very joyfull. Here we
stayed a great while, and at last meeting with a friend of his we went to the 3
Tun tavern and drank half a pint of wine, and not liking the wine we went to an
alehouse, where we met with company of this third man’s acquaintance, and there
we drank a little. Hence I went alone to Guildhall to see whether Monk was come
again or no, and met with him coming out of the chamber where he had been with
the Mayor and Aldermen, but such a shout I never heard in all my life, crying
out, “God bless your Excellence.” Here I met with Mr. Lock, and took him to an
alehouse, and left him there to fetch Chetwind; when we were come together, Lock
told us the substance of the letter that went from Monk to the Parliament;
wherein, after complaints that he and his officers were put upon such offices
against the City as they could not do with any content or honour, that there are
many members now in the House that were of the late tyrannical Committee of
Safety. That Lambert and Vane are now in town, contrary to the vote of
Parliament. That there were many in the House that do press for new oaths to be
put upon men; whereas we have more cause to be sorry for the many oaths that we
have already taken and broken. That the late petition of the fanatique people
presented by Barebone, for the imposing of an oath upon all sorts of people, was
received by the House with thanks. That therefore he [Monk] do desire that all
writs for filling up of the House be issued by Friday next, and that in the mean
time, he would retire into the City and only leave them guards for the security
of the House and Council. The occasion of this was the order that he had last
night to go into the City and disarm them, and take away their charter; whereby
he and his officers say that the House had a mind to put them upon things that
should make them odious; and so it would be in their power to do what they would
with them. He told us that they [the Parliament] had sent Scott and Robinson to
him [Monk] this afternoon, but he would not hear them. And that the Mayor and
Aldermen had offered him their own houses for himself and his officers; and that
his soldiers would lack for nothing. And indeed I saw many people give the
soldiers drink and money, and all along in the streets cried, “God bless them!”
and extraordinary good words. Hence we went to a merchant’s house hard by, where
Lock wrote a note and left, where I saw Sir Nich. Crisp, and so we went to the
Star Tavern (Monk being then at Benson’s), where we dined and I wrote a letter
to my Lord from thence. In Cheapside there was a great many bonfires, and Bow
bells and all the bells in all the churches as we went home were a-ringing.
Hence we went homewards, it being about ten o’clock. But the common joy that was
every where to be seen! The number of bonfires, there being fourteen between St.
Dunstan’s and Temple Bar, and at Strand Bridge’ I could at one view tell thirty-
one fires. In King-street seven or eight; and all along burning, and roasting,
and drinking for rumps. There being rumps tied upon sticks and carried up and
down. The butchers at the May Pole in the Strand rang a peal with their knives
when they were going to sacrifice their rump. On Ludgate Hill there was one
turning of the spit that had a rump tied upon it, and another basting of it.
Indeed it was past imagination, both the greatness and the suddenness of it. At
one end of the street you would think there was a whole lane of fire, and so hot
that we were fain to keep still on the further side merely for heat. We came to
the Chequers at Charing Cross, where Chetwind wrote a letter and I gave him an
account of what I had wrote for him to write. Thence home and sent my letters to
the posthouse in London, and my wife and I (after Mr. Hunt was gone, whom I
found waiting at my house) went out again to show her the fires, and after
walking as far as the Exchange we returned and to bed.
```
