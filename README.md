https://drive.google.com/file/d/15ttCTZDYG83opVHWh6F1MpwLtcDXsAQX/view?usp=sharing

// LCD display thriugh arduino

#include <LiquidCrystal.h>

LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

byte character1[8] = {
  B11111,
  B10001,
  B11111,
  B10001,
  B11111,
  B10001,
  B11111,
  B10001
};

byte character2[8] = {
  B10001,
  B10001,
  B11011,
  B11111,
  B11111,
  B11011,
  B10001,
  B10001
};

byte character3[8] = {
  B01010,
  B10101,
  B01010,
  B10101,
  B01010,
  B10101,
  B01010,
  B10101
};

void setup() {
  lcd.begin(16, 2);

  lcd.createChar(0, character1);
  lcd.createChar(1, character2);
  lcd.createChar(2, character3);

  lcd.clear();

  lcd.setCursor(0, 0);

  lcd.write((uint8_t)0);
  lcd.write((uint8_t)1);
  lcd.write((uint8_t)2);

  Serial.begin(9600);
}

void loop() {
  if (Serial.available()) {
    char command = Serial.read();
    lcd.clear();
    lcd.setCursor(0, 0);
    switch (command) {
      case '1':
        lcd.write((uint8_t)0);
        break;
      case '2':
        lcd.write((uint8_t)1);
        break;
      case '3':
        lcd.write((uint8_t)2);
        break;
    }
  }
}
