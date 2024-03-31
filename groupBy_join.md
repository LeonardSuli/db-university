# Ex Group by

## 1. Contare quanti iscritti ci sono stati ogni anno

SELECT COUNT(\*) AS 'total_registered', year(`enrolment_date`) AS 'year'
FROM `students`
GROUP BY year(`enrolment_date`);

## 2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

SELECT COUNT(\*) AS 'total_teachers', `office_address`
FROM `teachers`
GROUP BY `office_address`;

## 3. Calcolare la media dei voti di ogni appello d'esame

SELECT `exam_id`, AVG(`vote`) AS 'media_voti'
FROM `exam_student`
GROUP BY `exam_id`;

## 4. Contare quanti corsi di laurea ci sono per ogni dipartimento

SELECT COUNT(\*) AS 'total_courses', `department_id`
FROM `degrees`
GROUP BY `department_id`;
