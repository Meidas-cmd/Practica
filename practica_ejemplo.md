# Practica 1 .Practica de ejemplo 

## INDICE
1.[Intro](https://github.com/Meidas-cmd/Practica/new/main#intro#1.-intro)

2.[Estructura de clases](https://github.com/Meidas-cmd/Practica/new/main#2estructura-de-datos)

  - Diagrama de clases
  - Codigo de plantuml
  - Contenido de las clase(.java)

3.[Programa principal(nombreApp)](https://github.com/Meidas-cmd/Practica/new/main#3-programa-principal#3.-Programa_Principal)

4.[Pruebas](https://github.com/Meidas-cmd/Practica/new/main#4-prueba#4.-Pruebas)

5.[Entrega](https://github.com/Meidas-cmd/Practica/new/main#5entrega#5.-Entrega)

## Intro

> La practica consistira en ...

## 2.Estructura de datos

### Diagrama de clases

![](./img/imagenes-de-stitch.jpg)

### Codigo de plantuml

````
@startuml
skinparam classAttributeIconSize 0

class casa {
  {static} - entrada : Scanner
  - direccion : String
  - listaHabitaciones : ArrayList<Habitacion>
  - propietario : Propietario

  + casa(direccion : String)
  + crearHabitacion(nombre : String, metros : double) : void
  + eliminarHabitacion(nombre : String) : void
  + mostrarHabitaciones() : void
  + getHabitacionesMasGrades() : Habitacion
  + habitacionMasConsume() : Habitacion
  + getDireccion() : String
  + setDireccion(direccion : String) : void
  + getListaHabitaciones() : ArrayList<Habitacion>
  + setListaHabitaciones(listaHabitaciones : ArrayList<Habitacion>) : void
  + getPropietario() : Propietario
  + setPropietario() : void
  + toString() : String
}

class Habitacion {
  - Nombre : String
  - metros : double
  - listaElectrodomesticos : ArrayList<Electrodemestico>

  + Habitacion(nombre : String, metros : double)
  + agregarElctrodomesticos(nombre : String, consumo : double) : void
  + mostrarElectrodomestico() : void
  + calcualrConsumo() : double
  + getNombre() : String
  + setNombre(nombre : String) : void
  + getMetros() : double
  + setMetros(metros : double) : void
  + getListaElectrodomesticos() : ArrayList<Electrodemestico>
  + setListaElectrodomesticos(listaElectrodomesticos : ArrayList<Electrodemestico>) : void
  + toString() : String
}

class Electrodemestico {
  - nombre : String
  - consumo : double

  + Electrodemestico(nombre : String, consumo : double)
  + getConsumo() : double
  + setConsumo(consumo : double) : void
  + getNombre() : String
  + setNombre(nombre : String) : void
  + toString() : String
}

class Propietario {
  - nombre : String
  - edad : int

  + Propietario(nombre : String, edad : int)
  + getNombre() : String
  + setNombre(nombre : String) : void
  + getEdad() : int
  + setEdad(edad : int) : void
  + toString() : String
}

casa "1" *-- "0..*" Habitacion : contiene >
casa "1" *-- "1" Propietario : tiene >
Habitacion "1" *-- "0..*" Electrodemestico : contiene >

@enduml


````

### Contenido de las clases(.java)

- Clase **Casa.java**

  
  ````
  
public class casa {

    static  Scanner entrada = new Scanner(System.in);

    private String direccion;


    private ArrayList<Habitacion> listaHabitaciones;

    private Propietario propietario;

    public casa (String direccion){

        this.direccion = direccion;
        listaHabitaciones = new ArrayList<>();
        setPropietario();

    }

    public void crearHabitacion(String nombre, double metros){

        for (Habitacion habitacion : listaHabitaciones){

            if (habitacion.getNombre().equals(nombre)){
                System.out.println("La habitacion " + nombre + " ya existe.");
                return;
            }
        }

        Habitacion habitacion = new Habitacion(nombre,metros);

        listaHabitaciones.add(habitacion);

        System.out.println("Habitacion " + nombre + " creada.");

    }

    public void eliminarHabitacion(String nombre){

        for (Habitacion habitacion : listaHabitaciones){

            if(habitacion.getNombre().equals(nombre)){
                listaHabitaciones.remove(habitacion);
                System.out.println("Habitacion eliminada");
                return;
            }
        }

        System.out.println("La habitacion no existe ");

    }


    public void mostrarHabitaciones(){

        System.out.println("Casa en " + direccion + "y propetario "+ getPropietario() + " tiene " + listaHabitaciones.size() + " habitaciones.");
        for (Habitacion habitacion : listaHabitaciones){
            System.out.println("- " + habitacion.getNombre() + " (" + habitacion.getMetros() + ") m2");
        }
    }
    public Habitacion getHabitacionesMasGrades(){
        Habitacion mayor = listaHabitaciones.get(0) ;

        for (Habitacion habitacion : listaHabitaciones){
            if (habitacion.getMetros()>mayor.getMetros()){
            mayor = habitacion;

            }
        }
        return  mayor;
    }



    public String getDireccion() {
        return direccion;
    }

    public void setDireccion(String direccion) {
        this.direccion = direccion;
    }

    public ArrayList<Habitacion> getListaHabitaciones() {
        return listaHabitaciones;
    }

    public void setListaHabitaciones(ArrayList<Habitacion> listaHabitaciones) {
        this.listaHabitaciones = listaHabitaciones;
    }

    public Habitacion habitacionMasConsume(){
        Habitacion maximo = listaHabitaciones.get(0);

        for (Habitacion habitacion : listaHabitaciones){
            if (habitacion.calcualrConsumo()>maximo.calcualrConsumo()){
                maximo=habitacion;
            }
        }

        return maximo;
    }

    public Propietario getPropietario() {
        return propietario;
    }

    public void setPropietario() {
        System.out.println("Introduce el nombre del propietario :");
        String nombre = entrada.nextLine();
        System.out.println("Edad : ");
        int edad = entrada.nextInt();
        entrada.nextLine();
        Propietario propietario = new Propietario(nombre,edad);
        this.propietario = propietario;
        System.out.println("Propietario " + nombre + " añadido" );
    }

    @Override
    public String toString() {
        return "casa{" +
                "direccion='" + direccion + '\'' +
                "propietario" + propietario + '\'' +
                '}';
    }



}

## 3. Programa principal

> TIP
> para hacer lo como una cajita el texto

## 4. Prueba

## 5.Entrega

- [X] Codigo fuente en Github: [Link]()
- [] HOLA ESTO ES PARA HACER UNA CHECKBOX.
