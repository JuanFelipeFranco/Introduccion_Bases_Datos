# Introduccion_Bases_Datos
Curso introduccion de bases de datos relacionales MYSQL y no relacionales

# CREACION DE DIAGRAMA ENTIDAD RELACION
<img width="582" alt="image" src="https://github.com/JuanFelipeFranco/Introduccion_Bases_Datos/assets/111205147/bf7b2887-9498-446f-9b99-a17ac3ce9d27">

# CREACION DE DATABASE.
CREATE SCHEMA `blog` ;

# CREACION DE TABLAS INDEPENDIENTES 
CREATE TABLE categorias (
	id SERIAL PRIMARY KEY NOT NULL,
	name Varchar(30) NOT NULL
);

CREATE TABLE etiquetas (
	id SERIAL PRIMARY KEY NOT NULL,
	name VARCHAR(30) NOT NULL
);

CREATE TABLE usuarios (
	id SERIAL PRIMARY KEY NOT NULL,
	login VARCHAR(30) NOT NULL,
	password VARCHAR(32) NOT NULL,
	nickname VARCHAR(40) NOT NULL,
	email VARCHAR(255) NOT NULL UNIQUE
);
# CREACION DE TABLAS DEPENDIENTES
CREATE TABLE posts(
id INT,
titulo VARCHAR(130) NOT NULL,
fecha_publicacion TIMESTAMP,
contenido TEXT NOT NULL,
estatus CHAR(8) DEFAULT &quot;activo&quot;,
usuario_id INT NOT NULL,
categoria_id INT NOT NULL,
PRIMARY KEY (id),
FOREIGN KEY (usuario_id) REFERENCES usuarios(id) ON UPDATE CASCADE ON DELETE NO ACTION,
FOREIGN KEY (categoria_id) REFERENCES categorias(id)
)```

CREATE TABLE comentarios (
idComentario INT IDENTITY(1,1) PRIMARY KEY,
comentario TEXT NOT NULL, 
idUsuario INT NOT NULL,
idPost INT NOT NULL,
FOREIGN KEY (idUsuario) REFERENCES usuarios(idUsuario)
ON UPDATE CASCADE
ON DELETE NO ACTION,
FOREIGN KEY (idPost) REFERENCES posts(idPost)
ON UPDATE CASCADE
ON DELETE NO ACTION
);

# CREACION DE TABLA INDEXADAS ETIQUETAS - POSTS

CREATE TABLE posts_etiquetas(
idPostEtiqueta INT IDENTITY(1,1) PRIMARY KEY,
idPost INT NOT NULL,
idEtiqueta INT NOT NULL,
FOREIGN KEY (idPost) REFERENCES posts(idPost)
ON UPDATE CASCADE
ON DELETE NO ACTION,
FOREIGN KEY (idEtiqueta) REFERENCES etiquetas(idEtiqueta)
ON UPDATE CASCADE
ON DELETE NO ACTION
);


