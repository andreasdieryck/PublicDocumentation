# Ideas of the day

The principle of the ideas of the day is to get new popular-random text-image cards, the ideas, for the intentions you want to express for the people you want to.
These ideas are great things to push up front in your application when a user starts.

You can actually get theses ideas in different ways:

* [get cards for a predefined selection of intentions](#ByIntention):
  * [http://api.cvd.io/popular/stickers/IdeasOfTheDay/ByIntention](http://api.cvd.io/popular/stickers/IdeasOfTheDay/ByIntention)
* [get cards for some recipient](#ForRecipient) (and the usual intentions associated with this recipient):
  * [http://api.cvd.io/popular/stickers/IdeasOfTheDay/forRecipient/Mother](http://api.cvd.io/popular/stickers/IdeasOfTheDay/forRecipient/Mother)
  
<a name="ByIntention">
By Intention
------------
 
 By default you'll get one card suggestion by intention for the predefined list of intentions for the Ideas of the Day (you can get the list
 at [http://api.cvd.io/IdeaOfTheDay/intentions](http://api.cvd.io/IdeaOfTheDay/intentions).
 
### Endoint:
 
    GET http://api.cvd.io/popular/{area}/IdeasOfTheDay/ByIntention?{options}
    
### Definitions:

Path:

* area : the name of your app area (not relevant for the search)
    
Options: 

* culture : string, 'en-EN' | 'fr-FR' | 'es-ES', by default the culture will be automatically picked from the http headers
* nbcards : int, the number of cards ideas to return for each intention, 1 by default
* new: when set to true, it avoids the cache and forces a refresh
* deviceid: the device id of the user doing the request (not used actually but it will in the future to get more accurate suggestions for the user)
 
Response:

* array of [cardIdea](#ObjectDefinitions)

Notes:

This api is available through your browser to have a better looking of the cards than in a json api.



<a name="ForRecipient">
For recipient
------------

This api will get you some ideas of things to say to someone, targeting a recipient you define in parameter. You may also provide the gender
of the current user asking for ideas in order to get even more accurate ideas.

exemple, assuming I'm a man, I want new ideas to say something to my mum in french, give me 3 ideas for each intention:

    GET http://api.cvd.io/popular/stickers/IdeasOfTheDay/forRecipient/Mother?culture=fr-Fr&senderGender='M'&nbcards=3
    Resonse:  array of [cardIdea](#ObjectDefinitions)
    
### Endoint:
 
    GET http://api.cvd.io/popular/{area}/IdeasOfTheDay/forRecipient/{recipient}?{options}
    
### Definitions:

Path:

* area : string, the name of your app area (not relevant for the search)
* recipient : string, a recipient name. you'll find a full list of recipients with their intentions here : [http://api.cvd.io/popular/stickers/IdeasOfTheDay/intentionforrelations](http://api.cvd.io/popular/stickers/IdeasOfTheDay/intentionforrelations)
 
Options: 

* senderGender: string, the gender of the user requesting the ideas ('H'|'M'|'Male  or  'F'|'Female'), by default 'I' (unknown)
* culture : string, 'en-EN' | 'fr-FR' | 'es-ES'
* nbcards : int, the number of cards ideas to return for each intention, 1 by default
* new: when set to true, it avoids the cache and forces a refresh
* deviceid: the device id of the user doing the request (not used actually but it will in the future to get more accurate suggestions for the user)

Response:

* array of [cardIdea](#ObjectDefinitions)
 

Notes:

This api is available through your browser to have a better looking of the cards than in a json api.



<a name="ObjectDefinitions">
### Response objects details:

- **CardIdea** : It defines the properties of the card you'll get as response:
     -  "IntentionId": string, id of the intention expressed in the card
     - "PrototypeId": string, id of the prototype of the text
     - "TextId": string, id of the text
     - "Content": string, content of the text
     - "ImageName": string, name of the suggested image (a popular one for this text)
     - "ImageLink": string, image link
     - "Sender": string, can be ("H","F","I","N")
     - "Recipient": string, can be ("H","F","I","N")

      