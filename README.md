# db-university
===
Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:
sono presenti diversi Dipartimenti (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
ogni Dipartimento offre più Corsi di Laurea (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
ogni Corso di Laurea prevede diversi Corsi (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
ogni Corso può essere tenuto da diversi Insegnanti;
ogni Corso prevede più appelli d'Esame;
ogni Studente è iscritto ad un solo Corso di Laurea;
ogni Studente può iscriversi a più appelli di Esame;
per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente.
Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.
Utilizzare https://www.drawio.com/ per la creazione dello schema.
Esportare quindi il diagramma in jpg e caricarlo nella repo.
===
PROSEGUIMENTO ESERCIZIO:
Dopo aver creato un nuovo database nel vostro MySQL Workbench e aver importato lo schema allegato, eseguite le query del file allegato.

Queries from 1 to 4

1)   SELECT * FROM `students` WHERE YEAR (`date_of_birth`) = 1990
2)   SELECT * FROM `courses` WHERE `cfu` > 10
3)   SELECT * from `STUDENTS` WHERE YEAR (`date_of_birth`) <= 1994
4)   SELECT * FROM `courses` WHERE `year` = 1 AND `period`LIKE "I_s%"

Queries from 5 to 8

5)   SELECT * FROM `exams` WHERE DATE (`date`) = "2020-06-20" AND TIME (`hour`) > "14:00:00"
6)   SELECT * FROM `degrees` WHERE `level` = "magistrale"
7)   SELECT COUNT(*) FROM AS `num_departments` `departments` 
8)   SELECT COUNT(*) AS `num_teachers` FROM `teachers` WHERE `phone` IS NULL

Second page Queries 

1)  SELECT COUNT(*) AS `iscritti`,  YEAR (`enrolment_date`) AS `year` FROM `students` GROUP BY `year`
2)  SELECT COUNT(*) AS `numero_insegnati`, `office_address` FROM `teachers` GROUP BY `office_address`ok
3)  SELECT AVG(`vote`) FROM `exam_student` GROUP BY `exam_id`ok
4)  SELECT `department_id`, COUNT(*) AS `numero_corsi` FROM `degrees` GROUP BY `department_id`
===
PROSEGUIMENTO ESERCIZIO
Utilizzando lo stesso database di ieri, eseguite le query in allegato.
Caricate un secondo file nella stessa repo di ieri (db-university) con le query di oggi.

1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
SELECT *
FROM `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = "Corso di Laurea in Economia"

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
SELECT *
FROM `degrees`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
WHERE `departments`.`name` = "Dipartimento di Neuroscienze"
AND `degrees`.`level` = 'magistrale'

