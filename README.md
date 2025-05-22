# Proyecto-Final 
import tkinter as tk
from tkinter as import messagebox
class unidad
     def__int( self,nombre ,hp, jugador)
     self.nombre
     self.hp
     self. jugador
     self. posicion 
     posicion 
--def recibir_dano(self, cantidad)
--self.hp -= cantidad 
--return self.hp < = 0
class jugador :
-- def__init__(self, nombre):
------self.nombre = nombre
------self.unidaddes = []
class  Juego Batalla Naval
--def__init__(self,root) :
-----self.root = root
-----self.filas = 5
-----self. columnas=5 
-----self.tablero =[[ none for in range(self.columnas)] for in range(self.filas)]
--self.jugador1 = Jugador("Jugador 1")
--self.jugador2 = Jugador("Jugador 2")
--self.jugadores = [self.jugador1, self.jugador2] 
--self.turno = 0
--self.colocando_unidades = False.          --self.unidades_a_colocar =[]               --self.jugador_colocando = None
--self.crear_unidades_iniciales()
--self.crear_gui()



(Segunda parte del Código)



 if not self.unidades_a_colocar:
    if self.jugador_colocando==self.jugador1:
        self.jugador_colocando=self.jugador2
        self.unidades_a_colocar=[Unidad(f"U2-{i+1}",2,self.jugador2) for i in range(3)] 
           messagebox.showinfo("TURNO"."Ahora coloca las unidades del jugador 2.")
   else:
       self.colocando_unidades= False
       self.turno=0
           messagebox.showinfo("Listo","¡Todas las unidades han sido colocadas!")
   self.actualizar_tabler()
else:
        messagebox.showwarning("Ocupado"," esa celda ya tiene una unidad.")

