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

MUCHOS A MUCHOS

```
create table estudiante (
id SERIAL primary key,
nombre varchar(100)
);

insert into estudiante (nombre) values ('Juan');
insert into estudiante (nombre) values ('Pedro');
insert into estudiante (nombre) values ('Daniel');
insert into estudiante (nombre) values ('Miguel');
insert into estudiante (nombre) values ('Santiago');
insert into estudiante (nombre) values ('Enrique');

select * from public.estudiante

create table curso(
id SERIAL primary key,
nombre varchar(100)
)

insert into curso (nombre) values ('Matematicas');
insert into curso (nombre) values ('Algebra');
insert into curso (nombre) values ('Quimica');
insert into curso (nombre) values ('Ingles');

select * from public.curso

create table inscripcion (
id serial primary key,
id_estudiante int,
id_curso int,
foreign key (id_estudiante) references estudiante(id),
foreign key (id_curso) references curso(id)
)

select e.nombre, c.nombre from inscripcion i
inner join estudiante e on i.id_estudiante = e.id
inner join curso c on i.id_curso = c.id

--PEDRO matematicas, quimica, ingles
insert into inscripcion (id_estudiante, id_curso) values (2,1);
insert into inscripcion (id_estudiante, id_curso) values (2,2);
insert into inscripcion (id_estudiante, id_curso) values (2,3);

--JUAN matematicas, quimica, ingles
insert into inscripcion (id_estudiante, id_curso) values (1,1);
insert into inscripcion (id_estudiante, id_curso) values (1,3);
insert into inscripcion (id_estudiante, id_curso) values (1,4);
```


