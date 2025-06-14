# Open Notebook API Plan

We are leaving Podcasts out of the scope for now since we will update this funcionality and replace it with a new module soon. 

# COMPLETED


## Sources API

### GET /api/sources
Get sources
- Parameters: notebook_id (string, optional)
- Pages: 2_📒_Notebooks.py, stream_app/source.py

### POST /api/sources
Add new source
- Parameters: notebook_id (string), type (link/upload/text), url (string), file (multipart for uploads), content (string), transformations (array), embed (boolean), delete_source (boolean)
- Pages: stream_app/source.py

### GET /api/sources/{id}
Get source details
- Parameters: id (string)
- Pages: components/source_panel.py

### PUT /api/sources/{id}
Update source metadata
- Parameters: id (string), title (string)
- Pages: components/source_panel.py

### DELETE /api/sources/{id}
Delete source
- Parameters: id (string)
- Pages: components/source_panel.py

## Settings API

### GET /api/settings
Get all application settings
- Parameters: setting_group (string, optional) - filter by group like "default_models", "default_prompts", "content_settings"
- Pages: 7_🤖_Models.py, 8_💱_Transformations.py, 10_⚙️_Settings.py

### PUT /api/settings
Update settings by group
- Parameters: setting_group (string), settings (object) - JSON object with key-value pairs to update
- Pages: 7_🤖_Models.py, 8_💱_Transformations.py, 10_⚙️_Settings.py

## Context API

### GET /api/context
Get context for notebook
- Parameters: notebook_id (string), context_config (object)
- Pages: stream_app/chat.py



## Models API

### GET /api/models
List all configured models
- Parameters: type (string)
- Pages: 7_🤖_Models.py

### POST /api/models
Add new model
- Parameters: name (string), provider (string), type (string)
- Pages: 7_🤖_Models.py

### DELETE /api/models/{id}
Delete model
- Parameters: id (string)
- Pages: 7_🤖_Models.py


## Transformations API

### GET /api/transformations
List all transformations
- Parameters: none
- Pages: 8_💱_Transformations.py

### POST /api/transformations
Create new transformation
- Parameters: name (string), title (string), description (string), prompt (string), apply_default (boolean)
- Pages: 8_💱_Transformations.py

### GET /api/transformations/{id}
Get transformation details
- Parameters: id (string)
- Pages: 8_💱_Transformations.py

### PUT /api/transformations/{id}
Update transformation
- Parameters: id (string), name (string), title (string), description (string), prompt (string), apply_default (boolean)
- Pages: 8_💱_Transformations.py

### DELETE /api/transformations/{id}
Delete transformation
- Parameters: id (string)
- Pages: 8_💱_Transformations.py

### POST /api/transformations/execute
Execute transformation on content
- Parameters: transformation_id (string), input_text (string), model_id (string)
- Pages: 8_💱_Transformations.py

## Notebooks API

### GET /api/notebooks
List all notebooks
- Parameters: archived (boolean), order_by (string)
- Pages: 2_📒_Notebooks.py

### POST /api/notebooks
Create new notebook
- Parameters: name (string), description (string)
- Pages: 2_📒_Notebooks.py

### GET /api/notebooks/{id}
Get specific notebook details
- Parameters: id (string)
- Pages: 2_📒_Notebooks.py

### PUT /api/notebooks/{id}
Update notebook
- Parameters: id (string), name (string), description (string), archived (boolean)
- Pages: 2_📒_Notebooks.py

### DELETE /api/notebooks/{id}
Delete notebook
- Parameters: id (string)
- Pages: 2_📒_Notebooks.py


## Search API

### POST /api/search
Search across knowledge base
- Parameters: query (string), type (text/vector), limit (integer), search_sources (boolean), search_notes (boolean)
- Pages: 3_🔍_Ask_and_Search.py

### POST /api/search/ask
Ask knowledge base with AI
- Parameters: question (string), strategy_model (string), answer_model (string), final_answer_model (string)
- Pages: 3_🔍_Ask_and_Search.py



## Notes API

### GET /api/notes
Get notes
- Parameters: notebook_id (string, optional)
- Pages: 2_📒_Notebooks.py, stream_app/note.py

### POST /api/notes
Create new note
- Parameters: notebook_id (string), title (string), content (string), note_type (string)
- Pages: stream_app/note.py

### GET /api/notes/{id}
Get note details
- Parameters: id (string)
- Pages: components/note_panel.py

### PUT /api/notes/{id}
Update note
- Parameters: id (string), title (string), content (string)
- Pages: components/note_panel.py

### DELETE /api/notes/{id}
Delete note
- Parameters: id (string)
- Pages: components/note_panel.py

## Embedding API

### POST /api/embed
Embed content for vector search
- Parameters: item_id (string), item_type (string)
- Pages: components/source_panel.py, components/note_panel.py


