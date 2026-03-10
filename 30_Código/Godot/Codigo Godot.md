---
tipo: snippet
lenguaje: Godot
tags:
  - programacion
  - snippet
fecha_inicio: <% tp.date.now("YYYY-MM-DD") %>
---
# 💻 Snippet: Codigo Godot

> [!QUESTION] ¿Qué hace este código?
> Codigo de Godot se encarga de:
> Dar gravedad a nuestro personaje
> Acciones por inputs de teclas como el salto y movimientos laterales
> Animaciones para los movientos anteriormente dichos
> 

## [[Bitacora de Proyecto - Juego -|Bitacora de este codigo ]]
## 🛠️ Implementación
```bash
extends CharacterBody2D

@export var animacion: AnimatedSprite2D 
@export var area_2d: Area2D

var _velocidad: float = 100.0
var _velocidad_salto: float = -300.0

func ready():
	pass

func _physics_process(delta):

	# --- Gravedad ---
	velocity += get_gravity() * delta
	
	# ---#Salto ---
	if Input.is_action_just_pressed("Saltar") and is_on_floor():
		velocity.y = _velocidad_salto
	
	# --- Movimiento lateral ---
	if Input.is_action_pressed("Derecha"):
		velocity.x = _velocidad
		animacion.flip_h = true
	elif Input.is_action_pressed("Izquierda"):
		velocity.x = -_velocidad
		animacion.flip_h = false
	else:
		velocity.x = 0	
	move_and_slide()
	# --- Animaciones para los movimientos ---
	if !is_on_floor():
		animacion.play("saltar")
	elif velocity.x != 0:
		animacion.play("correr")
	else:
		animacion.play("idle")


func _on_area_2d_body_entered(body: Node2D) -> void:
	pass # Replace with function body.