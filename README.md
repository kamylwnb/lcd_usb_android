# 🖥️ RPi Pico - Zdalny Ekran USB (usbscreen)

System umożliwiający przesyłanie zawartości wyświetlacza Twojego urządzenia bezpośrednio na ekran telefonu Android lub komputera PC przez port szeregowy USB.

---

## 📱 Aplikacja Mobilna (Android)

Dzięki tej aplikacji Twój telefon staje się monitorem dla Twojego projektu, łączącym się przewodowo przez port USB.

### 📥 Instalacja i Połączenie
1. **Pobierz:** Pobierz plik APK aplikacji.
2. **Zainstaluj:** Otwórz pobrany plik na telefonie (może być wymagana zgoda na "Instalację z nieznanych źródeł").
3. **Połącz:** - Użyj adaptera **USB OTG**, aby połączyć Raspberry Pi Pico z telefonem.
   - W aplikacji kliknij przycisk **"Connect"**.
   - Wybierz prędkość **115200 baud**.

---

## ⚙️ Specyfikacja Techniczna / Technical Specification

| Cecha / Feature | Wartość / Value |
| :--- | :--- |
| **Baudrate** | 115200 |
| **Format** | `SCRN:[HEX_DATA]\n` |
| **Resolution** | 128x64 px (Monochrome) |
| **Interface** | USB Serial / CDC |

---

## 🛠️ Implementacja w kodzie (C++)

Aplikacja nasłuchuje na porcie szeregowym linii zaczynających się od słowa kluczowego `SCRN:`. Poniżej znajduje się kompletna funkcja wysyłająca oraz przykład jej użycia w pętli głównej programu.

```cpp
// 1. Definicja funkcji wysyłającej dane
void send_screen_buffer_usb() {
    // Odwołanie do bufora graficznego (128x64 px = 1024 bajty)
    extern uint8_t ST7565_buffer[1024]; 
    
    // Wysłanie nagłówka komunikatu
    printf("SCRN:"); 
    
    // Konwersja bufora na tekst HEX i wysyłka przez USB
    for (int i = 0; i < 1024; i++) {
        printf("%02X", ST7565_buffer[i]);
    }
    
    // Znak końca linii informuje aplikację o pełnej klatce
    printf("\n");
    fflush(stdout);
}

// 2. Przykład użycia w pętli głównej (main loop)
// Wywołuj obie funkcje razem, aby zsynchronizować ekran fizyczny i zdalny:
void main_loop() {
    while(true) {
        // ... Twój kod rysowania ...
        
        ST7565_Update();           // Aktualizacja fizycznego LCD na urządzeniu
        send_screen_buffer_usb();  // Przesłanie kopii obrazu do aplikacji przez USB
    }
}
