## 👨‍💻 Built with
<img src="https://img.shields.io/badge/Python-FFD43B?style=for-the-badge&logo=python&logoColor=blue" /> <img src="https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white"/> <img src="https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white" /> <img src="https://img.shields.io/badge/Jupyter-F37626.svg?&style=for-the-badge&logo=Jupyter&logoColor=white" /> <img src="https://img.shields.io/badge/Pandas-2C2D72?style=for-the-badge&logo=pandas&logoColor=white" /> <img src="https://img.shields.io/badge/Numpy-777BB4?style=for-the-badge&logo=numpy&logoColor=white" />

##  Descripction about project
In this project I used [IMDb Datasets](https://www.imdb.com/interfaces/) to get information about movies.

This data is saved in TSV files. In this project is created a jupyter notebook to get data from url and save it in PostgreSQL. Notebook is named **creating_db.ipynb**. After creating DB it is time to analyse data, notebook named **analyse_imbd_dataset.ipynb**

This project was focused to check the best movies and series of all time, the best movies by year, actors and directors taking part in the highest rated movies, etc. All analisys you can check in notebook.

### Project using 2 Docker containers:

- **Container with PosgreSQL**

- **Container Jupyter Notebook**
    - Notebook created to analyse data used libraries: 
      - pandas
      - numpy
      - matplotlib
      - seaborn
      - sqlalchemy
      - wordcloud

## 📚Data

4 datasets were taken for analysis from IMDb:

- **title.basics.tsv.gz** - Contains the following information for titles:
   - tconst (string) - alphanumeric unique identifier of the title
   - titleType (string) – the type/format of the title (e.g. movie, short, tvseries, tvepisode, video, etc)
   - primaryTitle (string) – the more popular title / the title used by the filmmakers on promotional materials at the point of release
   - originalTitle (string) - original title, in the original language
   - isAdult (boolean) - 0: non-adult title; 1: adult title
   - startYear (YYYY) – represents the release year of a title. In the case of TV Series, it is the series start year
   - endYear (YYYY) – TV Series end year. ‘\N’ for all other title types
   - runtimeMinutes – primary runtime of the title, in minutes
   - genres (string array) – includes up to three genres associated with the title

- **title.principals.tsv.gz** – Contains the principal cast/crew for titles
   - tconst (string) - alphanumeric unique identifier of the title
   - ordering (integer) – a number to uniquely identify rows for a given titleId
   - nconst (string) - alphanumeric unique identifier of the name/person
   - category (string) - the category of job that person was in
   - job (string) - the specific job title if applicable, else '\N'
   - characters (string) - the name of the character played if applicable, else '\N'

- **title.ratings.tsv.gz** – Contains the IMDb rating and votes information for titles
   - tconst (string) - alphanumeric unique identifier of the title
   - averageRating – weighted average of all the individual user ratings
   - numVotes - number of votes the title has received


- **name.basics.tsv.gz** – Contains the following information for names:
   - nconst (string) - alphanumeric unique identifier of the name/person
   - primaryName (string)– name by which the person is most often credited
   - birthYear – in YYYY format
   - deathYear – in YYYY format if applicable, else '\N'
   - primaryProfession (array of strings)– the top-3 professions of the person
   - knownForTitles (array of tconsts) – titles the person is known for




## 🌲 Project tree
```bash

.
├── .env-sample # environmental values
├── README.md
├── analyse_imbd_dataset.ipynb # notebook for analisys
├── creating_db.ipynb # notebook to create db and fill with rows
├── docker-compose.yml # docker compose file
└── downloads # file to store tsv files

```
## 🔑 Setup your local variables
To run properly this project you should assign a environmental variables in file .env.

In this repo is created .env-sample with variables used to run containers. You need to assign variables below in your .env file:
```bash
POSTGRES_PS= # database password
POSTGRES_DB= # database name
JUPYTER_TOKEN= # token to jupyternotebook
HOST_DB= # select port on localhost
```
## ⚙️ Run Locally
- Clone the project
- Go to the project directory:
Type in CLI:
```bash
  $ ls
```
You should see this:
```bash
README.md			creating_db.ipynb		downloads
analyse_imbd_dataset.ipynb	docker-compose.yml
```
Run dockercomposer:
```bash
  $ docker-compose up
```


##  📊Data analisys
**Open jupyter lab via localhost, type in your browser:**
```bash
  localhost:8888
```
🚨In case the notebook requires a token pass a value which was assigned to JUPYER_TOKEN in .env🚨

1. Choose a file 🗒️creating_db.ipynb and run all cells to create db with values.
2. Choose a file 🗒️analyse_imbd_dataset.ipynb and run all cells to see move analisys.
