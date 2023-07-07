# segundo_parcial_spd

# Integrantes
Franco Sofia


# Proyecto : sistema de incendio
![image](https://github.com/francosofia/segundo_parcial_spd/assets/108673571/e7de133c-c800-4e13-b31f-cb36eb1a2ee0)

# Descripcion
El circuito nos advierte la temperatura por un display y a su vez en que estacion del año estamos segun la temperatura  hambiente (invierno,otoño[tuvimos porblema spara colocar una ñ asique lo hicimos n i],primavera,verano), ademasd de una led verde indicando que va a mostrar una estacion y  cuando la temperatura alcanza los 60°  o superir  cuando esto sucede el servo emula ser una respuesta del sistema de incendio y  el sistema nos advierte de fuego mostrandolo en el display y  por medio de una led roja que se enciende

#Funcion principal
esta funcion lo que hace es detectar si tocas el boton de subir o bajar y le suma o resta al contador dado el caso .En el caso que el contador sea  1 muestra inviero , 2 otoño , 3 primavera y 4 verano y en caso de que no este seleccionada ninguna estacion no muestra nada

    void control_estaciones()
    {
      if (IrReceiver.decode())//subo o bajo el contador segun que boton toco
      {
        if (IrReceiver.decodedIRData.decodedRawData == BOTON_SUBIR)
        {
          Serial.println("sube");
              contador += 1;
        }
        if (IrReceiver.decodedIRData.decodedRawData == BOTON_BAJAR)
        {
          Serial.println("baja");
          contador -= 1;
        }
        IrReceiver.resume();
      }

      Serial.println(contador);

      if (contador >= 1 && contador <= 4)
      {
        lcd.setCursor(0, 1);
        digitalWrite(5, HIGH);

    switch (contador)
    {
      case 1://pongo la estacion segun el caso dado
        lcd.print("invierno      ");
        break;
      case 2:
        lcd.print("otonio        ");
        break;
      case 3:
        lcd.print("primavera     ");
        break;
      case 4:
        lcd.print("verano        ");
        break;
    }
      }
      else
      {
    lcd.setCursor(0, 1);
    lcd.print("                "); // Borra la segunda fila del display si no se ha seleccionado ninguna estación válida
    digitalWrite(5, LOW);
      }
    }

# Diagrama esquematico del circuito

![Diagrama esquematico del circuito](https://github.com/francosofia/segundo_parcial_spd/assets/108673571/8bacbdb1-83ff-4425-baaf-72abceea1ead)

# Posibles errores
Un error que puede aparecer es que las estaciones titles y no se vean bien 

