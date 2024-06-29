#include <DHT.h>
#include <LiquidCrystal_I2C.h>

DHT dht(2, DHT11);
int temp;
int humidity;
int dt = 2000;
5
LiquidCrystal_I2C lcd (0x27, 16, 2);

void setup()
{
   dht.begin();

   lcd.init();
   lcd.backlight();
}

void loop()
{
  delay(dt);
   temp = dht.readTemperature();
   humidity = dht.readHumidity();

   lcd.setCursor(0,0);
   lcd.print("Temp: ");
   lcd.print(temp);
   lcd.print(" C");

   lcd.setCursor(0, 1);
   lcd.print("Humidity");
   lcd.print(humidity);
   lcd.print(" %");
}
