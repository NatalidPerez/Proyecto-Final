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
        messagebox.showwarning(Ocupado"," esa celda ya tiene una unidad.")
  elif not self.colocando_unidades:
    self.atac_celda(fila, columna)
def atacar_celda(self, fila, columna):
  jugador actual=self.jugadores[self.turno]
jugador_enemigo=self.jugadores[(self.turno+1)%2]
     
unidad=self.tablero[fila][columna]
if unidad and unidad.jugador!=jugador_actual:
   destruida=unidad.recibir_daño(1)
mensaje=f"¡Impacto! Has dañado una unidad enemiga."
if destruida:
  mensaje +="¡Unidad destruid!"
  self.tablero[fila][columna]=none
  jugador enemigo.unidades.remove(unidad)
else:
 mensaje="¡Agua!"
massagebox.showinfo(Resultado del ataque",mensaje)

if selv.verificar_victoria():
  ganador=juagdor_actual.nombre
  self.actualizar_tablero()
messagebox.showinfo("FIN DEL JUEGO", f"{ganador}{ha ganado la partida.")
self.root.quit()
  return

self.turno=(self.turno+1)%2
self.actualizar_tablero()

#Como se ve el tablero y la ubicacion de los barcos por defecto
def actualizar_tablero(self):
  for i in range(self.filas)
    for j in rang(self.columnas)
      unidad = self.tablero[i][j]
      btn = self.botones[i][j]
      if unidad is None:
        btn.config(text=" ", bg="SystemButtonFace")
      elif unidad.jugador == self.jugador[self.turno]
        btn.config(text=f"{unidad.hp}", bg="lightblue")
      else:
        btn.config(text=" ", bg="SystemButtonFace")

  vidas1 = len(self.jugador1.unidade)
  vidas2 = len(self.jugador2.unidades)
  if not self.colocando_unidades:
      texto = f"Turno de {self.jugadores[self.turno].nombre} | Vidas - J1: {vidas1} | J2: {vidas2}"
  else:
      texto = f"Colocando Unidades para: {self.jugador_colocando.nombre}"
  self.info_label.config(text=texto)

#Verificar la Victoria
def verificar_victoria(self):
   for jugador in self.jugadores
       return True
   return False

#Reubicar barcos a gusto del jugador
def reubicar_manual(self):
   self.tablero = [[None for _ in range(self.columnas)] for _ in range(self.filas)]
   self.jugador1.unidades.clear()
   self.jugador2.unidades.clear()
   self.colocando_unidades = True
   self.jugador_colocando = self.jugador1
   self.unidades_a_colocar = [Unidad(f"U1-{i+1}", 2, sel.jugador1) for i in range(3)]
   messagebox.showinfo("Reubicar", "Coloca las unidades del Jugador 1 <3.")
   self.actualizar_tablero()

#Ejecutar juego
if __name__ == "__main__":
   root = tk.Tk()
   root.title("Batalla Naval - Juego por Turnos - Preparate!")
   juego = JuegoBatallaNaval(root)
   root.mainloop()
   
