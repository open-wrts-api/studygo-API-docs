
# Update
SG heeft captcha's toegevoegt aan een paar endpoints en ik ga niet verder met het onderhouden van deze docs


# studygo onofficel API docs
voor forum zie het license tabblad in github
## get_token
met get_token kan je een x-auth-token genareren door een post verzoek te doen naar https://api.wrts.nl/api/v3/auth/get_token met een email en wachtwoord
bijvoorbeeld:

curl 'https://api.wrts.nl/api/v3/auth/get_token' --compressed -X POST -H 'Accept: application/json, text/plain, */*' -H 'Content-Type: application/json' -H 'X-Client-Type: web' --data-raw '{"email":"email","password":"wachtwoord"}'

de uitkomst is bijv deze JSON

    {
    
    "success":  true,
    
    "auth_token":  "token",
    
    "expires_at":  1739026504,
    
    "renew_from":  1739026504
    
    }
   
   ## get_user_data
   met get_user_data kan je algemenen info over jouw acount.
   ik ga vanaf nu laten zien hoe je de API kan gebruiken met curl je kan dit vertalen met [deze website](https://curlconverter.com/)

       curl --location 'https://api.wrts.nl/api/v3/get_user_data' \
    --header 'x-auth-token: jouw_token'

## lists
met lists kan je openbare lijsten bekijken hier is geen auth token voor nodig

    curl --location 'https://api.wrts.nl/api/v3/public/lists/180557958'
vervang hierbij 180557958 met jouw lijst ID je kan een lijst ID zien in de URL
van een lijst zo is de URL voor deze lijst hierbij is het getal belangerijk en verder niks zo is studygo-api aleen de naam van de lijst

    https://studygo.com/nl/learn/lists/180557958/studgo-api
## groups/practiceable_items
met groups/practiceable_items kan je lijsten en andere info van een groep krijgen
je kan het gebruiken met 

        curl --location 'https://api.wrts.nl/api/v3/groups/groep_ID/practiceable_items' \
    --header 'x-auth-token: jouw_token'
vervang hierbij groep_ID met jouw groeps ID je kan die vinden in de URL van de groep 

    https://studygo.com/nl/learn/groups/347718/exercises
hier bij is 347718 de goeps ID

## items_overview
je kan items_overview gebruiken om de info op de home pagina van studygo te gebruiken inclusief lijst IDs

    curl --location 'https://api.wrts.nl/api/v3/items_overview' \
    --header 'x-auth-token: jouw_token'
## search
je kan zoeken op studygo met

    curl --location 'https://api.wrts.nl/api/v3/search?apply_default_filters=true&search_terms=APPELSAP&limit=5&offset=0' \
    --header 'x-auth-token: jouw_token'
in dit voorbeeld word er op APPELSAP gezocht vervang hierbij dus APPELSAP om ergen anders op te zoeken
