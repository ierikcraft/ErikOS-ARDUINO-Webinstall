# Qué tiene ErikOS

>[!NOTE]
>**Sistema UI “ErikOS” (LVGL)**
>
>- Pantalla de arranque, menú principal con iconos, y navegación entre apps.
>- Teclado global de LVGL para escribir en campos de texto.
>- WiFi inteligente

**Intenta conectar al WiFi guardado.**

- Si falla, abre portal con WiFiManager para configurar.
- Opción “Omitir” si existe una red guardada.

## **Cuenta en la nube (Firestore)**

- Variables globales: email, name, id, issigned.
- Inicio de sesión con Mail + Contraseña (no usa Firebase Auth tradicional, se valida contra documentos en users en Firestore).
- Guarda sesión en NVS (Preferences) para persistencia (como el WiFi).

## **Pantalla de bienvenida tras login.**

**Si ya hay sesión: muestra tu nombre en Ajustes, permite cambiar nombre (actualiza Firestore) y cerrar sesión.**

## **Chat (Firestore)**

- App “Chat” con: Campo para crear un chat privado buscando por Nombre.
- Lista de chats (rooms) con botón para abrir y otro para eliminar.
- Al abrir un chat: pantalla de mensajes + input para enviar.
- Descarga rooms desde erikchat_rooms y mensajes desde erikchat_messages.

## Anti-bootloop: 
```tsx
no hace llamadas HTTP durante setup(). Solo consulta Firestore cuando entras al chat o pulsas “Refrescar”.**
```

> [!IMPORTANT]
>## **Erik AI (Groq)**
>
>- Chatbot usando API compatible con OpenAI (chat completions) en Groq.
>- Interfaz tipo chat dentro de la app “Asistente”.

## Más cosas
>**Reloj**
>
>- Hora por NTP, mostrada en barra de estado y en app “Reloj”.

>**Tiempo (OpenWeatherMap)**
>
>- Muestra ciudad, temperatura, descripción e icono.
>- Actualiza cada 10 minutos.

>**Linterna**
>
>- Control de GPIO RGB (4/16/17) con switch.

>**Cronómetro**
>
>- Start/Stop/Reset con timer a 50 ms.

## **Info del sistema**

- Versión, build, WiFi, IP, MAC, heap libre, uptime (actualiza cada segundo).


> [!IMPORTANT]
>**Actualización por SD**
>
>- Permite flashear firmware desde /1.bin…/5.bin usando Update.h.
>- Bloquea el táctil durante el update para evitar errores.
