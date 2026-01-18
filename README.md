<hr style="margin:40px 0;">

    <h2>📱 Aplikacja Mobilna (Android APK)</h2>
    <div class="info">
        <strong>Szybki start:</strong> Możesz podglądać ekran swojego urządzenia bezpośrednio na smartfonie! Aplikacja działa z dowolnym mikrokontrolerem wysyłającym dane w formacie HEX (np. RPi Pico, Arduino, ESP32).
    </div>

    <h3>Jak połączyć urządzenie z telefonem:</h3>
    <ol>
        <li><strong>Pobierz aplikację:</strong> Ściągnij plik <code>usbscreen_remote.apk</code> z sekcji wydań (Releases) na tym GitHubie i zainstaluj go na swoim telefonie.</li>
        <li><strong>Użyj kabla OTG:</strong> Podłącz swoje Raspberry Pi Pico (lub inne urządzenie) do telefonu za pomocą przejściówki <strong>USB OTG</strong>.</li>
        <li><strong>Uruchom i połącz:</strong>
            <ul>
                <li>Otwórz aplikację.</li>
                <li>Kliknij przycisk <b>"Połącz / Connect"</b>.</li>
                <li>Zezwól aplikacji na dostęp do urządzenia USB w wyskakującym okienku Androida.</li>
                <li>Ustaw prędkość na <b>115200 baud</b>.</li>
            </ul>
        </li>
        <li><strong>Działaj!</strong> Jeśli Twoje urządzenie wysyła ramki <code>SCRN:...</code>, obraz natychmiast pojawi się na wyświetlaczu telefonu.</li>
    </ol>

    <div class="warning">
        <strong>💡 Pro tip:</strong> Aplikacja jest uniwersalna. Choć polecamy <strong>RPi Pico</strong> ze względu na wydajność, możesz użyć dowolnego modułu, który potrafi wysyłać tekst przez Serial. Pamiętaj tylko o wspólnej masie (GND) i poprawnym standardzie napięć (3.3V dla Pico).
    </div>

    <h3>Dlaczego warto używać trybu USB Screen?</h3>
    <ul>
        <li><strong>Debugowanie:</strong> Widzisz co dzieje się na ekranie, nawet jeśli nie masz fizycznego wyświetlacza ST7565 pod ręką.</li>
        <li><strong>Prezentacje:</strong> Możesz pokazać działanie swojego projektu na dużym ekranie telefonu lub rzutniku (przez telefon).</li>
        <li><strong>Zdalne sterowanie:</strong> Idealne do testowania interfejsu użytkownika i menu bez patrzenia na mały ekranik urządzenia.</li>
    </ul>

    <p style="text-align: center; margin-top: 30px;">
        <a href="usbscreen_remote.apk" style="background-color: #28a745; color: white; padding: 15px 25px; text-decoration: none; border-radius: 5px; font-weight: bold;">📥 Pobierz aplikację .APK</a>
    </p>
