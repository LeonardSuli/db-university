# Esercizi SQL

## Es. 1

SELECT \* FROM `students` WHERE YEAR(`date_of_birth`) = 1990;

## Es. 2

SELECT \* FROM `courses` WHERE `cfu` > 10;

## Es. 3

SELECT \* FROM `students` WHERE TIMESTAMPDIFF(YEAR, date_of_birth, CURDATE()) > 30;

## Es. 4

SELECT \* FROM `courses` WHERE year = 1 AND period = 'I semestre';

## Es. 5

SELECT \* FROM `exams` WHERE `date` = '2020-06-20' AND `hour` > '14:00:00';

## Es. 6

SELECT \* FROM `degrees` WHERE `level` = 'magistrale';

## Es. 7

SELECT COUNT(`id`) FROM `departments`;

## Es. 8

SELECT \* FROM `teachers` WHERE `phone` IS NULL;
