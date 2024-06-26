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

#

#

# Ex Joins

## 1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia (68)

SELECT `students`.`*`, `degrees`.`name` AS 'degree_name'
FROM `students`
JOIN `degrees`
ON `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = 'Corso di Laurea in Economia';

## 2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze (1)

SELECT `degrees`.`*`, `departments`.`name` AS 'department_name'
FROM `degrees`
JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id`
WHERE `departments`.`name` = 'Dipartimento di Neuroscienze'
AND `degrees`.`level` = 'magistrale';

## 3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT `courses`.`name`, `course_teacher`.`teacher_id` AS 'prof_id', `teachers`.`name`, `teachers`.`surname`
FROM `course_teacher`
JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`
WHERE `course_teacher`.`teacher_id` = 44;

## 4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

SELECT `students`.`name` AS 'student_name', `students`.`surname`, `degrees`.`name` AS 'degree_name', `departments`.`name` AS `department_name`
FROM `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`  
ORDER BY `students`.`surname` ASC, `students`.`name` ASC;

## 5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT `degrees`.`name` AS 'degree_name', `courses`.`name` AS 'course_name', `teachers`.`name` AS 'teacher_name', `teachers`.`surname`
FROM `degrees`
JOIN `courses` ON `degrees`.`id` = `courses`.`degree_id`
JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id`
JOIN `teachers` ON `teachers`.`id` = `course_teacher`.`teacher_id`;

## 6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

SELECT `teachers`.`id`, `teachers`.`name`, `teachers`.`surname`, `departments`.`name`
FROM `course_teacher`
JOIN `teachers`
ON `course_teacher`.`teacher_id` = `teachers`.`id`
JOIN `courses`
ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `degrees`
ON `courses`.`degree_id` = `degrees`.`id`
JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id`
WHERE `departments`.`name` = 'Dipartimento di Matematica';
