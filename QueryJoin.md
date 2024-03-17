1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

       SELECT `students`.*
       FROM `students`
       INNER JOIN `degrees` 
       ON `degrees`.`id` = `students`.`degree_id`
       WHERE  `degrees`.`name` = 'Corso di Laurea in Economia';
 
2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
Neuroscienze

       SELECT `degrees`.*
       FROM `degrees`
       INNER JOIN `departments` 
       ON `degrees`.`department_id = `departments`.`id`
       WHERE `departments`.`name` = 'Dipartimento di Neuroscienze';
       AND `degrees`.`level` = 'magistrale'

 
3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

       SELECT `courses`.*
       FROM `courses`
       INNER JOIN `course_teacher`
       ON `courses`.`id` = `course_teacher`.`course_id`
       WHERE `course_teacher`.`teacher_id` = 44;
 
4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
nome

       SELECT `students`.*, `degrees`.*, `departments`.*
       FROM `students`
       INNER JOIN `degrees`
       ON `students`.`degree_id` = `degrees`.`id`
       INNER JOIN `departments`
       ON `degrees`.`departments_id` = `departments`.`id`
       ORDER BY `students`.`name` ASC, `students`.`surname` ASC

5. Selezionare tutti i docenti che insegnano nel Dipartimento di
Matematica (54)

       SELECT `teachers`.*
       FROM `teachers`
       INNER JOIN `course_teacher`
       ON `teachers`.`id` = `course_teacher`.`teacher_id`
       INNER JOIN `courses`
       ON `courses`.`id` = `course_teacher`.`courses_id`
       INNER JOIN `degrees`
       ON `courses`.`degree_id` = `degrees`.`id`
       INNER JOIN `departments`
       ON `degrees`.`departments_id` = `departments`.`id`
       WHERE `departments`.`name` = 'Dipartimento di Matematica'
 