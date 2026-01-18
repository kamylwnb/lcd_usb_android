# 🖥️ RPi Pico - Zdalny Ekran USB (usbscreen)

System umożliwiający przesyłanie zawartości wyświetlacza Twojego urządzenia bezpośrednio na ekran telefonu Android lub komputera PC.

---

## 📱 Aplikacja Mobilna (Android)

Dzięki tej aplikacji Twój telefon staje się bezprzewodowym (lub przewodowym przez USB) monitorem dla Twojego projektu.

### 📥 Instalacja
1. **Pobierz APK:
2. **Zainstaluj:** Otwórz pobrany plik na telefonie (może być wymagana zgoda na "Instalację z nieznanych źródeł").
3. **Połącz:** - Użyj adaptera **USB OTG**, aby połączyć Pico z telefonem.
   - W aplikacji kliknij przycisk **"Connect"**.
   - Wybierz prędkość **115200 baud**.



---

## 🛠️ Instrukcja wysyłania obrazu (C++)

Aplikacja nasłuchuje na porcie szeregowym linii zaczynających się od słowa kluczowego `SCRN:`. Po nim następuje 1024 bajty Twojego ekranu zamienione na tekst HEX.

### 1. Dodaj funkcję do swojego projektu
Skopiuj ten kod do pliku, w którym obsługujesz ekran (np. `ekran.cpp`):

```cpp
void send_screen_buffer_usb() {
    // Sprawdź czy funkcja jest aktywna (opcjonalne)
    if (!remote_display_on) return; 

    // Odwołanie do bufora graficznego (128x64 px = 1024 bajty)
    extern uint8_t ST7565_buffer[1024]; 
    
    // Wysłanie nagłówka
    printf("SCRN:"); 
    
    // Konwersja bufora na tekst HEX i wysyłka przez USB
    for (int i = 0; i < 1024; i++) {
        printf("%02X", ST7565_buffer[i]);
    }
    
    // Znak końca linii informuje aplikację o pełnej klatce
    printf("\n");
    fflush(stdout);
}
