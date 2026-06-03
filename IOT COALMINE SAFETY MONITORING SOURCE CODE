```cpp
#include <LiquidCrystal.h>

#define buzzer 7
#define gassensor 2
#define flamesensor 3

int temppin = A1;

const int rs = 13, en = 12, d4 = 11, d5 = 10, d6 = 9, d7 = 8;

LiquidCrystal lcd(rs, en, d4, d5, d6, d7);

void setup()
{
    lcd.begin(16, 2);

    pinMode(gassensor, INPUT);
    pinMode(flamesensor, INPUT);
    pinMode(buzzer, OUTPUT);

    Serial.begin(9600);
}

void loop()
{
    int tempval = analogRead(temppin);

    float mv = (tempval / 1024.0) * 5000;
    float temp = mv / 10;

    int gassensorval = digitalRead(gassensor);
    int flamesensorval = digitalRead(flamesensor);

    if (temp > 40 || gassensorval == HIGH || flamesensorval == HIGH)
    {
        digitalWrite(buzzer, HIGH);

        lcd.setCursor(0, 0);
        lcd.print("ALERT!");

        Serial.println("ALERT!");

        delay(500);
        lcd.clear();
    }
    else
    {
        digitalWrite(buzzer, LOW);

        lcd.setCursor(0, 0);
        lcd.print("Temperature");

        lcd.setCursor(0, 1);
        lcd.print(temp);

        Serial.print("Temperature: ");
        Serial.println(temp);

        delay(500);
        lcd.clear();
    }
}
```
