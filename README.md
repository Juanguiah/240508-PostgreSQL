## Relacion de 1 a 1:
Comandos para realizar en la consola SQL de DBeaver:
```
create table persona (
id SERIAL primary key,
nombre varchar(100),
edad INT
)

create table pasaporte(
id SERIAL primary key,
numero varchar(20) unique,
id_persona int unique,
--CREAMOS LA RELACIÓN UNO A UNO
foreign key (id_persona) references persona(id)
)

insert into persona (nombre,edad) values ('Juan', 23);
insert into persona (nombre,edad) values ('Pedro', 34);
insert into persona (nombre,edad) values ('Camilo', 38);
insert into persona (nombre,edad) values ('Julian', 45);
insert into persona (nombre,edad) values ('Ana', 51);
insert into persona (nombre,edad) values ('Luis', 18);

select * from persona p

insert into pasaporte (numero,id_persona) values ('ABC2', 1);
insert into pasaporte (numero,id_persona) values ('AZDRT4', 2);
insert into pasaporte (numero,id_persona) values ('FTGTY7', 3);
insert into pasaporte (numero,id_persona) values ('JUKI87', 4);
insert into pasaporte (numero,id_persona) values ('HGJKIU1', 5);
insert into pasaporte (numero,id_persona) values ('FHJGYER1', 6);

select per.nombre , per.edad , pass.numero  from pasaporte pass
inner join persona per on pass.id_persona = per.id
inner join direcciones dire on per.id_direccion = dire.id
```

## Relacion de Muchos a Muchos:
Comandos para realizar en la consola SQL de DBeaver:
```
create table Estudiante (
	id serial primary key,
	nombre varchar(50)
)

insert into public.estudiante (nombre) values ('Juan');
insert into public.estudiante (nombre) values ('Andrea');
insert into public.estudiante (nombre) values ('Milu');

select * from estudiante

create table Curso (
	id serial primary key,
	nombre varchar(50)
)

insert into public.Curso (nombre) values ('Programacion');
insert into public.Curso (nombre) values ('Sociales');
insert into public.Curso (nombre) values ('Ciencias');
insert into public.Curso (nombre) values ('Matematicas');
insert into public.Curso (nombre) values ('Ingles');
insert into public.Curso (nombre) values ('Canto');

select * from Curso

create table Inscripcion (
	id serial primary key,
	id_estudiante int,
	id_curso int,
	foreign key (id_estudiante) references estudiante(id),
	foreign key (id_curso) references curso(id)
)

insert into inscripcion (id_estudiante, id_curso) values (1,1);
insert into inscripcion (id_estudiante, id_curso) values (1,7);
insert into inscripcion (id_estudiante, id_curso) values (2,6);
insert into inscripcion (id_estudiante, id_curso) values (2,9);
insert into inscripcion (id_estudiante, id_curso) values (3,8);
insert into inscripcion (id_estudiante, id_curso) values (3,7);

select * from Inscripcion

select * from Inscripcion 
inner join estudiante e on inscripcion.id_estudiante =e.id 
inner join curso c  on inscripcion.id_curso =c.id 

select e.nombre, c.nombre  from Inscripcion 
inner join estudiante e on inscripcion.id_estudiante =e.id 
inner join curso c  on inscripcion.id_curso =c.id 

```
