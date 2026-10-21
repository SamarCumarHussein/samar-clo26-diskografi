# SQL-inlämning — Diskografi

**Namn:** [Samar Hussein  
**Artist:** [2Pac]  
**Datum:** [2026-10-21]

---

> Lägg länk till eller bild på ditt ER-diagram här:
> `[ER-diagram](er_diagram.png)`

---

## 1. Skapa databasen — CREATE TABLE

```sql
CREATE TABLE artists (
    id INT PRIMARY KEY,
	name TEXT NOT NULL 
);

CREATE TABLE albums (
    id INT PRIMARY KEY,
	titele TEXT NOT NULL, 
	release_year INT,
	artists_id INT,
	FOREIGN KEY  (artists_id) REFERENCES artists(id)
);


CREATE TABLE songs (
    id INT PRIMARY KEY, 
	titele TEXT NOT NULL,
	lenght INT, 
	albums_id INT,
	FOREIGN KEY (albums_id ) REFERENCES albums(id)

);

```

---

## 2. Seeda med data — INSERT

```sql
-- Lägg till artisten 2Pac
INSERT INTO artists (id, name)
VALUES (1, '2Pac');

-- Lägg till album kopplade till artisten med id
INSERT INTO albums (id, titele, release_year, artists_id)
VALUES
(1, '2Pacalypse Now', 1991, 1),
(2, 'Me Against the World', 1995, 1),
(3, 'All Eyez on Me', 1996, 1);

-- Lägg till låtarna efter albumen
INSERT INTO songs (id, titele, lenght, albums_id)
VALUES
(1, 'Brenda''s Got a Baby', 234, 1),
(2, 'Trapped', 285, 1),
(3, 'If My Homie Calls', 258, 1),
(4, 'Dear Mama', 279, 2),
(5, 'So Many Tears', 238, 2),
(6, 'Temptations', 300, 2),
(7, 'California Love', 285, 3),
(8, '2 of Amerikaz Most Wanted', 247, 3),
(9, 'All Eyez on Me', 308, 3),
(10, 'Hit Em Up', 315, 3);---

```

---

## 3. Söka — SELECT

```sql
--- query 1: Lista alla album, sorterade efter år ---
SELECT * FROM albums 
ORDER BY release_year ASC;

--- query 2: Lista alla låtar på ett specifikt album ---
SELECT titele, lenght FROM songs
WHERE albums_id = 1;


--- query 3: Antal låtar per album ---
SELECT albums.titele,COUNT (songs.id) AS antal_songs
FROM albums
JOIN songs ON albums.id = songs.albums_id
GROUP BY albums.id, albums.titele;


--- query 4: Längsta låten ---
SELECT titele, lenght FROM songs 
ORDER BY lenght DESC 
LIMIT 1;

--- query 5: Alla låtar sorterade alfabetiskt ---
SELECT * FROM songs 
ORDER BY titele ASC;

```

---

## 4. Lägg till en ny rad — INSERT

```sql
--- lägg till ett nytt album eller en ny låt ---
INSERT INTO songs (id, titele, lenght, albums_id)
VALUES (11, 'Keep Ya Head Up', 276, 1);

```

---

## 5. Ta bort en rad — DELETE

```sql
--- ta bort en rad ur valfri tabell ---
-- Valde att tar bara bort den ny inlagt låten.
DELETE FROM songs
WHERE id = 11;

```

---

## 6. Uppdatera en rad — UPDATE

```sql
--- uppdatera minst en rad i valfri tabell ---

```

---

## 7. VG-queries (om du siktar på VG)

```sql
--- query 6: Snittlängd på låtar per album ---


--- query 7: Albumet med flest låtar ---


--- query 8: Alla låtar längre än 4 minuter (240 sekunder), med albumtitel ---

```
