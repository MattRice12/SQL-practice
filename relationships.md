# One-to-one
  * [  ] 1 ----- 1 [  ]

  CREATE TABLE Rooms (
    id int PRIMARY KEY,
    seats int,
    movie_id int REFERENCES movies UNIQUE
    );


# One-to-many
  * [  ] 1 ----- * [  ]

  CREATE TABLE Rooms (
    id int PRIMARY KEY,
    seats int,
    movie_id int REFERENCES movies
    );


# Many-to-many
  * [  ] * ----- * [  ]
