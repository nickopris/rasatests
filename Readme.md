https://rasa.com/docs/core/installation/


Run this to train with Markdown file:

    curl --request POST --header 'content-type: application/x-yml' --data-binary @config_train_server_md.yml --url 'localhost:5000/train?project=test_model'

Then query like this:

    curl 'http://localhost:5000/parse?q=bye&amp;project=test_model'

It should reply with `goodbye` intent high confidence score

    curl 'http://localhost:5000/parse?q=I%20really%20need%20to%20know&amp;project=test_model'

It should reply with `learning` intent high confidence score


#Training file (markdown format)
config_train_server_md.yml
See also: https://rasa.com/docs/nlu/dataformat/
See also: https://github.com/RasaHQ/rasa-nlu-trainer 

    language: "en"
    
    pipeline: "spacy_sklearn"
    
    data: |    
      ## intent:goodbye
      - bye
      - goodbye
    
      ## intent:learning
      - how do I
      - teach me about
      - I need to know
      - do you know how to


#Training with JSON format
    curl 'https://raw.githubusercontent.com/RasaHQ/rasa_nlu/master/sample_configs/config_train_server_json.yml' | \
    curl --request POST --header 'content-type: application/x-yml' --data-binary @- --url 'localhost:5000/train?project=test_model'

See file attached for a local JSON file.
    
    curl --request POST --header 'content-type: application/x-yml' --data-binary @config_train_server_json.yml --url 'localhost:5000/train?project=test_model'

#HTTP API
See: https://rasa.com/docs/nlu/http/
- delete models:

    curl -X DELETE localhost:5000/models?project=test_model&model=model_XXXX

#Troubleshooting

`The server can't train more models right now!`

See: https://github.com/RasaHQ/rasa_nlu/issues/1323



# Duckling
https://hub.docker.com/r/rasa/duckling/

`$ curl -XPOST http://0.0.0.0:8000/parse --data 'locale=en_GB&amp;text=tomorrow at eight'`

#Rasa nlu
https://hub.docker.com/r/rasa/rasa_nlu/


If wget not installed on Mac:
`brew install wget --with-libressl`

#to check
https://github.com/paschmann/rasa-ui
https://www.quora.com/What-are-good-ways-to-automatically-find-synonyms-using-machine-learning-ML-techniques-What-are-good-ways-to-automatically-find-antonyms-using-ML-techniques

