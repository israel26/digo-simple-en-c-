# digo-simple-en-c++
programas cencillo eliminando registro en c++
//israel lopez........
#include<iostream>
#include<fstream>
#include<conio.h>
#include<string.h>
#include<stdio.h>
using namespace std;
main ()
{
	char  nombre[25],profesion[20];
	int edad;
	
	ifstream salida;       // crer flujo se salida de datos de archivo al programa
	salida.open("empleados.txt",ios::in);
	
	ofstream entrada; // archivo nuevo para guardar archivos que no exixte
	entrada.open("temp. txt",ios::out);// tem.txt donde se guartara el dato que no existe
	                                   // a borrar  
	
	if (salida.fail()){  // verificamos que el archivo se haya abierto correcta mente
		cout <<"hubo un error al abrir el arcivo empleados txt";
		getch();  //mostra si ocurrio herror al abrir el archivo
		
	}
	else{
		char aux [25];
		cout <<"introdusca el nombre:  ";
		cin >>aux;
		
		salida>>nombre;  // recuperar dato de archivo
		while (!salida.eof()){
			
			salida>>edad>>profesion;
				
			if (strcmp(aux,nombre)==0){  //aqui decimos si el dato ingresado es igual
			                             // al que contiene el archivo empleados.txt sera borrado
				cout <<"el registro se ha eliminado;";
				getch();
				
			}
			else
			{
				entrada<<nombre<<""<<edad<<""<<profesion<<endl;
			}
			salida>>nombre;
		}
		entrada.close();
		salida.close();
		
		remove("empleado.txt"); // remove nos ayuda a borrar el archivo empleado.txt   
		rename("temp.txt","empleados.txt");//opcion que nos ayuda a renombrar el archivo temp.txt
		                                  // a empleado.txtx
	}
	cin.get();
	return 0;
}


