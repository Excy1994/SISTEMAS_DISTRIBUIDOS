
# incluye < stdio.h >
# incluir < string.h >
# incluye < stdlib.h >
# incluir < unistd.h >
# incluye < sys / socket.h >
# incluye < arpa / inet.h >
# incluye < netinet / in.h >
# incluye < netdb.h >


int  main ( int argc, char ** argv) {
  si (argc < 2 )
  { // Especifica los argumentos
    printf ( " % s <puerto> \ n " , argv [ 0 ]);
    return  1 ;
  }


  int conexion_servidor, conexion_cliente, puerto;
  socklen_t longc;
  struct sockaddr_in servidor, cliente;
  tampón de carbón [ 100 ];
  puerto = atoi (argv [ 1 ]);
  conexion_servidor = enchufe (AF_INET, SOCK_STREAM, 0 ); // creamos el socket
  bzero (( char *) & servidor, sizeof (servidor)); // llenamos la estructura de 0's
  servidor. sin_family = AF_INET; // asignamos a la estructura
  servidor. sin_port = htons (puerto);
  servidor. sin_addr . s_addr = INADDR_ANY ;
  if ( bind (conexion_servidor, ( struct sockaddr *) & servidor, sizeof (servidor)) < 0 )
  { // asignamos un puerto al socket
    printf ( " Error al asociar el puerto a la conexion \ n " );
    cerrar (conexion_servidor);
    return  1 ;
  }


  escuchar (conexion_servidor, 3 ); // Estamos a la escucha
  printf ( " A la escucha en el puerto % d \ n " , ntohs (servidor. sin_port ));
  longc = sizeof (cliente); // Asignamos el tamaño de la estructura a esta variable
  conexion_cliente = accept (conexion_servidor, ( struct sockaddr *) & cliente, & longc);
  si (conexion_cliente < 0 )
  { printf ( " Hay error al aceptar trafico \ n " );
    cerrar (conexion_servidor);
    return  1 ;}

  printf ( " Conectando con % s : % d \ n " , inet_ntoa (cliente. sin_addr ), htons (cliente. sin_port ));
  si ( recv (conexion_cliente, buffer, 100 , 0 ) < 0 )
  { // Comenzamos a recibir datos del cliente
    // Si recv () recibe 0 el cliente ha cerrado la conexión. Si es menor que 0 ha habido algún error.
    printf ( " Error al recibir los datos \ n " );
    cerrar (conexion_servidor);
    return  1 ;}

  else {
    printf ( " % s \ n " , búfer);
    bzero (( char *) & búfer, tamaño de (búfer));
    enviar (conexion_cliente, " Recibido exitosamente \ n " , 13 , 0 );}

  cerrar (conexion_servidor);
  return  0 ;}