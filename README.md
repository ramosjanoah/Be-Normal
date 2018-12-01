# Be-Normal Dataset!

Author : 
- Ramos Janoah (Email: ramosj.noah@gmail.com | [IG](https://www.instagram.com/ramosjanoah/))
- Alson Cahywadi (Email: alson.cahyadi@bukalapak.com | [IG](https://www.instagram.com/alson.cahyadi/)

Be-Normal dataset is an Indonesian word normalizer dataset, collected from:
- Twitter, (15M collected, 1500 tweet picked, 200 normalized)
- YouTube comments (Comments collected from 10 videos, 0 picked, 0 normalized)

This data form in pair of text, raw text and normalized text. I'm targetting to make 10k pair of text, with 5k from each source.

You can use this dataset by contact me first using email: ramosj.noah@gmail.com. I'm an active user so i'll give response at least 24 after you send me the email.

## Index
- [Package used](#package)
- [Few notes for this project](#notes)
- [Normalization Rule](#normalization-rule)
- [Example](#example)
- [README: Twitter](twitter/README.md)

## Package
Package i used for this project:
- Tokenizer, from NLTK. Especially TweetTokenizer for tokenizing tweet.

## Notes
Notes for this dataset:
1. Tweet is collected on 2018, from random users.
2. YouTube comments is collected on 2018 from these video (the parenthesis is the comment retrieved from the video):
	- https://youtu.be/eo7P0g6L830 - Welcome Home 
	- https://youtu.be/otjAgNYRLqo - #StandUpNite2 - Raditya Dika (Part 1 of 2)
	- https://youtu.be/1QDSCy1ctQc - VLOGGG #19: Jengkol, Warteg, dan Sikat Gigi
	- https://youtu.be/K5TEigHDbJk - Mamat: Si Anak Papua - SUCI 7
	- https://youtu.be/RJzdy5AgMFg - GAPAPA JELEK YANG PENTING SOMBONG feat. DEVINAUREEL, EKA GUSTIWANA
	- https://youtu.be/5N7Km4gH2ZY - PERANG AYAM GEPREK! GAGAL TOTAL!
	- https://youtu.be/QedkKwF8E8s - Gokil! Arie Kriting & Akbar Pecahin Rekor Jawab TTS Berturut-turut
	- https://youtu.be/piJW_oRCZqY - PRANK RICIS DITELPON COWOK LAIN - CEMBURU CIYEEEE.....
	- https://youtu.be/NEjJZT6JPkU - PRANK PALING GREGET Wkwkwkwk
	- https://youtu.be/WP2QU2_RTQk - Bagaimana Jika (What If)
	- https://youtu.be/zXZfKEJCIbY - COBAIN CEREAL IMPOR
	- https://youtu.be/X9cSqFmKzQM - 6 Fakta Unik Tentang Agung Hapsah
	- https://youtu.be/f--nzCB8EKk - Kecewa
	- https://youtu.be/hAzxl--j3oI - Kenapa Ahok Kalah?
	- https://youtu.be/fg72DS56lwE - SKINNYINDONESIAN24 - INDOMIE, MIE DARI INDONESIA (LAGU INDOMIE)

## Normalization Rule
Rule for this normalization:
1. The normalization fix this kind of unnormalized form:
	- Typo or Misspell word (lack or overuse the character)
	- Elongation, example: ayoooooo -> ayo
	- Capitalization, example: AYO KITA BISA -> Ayo kita bisa
	- Using of the punctuation, example: AYO KITA BISA.....!! -> Ayo kita bisa!
	- Slang words. For details, see point number 2.
2. For slang words, it depends on the style (in Indonesian, _padanan kata_). If _padanan kata_ is casual style, then it would use the slang word that suitable to it style. But if it is formal style, than it would use the word on KBBI (Kamus Besar Bahasa Indonesia).
Example:
_Gue ngga bisa seperti ini_ -> _Gue enggak bisa seperti ini_ (casual style, the correct slang word of 'ngga' is 'enggak')
_Saya ngga bisa membalas pesan anda_ -> _Saya tidak bisa membalas pesan anda_ (formal style, the corect KBBI word for 'ngga' is 'tidak')
3. Hastag (#), mention (@) token are not changed.
4. There are no retweet on this dataset, because it would decrease your model if your model use language model. So basically all the tweet at least must be the first tweet on a conversation on twitter.
5. Named Entity are not changed, but the capitalization of the NE are corrected.
6. Emoticon has its own normalize form, check this:
	- :) -> \_\_smile\_\_
	- :( -> \_\_sad\_\_
	- :'( -> \_\_cry\_\_
7. I pick some ambiguity in this dataset, so it won't be easy to solve this normalization
8. Normalization also fix the usage of the space:
	 - The space must be exist between the punctuation and the character. Example: 
	 	- _Saya suka makan,dan juga minum_ -> _Saya suka makan, dan juga minum_
	 	- _Badan sakit semua kebanyakan tidur-\_\_\_-_ -> _Badan sakit semua kebanyakan tidur -\_\_\_-_
	 - The over-use of space character also fixed.
9. This dataset is not correcting the case if the sentence should using the punctuation but it's not.
10. The unclear and unknown word are not normalized. 

## Example
Example of the data:

```
#tweet_id = 0
#unnormalized = Temen2 blang "punya twitter kan,curhat gihh dstu" wkwkwkwkk
#normalized = Teman-teman bilang "punya twitter kan, curhat gih di situ" __laugh__
1	Temen2	Teman-teman	
3	blang	bilang	
4	"	"	
5	punya	punya	
6	twitter	twitter	
7	kan	kan	
8	,	,	
9	curhat	curhat	
10	gihh	gih	
11	dstu	di situ	
12	"	"	
13	wkwkwkwkk	__laugh__
```

