## RESTful API built with flask

### Setup & Installation

Using Python 3.7+, run the following command lines in the terminal

`$ git clone https://github.com/ZGZOO/flask-api.git`

`$ cd flask-api`

`$ python3 -m pip install -r requirements.txt` (to install the dependencies)

#### Dependencies & Libraries

```
aniso8601==9.0.1
click==8.0.3
Flask==2.0.2
Flask-RESTful==0.3.9
Flask-SQLAlchemy==2.5.1
greenlet==1.1.2
itsdangerous==2.0.1
Jinja2==3.0.2
MarkupSafe==2.0.1
pytz==2021.3
six==1.16.0
SQLAlchemy==1.4.25
Werkzeug==2.0.2
```

### Running the app

Run the following command lines in the terminal

`$ export FLASK_APP=api`

`$ flask seed_data` (seed the data I prepared so you can play around with this API)

`$ flask run` (start this API server)

```
 * Serving Flask app 'api' (lazy loading)
 * Environment: production
   WARNING: This is a development server. Do not use it in a production deployment.
   Use a production WSGI server instead.
 * Debug mode: off
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
```

If the above block shows up in your terminal, then it means the server is running!

### Database Related Tools

- Flask-SQLAlchemy
- SQLAlchemy
- sqlite (local db system)
- DB Browser for SQLite (a helpful visual tool to see the db)

### Model

| Model         | Description                                                       |
| ------------- | ----------------------------------------------------------------- |
| TodoNoteModel | A todo note with a title, and a list of todo items                |
| TodoItemModel | A todo item with a task name, and a boolean of if it is completed |

| Relationship | Description                                                                  |
| ------------ | ---------------------------------------------------------------------------- |
| One to Many  | One todo note has many todo items; A todo item only belongs to one todo note |

![ER Diagram](https://res.cloudinary.com/headincloud/image/upload/v1634596939/Database_ER_diagram_Todo_List_wtp3sd.png)

### Architecture/system diagram

![System Diagram](https://res.cloudinary.com/headincloud/image/upload/v1634598742/Backend_Server_system_diagram_rjizj0.png)

### API

| Request                                                | URL                                                                      | HTTP Verb | Query string parameters                      | Response                                                                                         |
| ------------------------------------------------------ | ------------------------------------------------------------------------ | --------- | -------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| create a Todo Note                                     | /notes                                                                   | POST      | title: a string representing the title       | create a new Todo Note with a title                                                              |
| show a list of all Todo Notes                          | /notes                                                                   | GET       | N/A                                          | return a list of Todo Notes                                                                      |
| delete Notes                                           | /notes                                                                   | DELETE    | N/A                                          | delete all Todo Notes in the database                                                            |
| show a specific Todo Note based on id                  | /notes/&lt;int:todo_note_id&gt;                                          | GET       | N/A                                          | return a single Todo Note based on id                                                            |
| update a specific Todo Note based on id                | /notes/&lt;int:todo_note_id&gt;                                          | PUT       | title: a string representing the title       | return the updated Todo Note based on id                                                         |
| delete a single Note                                   | /notes/&lt;int:todo_note_id&gt;                                          | DELETE    | N/A                                          | delete a single Todo Note in the database                                                        |
| complete Todos for a note                              | /notes/&lt;int:todo_note_id&gt;/completed                                | PUT       | N/A                                          | return all the updated Todo Items to be completed for a specific Todo Note based on todo_note_id |
| add Todos to a note                                    | /notes/&lt;int:todo_note_id&gt;/items                                    | POST      | task: a string representing the task of item | create a new Todo Item to a specific Todo Note based on todo_note_id                             |
| list all Todos                                         | /notes/&lt;int:todo_note_id&gt;/items                                    | GET       | N/A                                          | list all Todo Items of a specific Todo Note based on todo_note_id                                |
| delete Todos                                           | /notes/&lt;int:todo_note_id&lt;/items                                    | DELETE    | N/A                                          | delete all Todo Items of a specific Todo Note based on todo_note_id in the database              |
| show a specific Todo Item based on item_id of a note   | /notes/&lt;int:todo_note_id&gt;/items/&lt;int:todo_item_id&gt;           | GET       | N/A                                          | return a specific Todo Item based on item_id of a note                                           |
| update a specific Todo Item based on item_id of a note | /notes/&lt;int:todo_note_id&gt;/items/&lt;int:todo_item_id&gt;           | PUT       | task: a string representing the task of item | return the updated a specific Todo Item based on item_id of a note                               |
| delete a single Todo                                   | /notes/&lt;int:todo_note_id&gt;/items/&lt;int:todo_item_id&gt;           | DELETE    | N/A                                          | delete a single Todo Item of a Todo Note in the database                                         |
| complete a Todo of a note                              | /notes/&lt;int:todo_note_id&gt;/items/&lt;int:todo_item_id&gt;/completed | PUT       | N/A                                          | return the updated Todo Item to be completed for a specific Todo Note based on todo_note_id      |

### Test the API using Postman

- GET example
  ![GET example](https://res.cloudinary.com/headincloud/image/upload/v1634612953/GET_example_lirdge.png)

- DELETE example
  ![DELETE example](https://res.cloudinary.com/headincloud/image/upload/v1634613091/DELETE_example_ndjmdc.png)

- PUT example
  ![PUT example](https://res.cloudinary.com/headincloud/image/upload/v1634613224/PUT_example_y8rl28.png)

- POST example
  ![POST example](https://res.cloudinary.com/headincloud/image/upload/v1634613333/POST_example_f9wwpz.png)
