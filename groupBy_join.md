# Ex Group by

## 1. Contare quanti iscritti ci sono stati ogni anno

SELECT COUNT(\*) AS 'total_registered', year(`enrolment_date`) AS 'year'
FROM `students`
GROUP BY year(`enrolment_date`);

## 2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
