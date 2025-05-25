# Proyecto-Final 
import tkinter as tk
from tkinter import messagebox

class unidad:
  def __int__( self,nombre ,hp, jugador):
     self.nombre = nombre 
     self.hp = hp
     self. jugador = jugador
     self. posicion = None 
  def recibir_dano(self, cantidad):
     self.hp -= cantidad 
     return self.hp <= 0
     
class jugador :
   def __init__(self, nombre):
      self.nombre = nombre
      self.unidaddes = []
      
class  JuegoBatallaNaval:
  def __init__(self,root) :
     self.root = root
     self.filas = 5
     self.columnas = 5 
     self.tablero =[[ None for _ in range(self.columnas)] for _ in range(self.filas)]
     self.jugador1 = jugador("Jugador 1")
     self.jugador2 = jugador("Jugador 2")
     self.jugadores = [self.jugador1, self.jugador2] 
     self.turno = 0
     self.colocando_unidades = False          
     self.unidades_a_colocar =[]               
     self.jugador_colocando = None
     self.crear_unidades_iniciales()
     self.crear_gui()

  def crear_unidades_iniciales(self):
       for i in range(3):
           u = unidad(f"U1-{i+1}", 2, self.jugador1)
           u.posicion = (0, i)
           self.jugador1.unidades.append(u)
           self.tablero[0][i] = u

      for i in range(3):
          u = unidad(f"U2-{i+1}", 2, self.jugador2)
          u.posicion = (4, i+2)
          self.jugador2.unidades.append(u)
          self.tablero[4][i+2] = u

  def crear_gui(self):
       self.info_label = tk.label(self.root, text="", font=("Arial", 14))
       self.info_label.pack(pady=10)
       self.tablero_frame = tk.frame(self.root)
       self.tablero_frame.pack()
       self.botones = []
       for i in range(self.filas):
            fila_botones = []
            for j in range(self.columnas):
                 btn = tk.button(self.tablero_frame, width=6, height=3, command=lambda x=i, y=j: self.clic_en_celda(x, y))
                 btn.grid(row=i, column=j)
                 fila_botones.append(btn)
            self.botones.append(fila_botones)     
            self.boton_reubicar = tk.button(self.root, text="Reubicar Unidades", command=self.reubicar_manual)
            self.boton_reubicar.pack(pady=10)
            self.actualizar_tablero()

  def clic_en_celda(self, fila, columna):
       if self.colocando_unidades and self.unidades_a_colocar:
           if self.tablero[fila][columna] in None:
                unidad = self.unidades_a_colocar.pop(0)
                unidad.posiciom = (fila, columna)
                self.tablero[fila][columna] = unidad
                self.jugador_colocando.unidades.append(unidad)
                self.actualizar_tablero()

               if not self.unidades_a_colocar:
                  if self.jugador_colocando==self.jugador1:
                     self.jugador_colocando=self.jugador2
                     self.unidades_a_colocar=[unidad(f"U2-{i+1}",2,self.jugador2) for i in range(3)] 
                     messagebox.showinfo("TURNO","Ahora coloca las unidades del jugador 2.")
               else:
                    self.colocando_unidades= False
                    self.turno=0
                    messagebox.showinfo("Listo","¡Todas las unidades han sido colocadas!")
              self.actualizar_tabler()
              
          else:
              messagebox.showwarning("Ocupado","Esa celda ya tiene una unidad.")
      elif not self.colocando_unidades:
          self.atacar_celda(fila, columna)

def atacar_celda(self, fila, columna):
    jugador_actual = self.jugadores[self.turno]
    jugador_enemigo = self.jugadores[(self.turno+1)%2]
     
    unidad=self.tablero[fila][columna]
    if unidad and unidad.jugador!=jugador_actual:
       destruida=unidad.recibir_dano(1)
       mensaje=f"¡Impacto! Has dañado una unidad enemiga."
       if destruida:
          mensaje += "¡Unidad destruida!"
          self.tablero[fila][columna]=None
          jugador_enemigo.unidades.remove(unidad)
      else:
         mensaje="¡Agua!"
         
       messagebox.showinfo(Resultado del ataque",mensaje)
    
      if self.verificar_victoria():
        ganador = juagdor_actual.nombre
        self.actualizar_tablero()
        messagebox.showinfo("FIN DEL JUEGO", f"{ganador}{"Ha ganado la partida."}
        self.root.quit()
        return
      
      self.turno=(self.turno+1)%2
      self.actualizar_tablero()

#Como se ve el tablero y la ubicacion de los barcos por defecto
  def actualizar_tablero(self):
    for i in range(self.filas):
      for j in range(self.columnas):
        unidad = self.tablero[i][j]
        btn = self.botones[i][j]
        if unidad is None:
          btn.config(text=" ", bg="SystemButtonFace")
        elif unidad.jugador == self.jugador[self.turno]
          btn.config(text=f"{unidad.hp}", bg="lightblue")
        else:
          btn.config(text=" ", bg="SystemButtonFace")
  
    vidas1 = len(self.jugador1.unidades)
    vidas2 = len(self.jugador2.unidades)
    if not self.colocando_unidades:
        texto = f"Turno de {self.jugadores[self.turno].nombre} | Vidas - J1: {vidas1} | J2: {vidas2}"
    else:
        texto = f"Colocando Unidades para: {self.jugador_colocando.nombre}"
    self.info_label.config(text=texto)
  
  #Verificar la Victoria
  def verificar_victoria(self):
     for jugador in self.jugadores:
         return True
     return False
  
  #Reubicar barcos a gusto del jugador
  def reubicar_manual(self):
     self.tablero = [[None for _ in range(self.columnas)] for _ in range(self.filas)]
     self.jugador1.unidades.clear()
     self.jugador2.unidades.clear()
     self.colocando_unidades = True
     self.jugador_colocando = self.jugador1
     self.unidades_a_colocar = [unidad(f"U1-{i+1}", 2, self.jugador1) for i in range(3)]
     messagebox.showinfo("Reubicar", "Coloca las unidades del Jugador 1 <3.")
     self.actualizar_tablero()
  
  #Ejecutar juego
if __name__ == "__main__":
     root = tk.Tk()
     root.title("Batalla Naval - Juego por Turnos - Preparate!")
     juego = JuegoBatallaNaval(root)
     root.mainloop()
     
