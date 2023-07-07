# segundo_parcial_spd

# Integrantes
Franco Sofia


# Proyecto : sistema de incendio
![image](https://github.com/francosofia/segundo_parcial_spd/assets/108673571/e7de133c-c800-4e13-b31f-cb36eb1a2ee0)

# Descripcion
El circuito nos advierte la temperatura por un display y a su vez en que estacion del año estamos segun la temperatura  hambiente (invierno,otoño[tuvimos porblema spara colocar una ñ asique lo hicimos n i],primavera,verano), ademasd de una led verde indicando que todo esta normal y  cuando la temperatura alcanza los 60°  o superir  cuando esto sucede el servo emula ser una respuesta del sistema de incendio y  el sistema nos advierte de fuego mostrandolo en el display y  por medio de una led roja que se enciende

#Funcion principal
El codigo tiene una sola funcion advertir  la temperatura y la estacion 

    void display_lcd()
     {
   
    lecturaSensor = analogRead(A0);
    temperatura = map(lecturaSensor, 20, 358, -40, 125);
    //Seteo el cursor de donde quiero escribir
    lcd.setCursor(0, 0); //(columna:0) de la primer línea(fila:0)
    lcd.print(temperatura);//Escribo la temperatura
    lcd.print(" grados ");
    delay(100);
    
     if( temperatura > -40 && temperatura < 8)
     {
   
     lcd.setCursor(0, 1); //(indico que se prenda la lde y marco la estacion segun la temepratura
    lcd.print("invierno");
    digitalWrite(5, HIGH);
   
     }
    if( temperatura > 9 && temperatura < 18)
    {
   
     lcd.setCursor(0, 1); 
    lcd.print("otonio     ");
    digitalWrite(5, HIGH);
   
    }
    if( temperatura > 19 && temperatura < 28)
    {
  
     lcd.setCursor(0, 1); 
    lcd.print("primavera     ");
    digitalWrite(5, HIGH);
   
    }
     if( temperatura > 29 && temperatura < 59)
    {
   
     lcd.setCursor(0, 1);
      lcd.print("verano      ");
     digitalWrite(5, HIGH);
   
    }
    if( temperatura > 60 && temperatura < 125)
    {
   
     lcd.setCursor(0, 1); 
      lcd.print("fuego         ");
     digitalWrite(5, LOW);
    }
   
    }


# Diagrama esquematico del circuito

![Diagrama esquematico del circuito](https://github.com/francosofia/segundo_parcial_spd/assets/108673571/8bacbdb1-83ff-4425-baaf-72abceea1ead)



