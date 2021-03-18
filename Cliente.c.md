

# incluye < stdio.h >
# incluir < string.h >
# incluye < stdlib.h >
# incluir < unistd.h >
# incluye < arpa / inet.h >
# incluye < sys / socket.h >
# incluye < netinet / in.h >
# incluye < netdb.h >

int  main ( int argc, char ** argv) {
  si (argc < 2 )
  { printf ( " <host> <puerto> \ n " );
    return  1 ;}

  struct sockaddr_in cliente;
  struct hostent * servidor;
  servidor = gethostbyname (argv [ 1 ]);
  si (servidor == NULL )


  { printf ( " Error en host. \ n " );
    return  1 ;}

  int puerto, conexion;
  tampón de carbón [ 100 ];

  conexion = enchufe (AF_INET, SOCK_STREAM, 0 );
  puerto = ( atoi (argv [ 2 ]));
  bzero (( char *) & cliente, sizeof (( char *) & cliente)); // Rellena toda la estructura de 0's
        // La función bzero () es como memset () pero inicializando a 0 todas las variables


  cliente. sin_family = AF_INET;
  cliente. sin_port = htons (puerto);
  bcopy (( char *) servidor-> h_addr , ( char *) & cliente. sin_addr . s_addr , sizeof (servidor-> h_length ));
  // bcopy (); copia los datos del primer elemendo en el segundo con el tamaño máximo



  // cliente.sin_addr = * ((struct in_addr *) servidor-> h_addr); // <- para empezar prefiero que se usen
  // inet_aton (argv [1], & cliente.sin_addr); // <- alguna de estas dos funciones
  if ( connect (conexion, ( struct sockaddr *) & cliente, sizeof (cliente)) < 0 )
  { printf ( " Error al conectar con el host \ n " );
    cerrar (conexión);
    return  1 ;}

  printf ( " Conectado con % s : % d \ n " , inet_ntoa (cliente. sin_addr ), htons (cliente. sin_port ));
  // inet_ntoa (); está definida en <arpa / inet.h>
  printf ( " Escribir mensaje, aqui: " );
  fgets (búfer, 100 , stdin);
  enviar (conexión, búfer, 100 , 0 );
  bzero (tampón, 100 );
  recv (conexión, búfer, 100 , 0 );
  printf ( " % s " , búfer);


return  0 ;}