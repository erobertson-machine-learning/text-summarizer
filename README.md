# Spacy text summary learning
- Basted on vide [here](https://www.youtube.com/watch?v=XcZGKAF5zxg)



```python
import spacy
from spacy.lang.en.stop_words import STOP_WORDS
```


```python
# Stop words are words that do not add to text understanding, like 'a' and 'the'
# https://medium.com/@makcedward/nlp-pipeline-stop-words-part-5-d6770df8a936
print( 'Stop Words: ', len(STOP_WORDS) )
```

    Stop Words:  326
    

### Article


```python
article = '''President Donald Trump declared himself "your president of law and order" during remarks Monday as peaceful protesters just outside the White House gates were dispersed with tear gas, flash bangs and rubber bullets, apparently so Trump could visit a nearby church.
The episode, which amounted to one of the most highly charged and discordant moments in recent presidential history, came as nationwide unrest escalates and Trump comes under pressure to demonstrate a modicum of conciliation for a country torn along racial, ideological and political lines.
With the constant sound of helicopter blades overhead and a steady succession of bangs from nearby Lafayette Park, Trump declared himself an "ally of all peaceful protesters."
But as he was speaking, peaceful protesters were being urgently dispersed outside the White House gates by police using rubber bullets, tear gas and flash bangs. Several protesters were seen pouring water into their eyes to ease the gas's sting.
George Floyd protests spread nationwide
George Floyd protests spread nationwide
Later, Trump walked across the park to St. John's Episcopal Church, a house of worship used by American presidents for more than a century that was partially burned in a Sunday evening protest.
"We have the greatest country in the world," Trump said, holding a Bible and surrounded by aides.
Before Trump's address, a crowd was gathering outside the White House gates ahead of a 7 p.m. ET curfew mandated by the mayor of Washington, including near the church.
A large convoy of military vehicles was also seen driving through the White House complex and onto Pennsylvania Avenue.
Trump said from the Rose Garden he was committed to upholding laws and mobilizing military resources to end nationwide looting.
"My first and highest duty as president is to defend our great country and the American people," Trump said. "I swore an oath to uphold the laws of our nation and that is exactly what I will do."
In striking terms, Trump said he would use his entire presidential prerogative -- including threatening to invoke a rarely used law dating back to 1807 -- to ensure violent protests end, declaring he would deploy "thousands and thousands of heavily armed soldiers, military personnel and law enforcement officers" to bring order.
Trump said justice would be served for George Floyd, the unarmed black man who died after a white police officer knelt on his neck as he was being arrested.
Ahead of his appearance on Monday evening, a debate had raged among his advisers over how and whether he should address protests that have spread to dozens of cities.
Some of the President's allies were growing increasingly frustrated with what has felt like silence from the White House. And many of the President's traditional defenders -- from campaign donors to Republicans on Capitol Hill to some in the conservative media -- privately grumbled that Trump allowed several days to pass without addressing the nation or making any formal appeals for unity.
What Trump has done publicly -- tweet extensively about his grievances with Democratic state and local leaders and mention the protests in the middle of a previously scheduled event -- has at best gone unnoticed and at worst fanned the flames of outrage into a second week.
Some outside allies have reached out to the White House in recent days to push for an appearance from the President in which he would confront a crisis he has largely watched unfold from behind closed doors or in his underground bunker.
One major campaign donor worried that the damage inflicted by Trump's absence during a historic weekend of violence and pain could alone imperil his reelection.
An agitated Trump encourages governors to use aggressive tactics on protesters
An agitated Trump encourages governors to use aggressive tactics on protesters
One person familiar with the matter said there is a sense among allies that an attempt to address the situation in a speech over the weekend fell completely flat. The person said the unrelated backdrop of the Kennedy Space Center -- and the fact that the speech came on a Saturday afternoon -- ensured few people even registered the passages that were added at the last minute.
"We support the right of peaceful protests and we hear their pleas, but what we are now seeing on the streets of our cities has nothing to do with the memory of George Floyd," Trump said in his remarks after watching the first manned US space launch in nearly a decade. "The mobs are devastating the life's work of good people and destroying their dreams."
Trump's measured tone stood in stark contrast to his barrage of tweets over the weekend, which included messages blaming Antifa for the unrest and vowing severe retaliation.
A growing number of congressional Republicans, even Trump's allies, have privately said the "caps lock" tweets are not helping the situation. Republican Sen. Tim Scott of South Carolina said on "Fox News Sunday" that he had spoken to Trump over the weekend about his inflammatory tweets, which he described as "not constructive."
Over the weekend, some aides sought to convince Trump not to use violent rhetoric after he wrote on Twitter that "when the looting starts the shooting starts," warning language like that could inflame an already combustible situation and would not appear presidential.
Inside the White House, advisers remain divided over whether a speech delivered from the Oval Office or elsewhere at the White House would help lower the national temperature.
Trump has expressed interest in delivering a speech to the nation, a person close to the White House said, but some administration officials believe that would be a mistake. A senior White House aide said governors and mayors should be the ones responding to the destruction in their respective cities and states -- a view at least partially shared by Trump, who has spent days going after local leaders for not calling the National Guard fast enough or cracking down on violence aggressively enough.
In a heated phone call with governors on Monday morning, Trump placed responsibility on the governors for resolving the national crisis and said some of them appeared "weak" in their responses so far.
Other White House officials argued over the weekend against something as formal as an Oval Office address, a person familiar said, out of concern that such a speech could "inflame the situation, not make it better."
As aides debate how and whether to confront the situation, Trump's back-and-forth between violent rhetoric and a more measured tone has weighed in the deliberations, one official said. Some advisers wonder whether a presidential address calling for calm would be quickly erased by Trump's own penchant for escalation and instigation.
It did not seem such a speech was imminent on Monday morning.
"A national Oval Office address is not going to stop Antifa," White House press secretary Kayleigh McEnany said in an appearance Monday on Fox News, noting that Trump had addressed the killing of George Floyd -- a black Minneapolis man who died after a white police officer knelt on his neck during an arrest -- several times already.
"The President has addressed this repeatedly," she said. Later, McEnany said Trump's "focus right now is acting and keeping our streets safe."
'''
```


```python
article = article.replace('\n', '.')
article
```




    'President Donald Trump declared himself "your president of law and order" during remarks Monday as peaceful protesters just outside the White House gates were dispersed with tear gas, flash bangs and rubber bullets, apparently so Trump could visit a nearby church..The episode, which amounted to one of the most highly charged and discordant moments in recent presidential history, came as nationwide unrest escalates and Trump comes under pressure to demonstrate a modicum of conciliation for a country torn along racial, ideological and political lines..With the constant sound of helicopter blades overhead and a steady succession of bangs from nearby Lafayette Park, Trump declared himself an "ally of all peaceful protesters.".But as he was speaking, peaceful protesters were being urgently dispersed outside the White House gates by police using rubber bullets, tear gas and flash bangs. Several protesters were seen pouring water into their eyes to ease the gas\'s sting..George Floyd protests spread nationwide.George Floyd protests spread nationwide.Later, Trump walked across the park to St. John\'s Episcopal Church, a house of worship used by American presidents for more than a century that was partially burned in a Sunday evening protest.."We have the greatest country in the world," Trump said, holding a Bible and surrounded by aides..Before Trump\'s address, a crowd was gathering outside the White House gates ahead of a 7 p.m. ET curfew mandated by the mayor of Washington, including near the church..A large convoy of military vehicles was also seen driving through the White House complex and onto Pennsylvania Avenue..Trump said from the Rose Garden he was committed to upholding laws and mobilizing military resources to end nationwide looting.."My first and highest duty as president is to defend our great country and the American people," Trump said. "I swore an oath to uphold the laws of our nation and that is exactly what I will do.".In striking terms, Trump said he would use his entire presidential prerogative -- including threatening to invoke a rarely used law dating back to 1807 -- to ensure violent protests end, declaring he would deploy "thousands and thousands of heavily armed soldiers, military personnel and law enforcement officers" to bring order..Trump said justice would be served for George Floyd, the unarmed black man who died after a white police officer knelt on his neck as he was being arrested..Ahead of his appearance on Monday evening, a debate had raged among his advisers over how and whether he should address protests that have spread to dozens of cities..Some of the President\'s allies were growing increasingly frustrated with what has felt like silence from the White House. And many of the President\'s traditional defenders -- from campaign donors to Republicans on Capitol Hill to some in the conservative media -- privately grumbled that Trump allowed several days to pass without addressing the nation or making any formal appeals for unity..What Trump has done publicly -- tweet extensively about his grievances with Democratic state and local leaders and mention the protests in the middle of a previously scheduled event -- has at best gone unnoticed and at worst fanned the flames of outrage into a second week..Some outside allies have reached out to the White House in recent days to push for an appearance from the President in which he would confront a crisis he has largely watched unfold from behind closed doors or in his underground bunker..One major campaign donor worried that the damage inflicted by Trump\'s absence during a historic weekend of violence and pain could alone imperil his reelection..An agitated Trump encourages governors to use aggressive tactics on protesters.An agitated Trump encourages governors to use aggressive tactics on protesters.One person familiar with the matter said there is a sense among allies that an attempt to address the situation in a speech over the weekend fell completely flat. The person said the unrelated backdrop of the Kennedy Space Center -- and the fact that the speech came on a Saturday afternoon -- ensured few people even registered the passages that were added at the last minute.."We support the right of peaceful protests and we hear their pleas, but what we are now seeing on the streets of our cities has nothing to do with the memory of George Floyd," Trump said in his remarks after watching the first manned US space launch in nearly a decade. "The mobs are devastating the life\'s work of good people and destroying their dreams.".Trump\'s measured tone stood in stark contrast to his barrage of tweets over the weekend, which included messages blaming Antifa for the unrest and vowing severe retaliation..A growing number of congressional Republicans, even Trump\'s allies, have privately said the "caps lock" tweets are not helping the situation. Republican Sen. Tim Scott of South Carolina said on "Fox News Sunday" that he had spoken to Trump over the weekend about his inflammatory tweets, which he described as "not constructive.".Over the weekend, some aides sought to convince Trump not to use violent rhetoric after he wrote on Twitter that "when the looting starts the shooting starts," warning language like that could inflame an already combustible situation and would not appear presidential..Inside the White House, advisers remain divided over whether a speech delivered from the Oval Office or elsewhere at the White House would help lower the national temperature..Trump has expressed interest in delivering a speech to the nation, a person close to the White House said, but some administration officials believe that would be a mistake. A senior White House aide said governors and mayors should be the ones responding to the destruction in their respective cities and states -- a view at least partially shared by Trump, who has spent days going after local leaders for not calling the National Guard fast enough or cracking down on violence aggressively enough..In a heated phone call with governors on Monday morning, Trump placed responsibility on the governors for resolving the national crisis and said some of them appeared "weak" in their responses so far..Other White House officials argued over the weekend against something as formal as an Oval Office address, a person familiar said, out of concern that such a speech could "inflame the situation, not make it better.".As aides debate how and whether to confront the situation, Trump\'s back-and-forth between violent rhetoric and a more measured tone has weighed in the deliberations, one official said. Some advisers wonder whether a presidential address calling for calm would be quickly erased by Trump\'s own penchant for escalation and instigation..It did not seem such a speech was imminent on Monday morning.."A national Oval Office address is not going to stop Antifa," White House press secretary Kayleigh McEnany said in an appearance Monday on Fox News, noting that Trump had addressed the killing of George Floyd -- a black Minneapolis man who died after a white police officer knelt on his neck during an arrest -- several times already.."The President has addressed this repeatedly," she said. Later, McEnany said Trump\'s "focus right now is acting and keeping our streets safe.".'




```python
# Does tokenization of the text into parts of speach and stuch
nlp = spacy.load('en_core_web_sm')
parsed = nlp( article )
```


```python
print("Noun phrases:", [chunk.text for chunk in parsed.noun_chunks])
```

    Noun phrases: ['President Donald Trump', 'himself', 'your president', 'law', 'order', 'remarks', 'peaceful protesters', 'the White House gates', 'tear gas', 'flash bangs', 'rubber bullets', 'Trump', 'a nearby church', 'The episode', 'the most highly charged and discordant moments', 'recent presidential history', 'nationwide unrest escalates', 'Trump', 'pressure', 'a modicum', 'conciliation', 'a country', 'racial, ideological and political lines', 'the constant sound', 'helicopter blades', 'bangs', 'nearby Lafayette Park', 'Trump', 'himself', 'all peaceful protesters', 'he', 'peaceful protesters', 'the White House gates', 'police', 'rubber bullets', 'tear gas', 'flash bangs', 'Several protesters', 'water', 'their eyes', "the gas's sting", 'George Floyd protests', 'George Floyd protests', 'Trump', 'the park', "St. John's Episcopal Church", 'a house', 'worship', 'American presidents', 'more than a century', 'a Sunday evening protest', 'the greatest country', 'the world', 'Trump', 'a Bible', 'aides', "Trump's address", 'a crowd', 'a 7 p.m. ET curfew', 'the mayor', 'Washington', 'the church', 'A large convoy', 'military vehicles', 'the White House complex', 'Pennsylvania Avenue', 'Trump', 'the Rose Garden', 'he', 'laws', 'mobilizing military resources', 'nationwide looting', 'first and highest duty', 'president', 'our great country', 'the American people', 'Trump', 'I', 'an oath', 'the laws', 'our nation', 'exactly what', 'I', 'striking terms', 'Trump', 'he', 'his entire presidential prerogative', 'a rarely used law', 'violent protests', 'he', 'thousands', 'thousands', 'heavily armed soldiers', 'military personnel', 'law enforcement officers', 'order', 'Trump', 'justice', 'George Floyd', 'the unarmed black man', 'who', 'a white police officer', 'his neck', 'he', 'his appearance', 'Monday evening', 'a debate', 'his advisers', 'he', 'protests', 'dozens', 'cities', "the President's allies", 'what', 'silence', 'the White House', "the President's traditional defenders", 'campaign donors', 'Republicans', 'Capitol Hill', 'the conservative media', 'Trump', 'several days', 'the nation', 'any formal appeals', 'unity', 'What', 'Trump', 'his grievances', 'Democratic state and local leaders', 'the protests', 'the middle', 'a previously scheduled event', 'the flames', 'outrage', 'a second week', 'Some outside allies', 'the White House', 'recent days', 'an appearance', 'the President', 'he', 'a crisis', 'he', 'unfold', 'closed doors', 'his underground bunker', 'One major campaign donor', 'the damage', "Trump's absence", 'a historic weekend', 'violence', 'pain', 'his reelection', 'An agitated Trump', 'governors', 'aggressive tactics', 'protesters', 'An agitated Trump', 'governors', 'aggressive tactics', 'protesters', 'One person', 'the matter', 'a sense', 'allies', 'an attempt', 'the situation', 'a speech', 'the weekend', 'The person', 'the unrelated backdrop', 'the Kennedy Space Center', 'the fact', 'the speech', 'a Saturday afternoon', 'few people', 'the passages', 'the last minute', 'the right', 'peaceful protests', 'we', 'their pleas', 'what', 'we', 'the streets', 'our cities', 'nothing', 'the memory', 'George Floyd', 'Trump', 'his remarks', 'the first manned US space launch', 'nearly a decade', 'The mobs', "the life's work", 'good people', 'their dreams', "Trump's measured tone", 'stark contrast', 'his barrage', 'tweets', 'the weekend', 'messages', 'Antifa', 'the unrest', 'severe retaliation', 'A growing number', 'congressional Republicans', "even Trump's allies", 'the "caps lock" tweets', 'the situation', 'Republican Sen. Tim Scott', 'South Carolina', '"Fox News', 'he', 'the weekend', 'his inflammatory tweets', 'he', 'the weekend', 'some aides', 'Trump', 'violent rhetoric', 'he', 'Twitter', 'the looting', 'the shooting', 'language', 'an already combustible situation', 'the White House', 'advisers', 'a speech', 'the Oval Office', 'the White House', 'the national temperature', 'Trump', 'interest', 'a speech', 'the nation', 'a person', 'the White House', 'some administration officials', 'a mistake', 'A senior White House aide', 'governors', 'mayors', 'the ones', 'the destruction', 'their respective cities', 'states', 'Trump', 'who', 'days', 'local leaders', 'the National Guard', 'violence', 'a heated phone call', 'governors', 'Monday morning', 'Trump', 'responsibility', 'the governors', 'the national crisis', 'them', 'their responses', 'Other White House officials', 'the weekend', 'something', 'an Oval Office address', 'a person', 'concern', 'such a speech', 'the situation', 'it', 'aides', 'the situation', 'Trump', 'violent rhetoric', 'the deliberations', 'one official', 'Some advisers', 'a presidential address', 'calm', "Trump's own penchant", 'escalation', 'instigation', 'It', 'such a speech', 'Monday morning', '"A national Oval Office address', 'Antifa', 'White House press secretary Kayleigh McEnany', 'an appearance', 'Fox News', 'Trump', 'the killing', 'George Floyd', 'a black Minneapolis man', 'who', 'a white police officer', 'his neck', 'an arrest', 'President', 'she', 'McEnany', 'Trump\'s "focus', 'our streets']
    


```python
print("Verbs:", [token.lemma_ for token in parsed if token.pos_ == "VERB"])
```

    Verbs: ['declare', 'disperse', 'could', 'visit', 'amount', 'charge', 'come', 'come', 'demonstrate', 'tear', 'declare', 'speak', 'disperse', 'use', 'see', 'pour', 'ease', 'spread', 'spread', 'walk', 'use', 'burn', 'say', 'hold', 'surround', 'gather', 'gate', 'mandate', 'include', 'see', 'drive', 'say', 'commit', 'uphold', 'mobilize', 'end', 'defend', 'say', 'swear', 'uphold', 'will', 'strike', 'say', 'would', 'use', 'include', 'threaten', 'invoke', 'use', 'date', 'ensure', 'end', 'declare', 'would', 'deploy', 'bring', 'say', 'would', 'serve', 'die', 'arrest', 'rage', 'should', 'address', 'spread', 'grow', 'feel', 'grumble', 'allow', 'pass', 'address', 'make', 'do', 'tweet', 'mention', 'schedule', 'go', 'fan', 'reach', 'push', 'would', 'confront', 'watch', 'worry', 'inflict', 'could', 'imperil', 'encourage', 'use', 'encourage', 'use', 'say', 'address', 'fall', 'say', 'come', 'ensure', 'register', 'add', 'support', 'hear', 'see', 'say', 'watch', 'man', 'devastate', 'destroy', 'measure', 'stand', 'include', 'blame', 'vow', 'grow', 'say', 'help', 'say', 'speak', 'describe', 'seek', 'convince', 'use', 'write', 'start', 'start', 'could', 'inflame', 'would', 'appear', 'remain', 'deliver', 'would', 'help', 'lower', 'express', 'deliver', 'say', 'believe', 'would', 'say', 'should', 'respond', 'share', 'spend', 'go', 'call', 'crack', 'place', 'resolve', 'say', 'appear', 'argue', 'say', 'could', 'inflame', 'make', 'debate', 'confront', 'weigh', 'say', 'wonder', 'call', 'would', 'erase', 'seem', 'go', 'stop', 'say', 'note', 'address', 'die', 'address', 'say', 'say', 'act', 'keep']
    


```python
print("Adj:", [token.lemma_ for token in parsed if token.pos_ == "ADJ"])
```

    Adj: ['peaceful', 'tear', 'nearby', 'discordant', 'recent', 'presidential', 'nationwide', 'racial', 'ideological', 'political', 'constant', 'steady', 'nearby', 'peaceful', 'peaceful', 'tear', 'several', 'american', 'more', 'great', 'large', 'military', 'military', 'first', 'high', 'great', 'american', 'entire', 'presidential', 'violent', 'armed', 'military', 'unarmed', 'black', 'white', 'frustrated', 'many', 'traditional', 'conservative', 'several', 'formal', 'democratic', 'local', 'unnoticed', 'second', 'outside', 'recent', 'closed', 'underground', 'major', 'historic', 'agitated', 'aggressive', 'agitated', 'aggressive', 'familiar', 'flat', 'unrelated', 'few', 'last', 'peaceful', 'first', 'good', 'stark', 'severe', 'congressional', 'republican', 'inflammatory', 'constructive', 'violent', 'combustible', 'presidential', 'divided', 'national', 'close', 'senior', 'respective', 'least', 'local', 'heated', 'national', 'weak', 'other', 'formal', 'familiar', 'well', 'back', 'violent', 'measured', 'presidential', 'own', 'imminent', 'national', 'black', 'white', 'several', 'safe']
    

## Word Frequency Weight Generation


```python
## Find most frequent nouns, give them more weight for each instance
basic_frequency = {}
for noun in [chunk.text for chunk in parsed.noun_chunks]:
    noun = noun.lower()
    if noun not in basic_frequency.keys():
        basic_frequency[noun] = 1
    else:
        basic_frequency[noun] += 1
# Most common words
sorted(basic_frequency.items(), key=lambda x: x[1], reverse=True)[:20]
```




    [('trump', 18),
     ('he', 11),
     ('the white house', 5),
     ('the weekend', 5),
     ('governors', 4),
     ('the situation', 4),
     ('george floyd', 3),
     ('who', 3),
     ('what', 3),
     ('a speech', 3),
     ('himself', 2),
     ('order', 2),
     ('peaceful protesters', 2),
     ('the white house gates', 2),
     ('tear gas', 2),
     ('flash bangs', 2),
     ('rubber bullets', 2),
     ('george floyd protests', 2),
     ('aides', 2),
     ('president', 2)]




```python
## Find most frequent nouns, give them more weight for each instance and their length
length_ranked_frequency = {}
for noun in [chunk.text for chunk in parsed.noun_chunks]:
    noun = noun.lower()
    if noun not in length_ranked_frequency.keys():
        length_ranked_frequency[noun] = len(noun) * len(noun)
    else:
        length_ranked_frequency[noun] += len(noun)* len(noun)
# Most common words, longer is better
sorted(length_ranked_frequency.items(), key=lambda x: x[1], reverse=True)[:20]
```




    [('the most highly charged and discordant moments', 2116),
     ('white house press secretary kayleigh mcenany', 1936),
     ('racial, ideological and political lines', 1521),
     ("the president's traditional defenders", 1369),
     ('his entire presidential prerogative', 1225),
     ('democratic state and local leaders', 1156),
     ('the white house', 1125),
     ('the first manned us space launch', 1024),
     ('an already combustible situation', 1024),
     ('a white police officer', 968),
     ('"a national oval office address', 961),
     ('the white house gates', 882),
     ('george floyd protests', 882),
     ('mobilizing military resources', 841),
     ('some administration officials', 841),
     ('a previously scheduled event', 784),
     ('recent presidential history', 729),
     ('nationwide unrest escalates', 729),
     ("st. john's episcopal church", 729),
     ('other white house officials', 729)]




```python
## Find most frequent nouns, give them more weight for each instance and their brevity
inverse_length_ranked_frequency = {}
for noun in [chunk.text for chunk in parsed.noun_chunks]:
    noun = noun.lower()
    if len( noun ) < 5 :
        continue
    if len( noun ) > 20: 
        continue
    if noun not in inverse_length_ranked_frequency.keys():
        inverse_length_ranked_frequency[noun] = 20 - len(noun)
    else:
        inverse_length_ranked_frequency[noun] += 20 - len(noun)
# Most common words, longer is better
sorted(inverse_length_ranked_frequency.items(), key=lambda x: x[1], reverse=True)[:20]
```




    [('trump', 270),
     ('the weekend', 45),
     ('governors', 44),
     ('a speech', 36),
     ('order', 30),
     ('aides', 30),
     ('the situation', 28),
     ('antifa', 28),
     ('himself', 26),
     ('the white house', 25),
     ('tear gas', 24),
     ('george floyd', 24),
     ('his neck', 24),
     ('violence', 24),
     ('a person', 24),
     ('president', 22),
     ('thousands', 22),
     ('the nation', 20),
     ('protesters', 20),
     ('flash bangs', 18)]



## Sentence Procurement


```python
## Rank each sentence and find the best one given a frequency table
def get_best_sentences ( frequency ):
    scores = []
    for sentence in parsed.sents:
        score = 0
        for noun in sentence.noun_chunks:
            noun = noun.text.lower()
            if noun in frequency.keys():
                score += frequency[noun]
        scores.append( (score, sentence) )
    return '\n\n'.join([ a[1].text for a in sorted(scores, reverse=True)][:3])
```


```python
print( get_best_sentences( basic_frequency))
```

    In striking terms, Trump said he would use his entire presidential prerogative -- including threatening to invoke a rarely used law dating back to 1807 -- to ensure violent protests end, declaring he would deploy "thousands and thousands of heavily armed soldiers, military personnel and law enforcement officers" to bring order..
    
    Over the weekend, some aides sought to convince Trump not to use violent rhetoric after he wrote on Twitter that "when the looting starts the shooting starts," warning language like that could inflame an already combustible situation and would not appear presidential..
    
    Trump said justice would be served for George Floyd, the unarmed black man who died after a white police officer knelt on his neck as he was being arrested..
    


```python
print( get_best_sentences( length_ranked_frequency ))
```

    "A national Oval Office address is not going to stop Antifa," White House press secretary Kayleigh McEnany said in an appearance Monday on Fox News, noting that Trump had addressed the killing of George Floyd -- a black Minneapolis man who died after a white police officer knelt on his neck during an arrest -- several times already..
    
    The episode, which amounted to one of the most highly charged and discordant moments in recent presidential history, came as nationwide unrest escalates and Trump comes under pressure to demonstrate a modicum of conciliation for a country torn along racial, ideological and political lines..
    
    In striking terms, Trump said he would use his entire presidential prerogative -- including threatening to invoke a rarely used law dating back to 1807 -- to ensure violent protests end, declaring he would deploy "thousands and thousands of heavily armed soldiers, military personnel and law enforcement officers" to bring order..
    


```python
print( get_best_sentences( inverse_length_ranked_frequency ))
```

    President Donald Trump declared himself "your president of law and order" during remarks Monday as peaceful protesters just outside the White House gates were dispersed with tear gas, flash bangs and rubber bullets, apparently so Trump could visit a nearby church..
    
    Trump has expressed interest in delivering a speech to the nation, a person close to the White House said, but some administration officials believe that would be a mistake.
    
    "A national Oval Office address is not going to stop Antifa," White House press secretary Kayleigh McEnany said in an appearance Monday on Fox News, noting that Trump had addressed the killing of George Floyd -- a black Minneapolis man who died after a white police officer knelt on his neck during an arrest -- several times already..
    

## Sentence Procurement by uniqueness


```python
## Rank each sentence and find the best two sentences with unique words given a frequency table
def get_unique_sentences ( f ):
    frequency = f.copy()
    # Find the best result
    scores = []
    for sentence in parsed.sents:
        score = 0
        for noun in sentence.noun_chunks:
            noun = noun.text.lower()
            if noun in frequency.keys():
                score += frequency[noun]
        scores.append( (score, sentence) )
    best = sorted(scores, reverse=True)[0]
    
    # Remove weights from words selected
    for noun in best[1].noun_chunks:
        noun = noun.text.lower()
        if noun in frequency.keys():
            frequency[noun] = 0
            
    # Get next sentence 
    scores = []
    for sentence in parsed.sents:
        score = 0
        for noun in sentence.noun_chunks:
            noun = noun.text.lower()
            if noun in frequency.keys():
                score += frequency[noun]
        scores.append( (score, sentence) )
    best2 = sorted(scores, reverse=True)[0]
    return best[1].text + '\n\n' + best2[1].text
```


```python
print( get_unique_sentences( basic_frequency))
```

    In striking terms, Trump said he would use his entire presidential prerogative -- including threatening to invoke a rarely used law dating back to 1807 -- to ensure violent protests end, declaring he would deploy "thousands and thousands of heavily armed soldiers, military personnel and law enforcement officers" to bring order..
    
    "A national Oval Office address is not going to stop Antifa," White House press secretary Kayleigh McEnany said in an appearance Monday on Fox News, noting that Trump had addressed the killing of George Floyd -- a black Minneapolis man who died after a white police officer knelt on his neck during an arrest -- several times already..
    


```python
print( get_unique_sentences( length_ranked_frequency ))
```

    "A national Oval Office address is not going to stop Antifa," White House press secretary Kayleigh McEnany said in an appearance Monday on Fox News, noting that Trump had addressed the killing of George Floyd -- a black Minneapolis man who died after a white police officer knelt on his neck during an arrest -- several times already..
    
    The episode, which amounted to one of the most highly charged and discordant moments in recent presidential history, came as nationwide unrest escalates and Trump comes under pressure to demonstrate a modicum of conciliation for a country torn along racial, ideological and political lines..
    


```python
print( get_unique_sentences( inverse_length_ranked_frequency ))
```

    President Donald Trump declared himself "your president of law and order" during remarks Monday as peaceful protesters just outside the White House gates were dispersed with tear gas, flash bangs and rubber bullets, apparently so Trump could visit a nearby church..
    
    One person familiar with the matter said there is a sense among allies that an attempt to address the situation in a speech over the weekend fell completely flat.
    

### Conclusion
- 6 different ways to generate 2-3 sentence summaries of a text by choosing the most important sentences from within the text
---
3 ways to generate word ranking
- Pure frequency ( more instances of the word the better )
- Frequency + Length ( more instances and longer words are better )
- Frequency + Inverse Length ( more instnaces and shorter words are better )
---
2 ways to compile summary
- Top ranked sentences by frequency
- Top ranked sentence by frequency + next best sentence that does not share the same most common words


```python

```
