CREATE TABLE IF NOT EXISTS Genre(
    genreID INTEGER PRIMARY KEY,
    name VARCHAR(80) NOT NULL
);
CREATE TABLE IF NOT EXISTS Singer(
    singerID INTEGER PRIMARY KEY,
    name VARCHAR(80) NOT NULL
);
CREATE TABLE IF NOT EXISTS Album(
    albumID INTEGER PRIMARY KEY,
    name VARCHAR(80) NOT NULL,
    year date
);

CREATE TABLE IF NOT EXISTS Track(
    trackID INTEGER PRIMARY KEY,
    name VARCHAR(80) NOT NULL,
    time INTEGER,
    albumID INTEGER REFERENCES Album(albumID)
);

CREATE TABLE IF NOT EXISTS Collection(
    collectionID INTEGER PRIMARY KEY,
    name VARCHAR(80) NOT NULL,
    year date
);


CREATE TABLE IF NOT EXISTS Genre_Singer(
    genre_id INTEGER REFERENCES Genre(genreID),
    singer_id  INTEGER REFERENCES Singer(singerID),
    CONSTRAINT pk PRIMARY KEY(genre_id, singer_id)
);

CREATE TABLE IF NOT EXISTS Album_Singer(
    album_id INTEGER REFERENCES Album(albumID),
    singer_id  INTEGER REFERENCES Singer(singerID),
    CONSTRAINT pk1 PRIMARY KEY(album_id, singer_id)
);

CREATE TABLE IF NOT EXISTS Track_Collection(
    track_id INTEGER REFERENCES Track(trackID),
    collection_id INTEGER REFERENCES Collection(collectionID),
    CONSTRAINT pk2 PRIMARY KEY(track_id, collection_id)
);