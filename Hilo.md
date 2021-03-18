

### En el hilo es para saber cuantas veces se repite una palabra en un parrafo y lo hice dentro del servidor

### Se utilizan estas libreria y luego se hace la funcion.

# incluye  < stdio.h >
# incluir  < string.h >
# incluye  < stdlib.h >
# incluye  < pthread.h >
# incluir  < unistd.h >

typedef  struct {
  char palabra [ 101 ];
  int frecuencia;}
WordArray;

int  compareWords ( const  void * f1, const  void * f2) {
  WordArray * a = (WordArray *) f1;
  WordArray * b = (WordArray *) f2;
  return (b-> frecuencia - a-> frecuencia );
}

void  countFrequency ( void * arg) {
  
  char * fileName = ( char *) malloc ( sizeof ( char ));
  fileName = ( char *) arg;
  WordArray * palabras = (WordArray *) calloc (( 1000 ), sizeof (WordArray));
  char * resultado = ( char *) malloc ( tamaño de (resultado) * 100 );
  int contador = 0 ;
  int isUnique;
  int i = 0 ;
  ARCHIVO * archivo;
  pulido de carbón [ 1000 ];

 
  para (i = 0 ; i < sizeof (WordArray); i ++) {
    palabras [i]. palabra [ 0 ] = ' \ 0 ' ;
    palabras [i]. frecuencia = 0 ;
  }

  file = fopen (fileName, " r " );
  if (archivo == NULL ) {
    printf ( " No se pudo abrir el archivo: " );
  }
      
  else {
    while (( fscanf (archivo, " % s " , buff))! = EOF)
    {
      isUnique = - 1 ;

      
      int k;
      para (k = 0 ; k <contador; k ++) {
        if ( strcmp (palabras [k]. palabra , buff) == 0 ) {
          isUnique = k;
        }
      }
     
      if (isUnique == - 1 ) {
        strcpy (palabras [contador]. palabra , buff);
        palabras [contador]. frecuencia = 1 ;
        contador ++;
      }
      
      else {
        palabras [isUnique]. frecuencia ++;
      }
      
      palabras = REALLOC (palabras, ( sizeof (* palabras) + contador) * sizeof (WordArray));  
    }
  }

  
  qsort (palabras, contador, sizeof (WordArray), compareWords);
  // Almacene las 3 palabras más frecuentes como resultado, como una sola cadena y luego imprima esa cadena
  snprintf (resultado, 10000 , " % s  % d  % s  % s  % s " , nombre de archivo, contador, palabras [ 0 ]. palabra , palabras [ 1 ]. palabra , palabras [ 2 ]. palabra );
  fclose (archivo);
  printf ( " % s \ n " , resultado);

}

int  main ( int argc, char * argv []) {
  
  
  subprocesos pthread_t [argc- 1 ];
  pthread_attr_t attr;
  pthread_attr_init (& attr);

  // Ejecuta todos los hilos al mismo tiempo
  int i;
  para (i = 1 ; i <argc; i ++) {
    char * argumentos = ( char *) malloc ( tamaño de (argv [i]) + 1 );
    argumentos = argv [i];
    // Cree un nuevo hilo para cada argumento pasado por el usuario y cuente la frecuencia de palabras para cada
    pthread_create (& threads [i], & attr, ( void *) countFrequency, ( void *) argumentos);
  }
  para (i = 1 ; i <argc; i ++) {
    // Unir hilos para evitar pérdidas de memoria
    pthread_join (hilos [i], NULL );
  }

  return  0 ;}

  ## En el archivo.txt es donde se pone el parrafo o el texto que quiera saber de cuantas palabras se repiten y que les diga el nombre.

  en menú de VirtualBox Podremos encontrar las opciones en Archivo
  Importar servicio virtualizado debemos escoger el archivo con la imagen máquina que queremos importar
   generalmente en formato
   en menú de VirtualBox Podremos encontrar las opciones en Archivo
   Importar servicio virtualizado debemos escoger el archivo con la imagen máquina que queremos importar
   generalmente en formato
   en menú de VirtualBox Podremos encontrar las opciones en Archivo
  Importar servicio virtualizado debemos escoger el archivo con la imagen máquina que queremos importar
   generalmente en formato