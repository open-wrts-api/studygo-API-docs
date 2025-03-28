# Note: Dit is geen licentie, zie echtelicentie voor de echte licentie
---

# SG Forum API Docs

## **qna/questions**  
Geeft de homepagina van het forum (geen authenticatie nodig).  
**URL:**  
```plaintext
https://api.wrts.nl/api/v3/public/qna/questions
```

---

## **qna/questions/id**  
Geeft de inhoud en antwoorden van een post op het forum (geen authenticatie nodig).  
**URL:**  
```plaintext
https://api.wrts.nl/api/v3/public/qna/questions/jouw_prachtige_forum_post_id
```

Vervang hierbij `jouw_prachtige_forum_post_id` met jouw post-ID, bijvoorbeeld: `520564`.

---

## **qna/questions (POST)**  
Maak een post op het forum door een POST-verzoek te sturen naar:  
```plaintext
https://api.wrts.nl/api/v3/qna/questions
```

Hiervoor is een token nodig en een body die er zo uitziet:  

```json
{
   "qna_question": {
      "contents": "Wat is de meest effectieve strategie die je hebt gebruikt om je schoolwerk georganiseerd te houden, en waarom denk je dat deze aanpak zo goed werkt?",
      "qna_attachments_attributes": [],
      "subject_id": 3
   }
}
```

### Uitleg:
- **contents**: De vraag die je wilt stellen.
- **qna_attachments_attributes**: heel eerlijk idk.
- **subject_id**: ID van het vak dat je wilt oefenen (zie `vakken.js`).

---

## **Zoeken (erg lang)**  
Werkt net als "home", maar dan met zoeken (geen authenticatie nodig).  

**URL:**  
```plaintext
https://api.wrts.nl/api/v3/public/qna/questions?search_terms=test&status=unanswered&grade_number=1&school_track_id=12&school_track_name=vmbo-t&subject_id=3
```

### Parameters:
- **search_terms**: Wat je wilt zoeken.
- **status** (optioneel):  
  - `unanswered`: Onbeantwoorde vragen.  
  - `correct_answer`: Vragen beantwoord door een tutor.  
  - `answered`: Beantwoorde vragen.  
- **grade_number**: De klas waarin de vraagsteller zit (optioneel).  
- **school_track_id**: Iets met het type school van de vraagsteller (optioneel).  
- **school_track_name**: Naam van het type school van de vraagsteller (lijkt niets te doen) (optioneel).  
- **subject_id**: ID van het vak dat je wilt oefenen (zie `vakken.js`) (optioneel).  

---

## **qna/questions/answers**  
Beantwoord een forumpost door een POST-verzoek te sturen naar:  

**URL:**  
```plaintext
https://api.wrts.nl/api/v3/qna/questions/forum_post_id/answers
```

Vervang hierbij `forum_post_id` met de ID van de forumpost, bijvoorbeeld: `520564`.

### Body:
```json
{
  "qna_answer": {
    "body": "mijn geweldige antwoord",
    "qna_attachments_attributes": []
  }
}
```

### Uitleg:
- **body**: De tekst van jouw antwoord.
- **qna_attachments_attributes**: heel eerlijk idk.
