import ply.lex as lex

# Definición de tokens
tokens = [
    'IMPRIMIR', 'SUMA', 'RESTA', 'IGUAL', 'MULTIPLICACION', 'DIVISION',
    'PARIZQ', 'PARDER', 'CORCHIZQ', 'CORCHDER', 'LLAVEIZQ', 'LLAVEDER', 'DIFERENTE',
    'MENOR', 'MAYOR', 'MENORIGUAL', 'MAYORIGUAL', 'INCREMENTAR', 'DECREMENTAR',
    'MIENTRAS', 'PARA', 'FUNCION', 'DETENER', 'DEVOLVER', 'SI', 'SINO', 'ENTERO',
    'DECIMAL', 'LETRA', 'BOOLEANO', 'PALABRA', 'MOSTRAR', 'INGRESAR', 'COMENTARIO',
    'COMA', 'PUNTOYCOMA', 'ID', 'NUM'
]

# Expresiones regulares para tokens simples
t_IMPRIMIR = r'imprimir\(.*\)'
t_SUMA = r'mas'
t_RESTA = r'menos'
t_IGUAL = r'igual'
t_MULTIPLICACION = r'por'
t_DIVISION = r'entre'
t_PARIZQ = r'\('
t_PARDER = r'\)'
t_CORCHIZQ = r'\['
t_CORCHDER = r'\]'
t_LLAVEIZQ = r'\{'
t_LLAVEDER = r'\}'
t_DIFERENTE = r'noigual'
t_MENOR = r'menor'
t_MAYOR = r'mayor'
t_MENORIGUAL = r'menoroi'
t_MAYORIGUAL = r'mayoroi'
t_INCREMENTAR = r'incrementar'
t_DECREMENTAR = r'decrementar'
t_FUNCION = r'funcion'
t_MIENTRAS = r'mientras'
t_PARA = r'para'
t_DETENER = r'detener'
t_DEVOLVER = r'devolver'
t_SI = r'si'
t_SINO = r'sino'
t_ENTERO = r'entero'
t_DECIMAL = r'decimal'
t_LETRA = r'letra'
t_BOOLEANO = r'booleano'
t_PALABRA = r'palabra'
t_MOSTRAR = r'mostrar\("[^"]*"\)'
t_INGRESAR = r'ingresar'
t_COMENTARIO = r'//'
t_COMA = r','
t_PUNTOYCOMA = r';'

# Ignorar caracteres como espacios y tabulaciones
t_ignore = ' \t'

# Regla para ignorar saltos de línea
def t_newline(t):
    r'\n+'
    t.lexer.lineno += len(t.value)

# Definición de funciones para manejar tokens con acciones adicionales
def t_NUM(t):
    r'\d+'
    t.value = int(t.value)
    return t

def t_ID(t):
    r'[a-zA-Z][a-zA-Z0-9_]*'
    reserved_words = {
        'PRINCIPAL', 'DETENER', 'ENTERO', 'DECIMAL', 'LETRA', 'BOOLEANO',
        'MIENTRAS', 'PARA', 'FUNCION', 'DETENER', 'DEVOLVER', 'SI', 'SINO', 'MOSTRAR', 'INGRESAR'
    }
    if t.value.upper() in reserved_words:
        t.type = t.value.upper()
    else:
        t.type = 'ID'  # Devolver el tipo de token como 'ID' en lugar de la palabra reservada
    return t

# Función para manejar errores
def t_error(t):
    print("Carácter ilegal '%s'" % t.value[0])
    t.lexer.skip(1)

# Construir el lexer
lexer = lex.lex()

# Función para leer las pruebas desde un archivo de texto
def leer_pruebas(nombre_archivo):
    with open(nombre_archivo, 'r') as archivo:
        return archivo.read()

# Nombre del archivo que contiene las pruebas
nombres_archivos_pruebas = ['pruebas.txt','pruebas2.txt','pruebas3.txt']

# Iterar sobre los archivos de pruebas
for nombre_archivo_pruebas in nombres_archivos_pruebas:
    # Leer las pruebas desde el archivo
    pruebas = leer_pruebas(nombre_archivo_pruebas)

    print(f"Tokens encontrados en '{nombre_archivo_pruebas}':")
    # Ejecutar el lexer sobre las pruebas
    lexer.input(pruebas)

    # Tokenizar las pruebas e imprimir los tokens encontrados
    while True:
        tok = lexer.token()
        if not tok:
            break
        print(tok)
    print()  # Agregar una línea en blanco entre los tokens de cada archivo
