# Esercizi SQL

## Es. 1_Selezionare tutti gli studenti nati nel 1990 (160)

SELECT \* FROM `students` WHERE YEAR(`date_of_birth`) = 1990;
SELECT \* FROM `students` WHERE `date_of_birth` LIKE '1990%';
SELECT \* FROM `students` WHERE `date_of_birth` BETWEEN '1990-01-01' AND '1990-12-31';

## Es. 2_Selezionare tutti i corsi che valgono più di 10 crediti (479)

SELECT \* FROM `courses` WHERE `cfu` > 10;

## Es. 3_Selezionare tutti gli studenti che hanno più di 30 anni

SELECT \* FROM `students` WHERE TIMESTAMPDIFF(YEAR, date_of_birth, CURDATE()) > 30; (3531)
SELECT \* FROM `students` WHERE YEAR(now()) - YEAR(`date_of_birth`) > 30; (3646)
SELECT \* FROM `students` WHERE DATEDIFF(NOW(), `date_of_birth`) / 365.25 > 30; (3691)

## Es. 4_Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286)

SELECT \* FROM `courses` WHERE `year` = 1 AND `period` = 'I semestre';

## Es. 5_Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)

SELECT \* FROM `exams` WHERE `date` = '2020-06-20' AND `hour` > '14:00:00';
SELECT \* FROM `exams` WHERE `date` = '2020-06-20' AND HOUR(`hour`) >= 14;

## Es. 6_Selezionare tutti i corsi di laurea magistrale (38)

SELECT \* FROM `degrees` WHERE `level` = 'magistrale';

## Es. 7_Da quanti dipartimenti è composta l'università? (12)

SELECT COUNT(`id`) FROM `departments`;

## Es. 8_Quanti sono gli insegnanti che non hanno un numero di telefono? (50)

SELECT \* FROM `teachers` WHERE `phone` IS NULL;
