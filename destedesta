// casistrobo con neopixelbus
//Incluir la biblioteca de la tira de leds Esta se baja con la utileria de manejo de blibliotecas de arduino include
#include <NeoPixelBus.h>

// Defiinimos el numero de LEDs en cada franja. Queda en 20 porque iniciamos ciclos desde cero.
const uint16_t PixelCount = 20;
//definimos uno de los pines de señal
const uint8_t PixelPin = 12;
//definimos el otro pin
const uint8_t PinPixel = 13;
definimos un nivel de intensidad estandar
#define colorSaturation 127  //la saturacion los hace mas o menos intensos.

// three element pixels, in different order and speeds
//Definimos el prototipo de las clases NeoPixelBus. strip es un metodo de esa clase
//y toma dos parametros. El primero es el numero de LED y el segundo es el pin  que definimos antes.
//Se declara un prototipo para cada metodo. Obserba lod nomnbres PixelPin y PinPixel
NeoPixelBus<NeoGrbFeature, Neo800KbpsMethod> strip(PixelCount, PixelPin);
NeoPixelBus<NeoGrbFeature, Neo800KbpsMethod> strit(PixelCount, PinPixel);

//Definimos el color azul
RgbColor blue(0, 0, colorSaturation);
//Definimos el color rojo
RgbColor red(colorSaturation, 0, 0);
//Definimos el color blanco
RgbColor white(colorSaturation);
//Definimos el no color
RgbColor black(0);

//inicializamos en entorno de trabajo
void setup()
{
//Checar si realmente es necesaria la terminal
    Serial.begin(115200);
    while (!Serial); // wait for serial attach

    Serial.println();
    Serial.println("Inicializando...");
    Serial.flush();

//esto apaga todos los leds
    strip.Begin();
    strip.Show();
    strit.Begin();
    strit.Show();


    Serial.println();
    Serial.println("Ejecutando...");
}

//Funcion de encendido de la franja azul
void azul()
{
  //establecemos un primer ciclo de tres iteraciones para simular el destelleo
  //parecido al destello estroboscopico
    for(int j = 0; j < 3; j++)
    {
	//establecemps un ciclo de 7 iteraciones para encender uno por uno
	//los leds de cada tira.
	//sabemos que 2 son de 7 y una es de 5 pero para no ocupar ciclos
	//de control mejor gastamos dos iteraciones en el vacio. 
      for(int i = 0; i < 7; i++)
      {
		//ponemos el color en el primer led de la primera tira cuando i es cero
        strip.SetPixelColor(i, blue); 
        //pomemos el color en el primer led de la segunda tira. 
        //pero como esta 7 leds adelante, le sumamos 7
        strip.SetPixelColor(i+7, white);
        //pomemos el color en el primer led de la segunda tira. 
        //pero como esta 14 leds adelante del primero, le sumamos 14        
        //aqui es donde dos instrucciones se hacen de mas.
        strip.SetPixelColor(i+14, blue);
        //luego de poner el color en cada led, le decimos que lo prenda.
        strip.Show();
		//pomemos un retardo de tres milesimas de segundo
        delay(3);
      }
      //establecemos un ciclo igual al anterior pero ahora para apagar cada LED.
      for(int i = 0; i < 7; i++)
      {
        strip.SetPixelColor(i, black);
        strip.SetPixelColor(i+7, black);
        strip.SetPixelColor(i+14, black);
        strip.Show();
        delay(3); //con este delay esta equilibrado. sin el de abajo parece direccional
        }
    }
    //despues de encender tres veces los leds esperamos 200 milisegundos antes de regresar al ciclo principal
    delay(200);
}

//Funcion de encendido de la franja roja
//esta funcion es exactamente igual a la anterior 
void rojo()
{
    for(int j = 0; j < 3; j++)
    {
      for(int i = 0; i < 7; i++)
      {
        strit.SetPixelColor(i, red);
        strit.SetPixelColor(i+7, white);
        strit.SetPixelColor(i+14, red);
        strit.Show();
        delay(3); 
      }
      for(int i = 0; i < 7; i++)
      {
        strit.SetPixelColor(i, black);
        strit.SetPixelColor(i+7, black);
        strit.SetPixelColor(i+14, black);
        strit.Show();
        delay(3); //con este delay esta equilibrado. sin el de abajo parece direccional
        }
    }
    delay(200);//con 200 esta bien, vamos a ver con 100. Muy rapido con 100 y 150
}
//Esta funcion se realiza en un ciclo permanente
void loop()
{
  //primero enciende la franja azul
  azul();
  //hace una pausa de 150 milisegundos (ms)
  delay(150);
  //luego enciende el rojo
  rojo();
}
