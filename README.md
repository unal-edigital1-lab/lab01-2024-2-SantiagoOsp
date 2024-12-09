# Lab01- sumador 

### Santiago Ospina Contreras

@saospinaco@unal.edu.co - Electronica Digital 1

## Informe de laboratorio

### sum1bcc_primitive:

Este codigo muestra la interpretacion explicita del sistema sumador de 1 bit. Primero se declaran las variables, las de entrada y las de salida:

    input  A;
    input  B;
    input  Ci;
    output Cout;
    output S;

Ahora se crean las conexiones fisicas que van a tener, los cables:

    wire a_ab;
    wire x_ab;
    wire cout_t;

Y por ultimo tenemos las compuertas logicas:

    and(a_ab,A,B);
    xor(x_ab,A,B);

    xor(S,x_ab,Ci);
    and(cout_t,x_ab,Ci);

    or(Cout,cout_t,a_ab);

Como vemos, las compuertas tienen parametros que indican, la salida, y las entradas respectivamente.

### sum1bcc_primitive vs sum1bcc

El codigo sum1bcc no declara las compuertas a usar de manera explicita. Ademas, el codigo en sum1bcc almacena los valores (tiene memoria):

    reg [1:0] st;
    assign s = st[0];
    assign Cout = st[1];

Como los valores se almacenan es necesario un sistema que verifique las entradas constantemente, por ello se usa un sistema de bucle:

    always @ (*)
    begin
        A+B+Ci;
    end