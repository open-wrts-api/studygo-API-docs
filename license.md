# note: dit is geen license zie echtelicense
-----
# SG forum api docs
## qna_questions  
Geeft de homepagina van het forum (geen authenticatie nodig).  
URL: ```https://api.wrts.nl/api/v3/public/qna/questions```  

## qna_questions_id  
Geeft de inhoud en antwoorden van een post op het forum (geen authenticatie nodig).  
URL: ```https://api.wrts.nl/api/v3/public/qna/questions/jouw_prachtige_forum_post_id```  
Vervang hierbij ```jouw_prachtige_forum_post_id``` met jouw post-ID, bijvoorbeeld: ```520564```  

## qna_questions (POST)  
Als je een POST-verzoek stuurt naar ```https://api.wrts.nl/api/v3/qna/questions``` met een token en een body die er zo uitziet:  

```json
{
   "qna_question": {
      "contents": "Wat is de meest effectieve strategie die je hebt gebruikt om je schoolwerk georganiseerd te houden, en waarom denk je dat deze aanpak zo goed werkt?",
      "qna_attachments_attributes": [],
      "subject_id": 3
   }
}
```

Maak je een post op het forum. Hierbij is ```subject_id``` gelijk aan de ID van het vak dat je wilt oefenen (zie vakken.js) en ```contents``` de vraag.
## Zoeken (erg lang)

Werkt net als "home", maar dan met zoeken (geen authenticatie nodig).

```plaintext
https://api.wrts.nl/api/v3/public/qna/questions?search_terms=test&status=unanswered&grade_number=1&school_track_id=12&school_track_name=vmbo-t&subject_id=3
```

### Parameters:
- **search_terms**: Wat je wilt zoeken.
- **status** (optioneel): 
  - `unanswered`: Onbeantwoorde vragen.
  - `correct_answer`: Vragen beantwoord door een tutor.
  - `answered`: beantwoorde vragen.
- **grade_number**: De klas waarin de vraagsteller zit (optioneel).
- **school_track_id**: Iets met het type school van de vraagsteller (optioneel).
- **school_track_name**: Naam van het type school van de vraagsteller (lijkt niets te doen) (optioneel).
- **subject_id**: ID van het vak dat je wilt oefenen (zie `vakken.js`) (optioneel).
