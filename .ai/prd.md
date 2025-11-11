# Dokument wymagań produktu (PRD) - 10xCards (MVP)

## 1. Przegląd produktu

10xCards to aplikacja internetowa zaprojektowana w celu usprawnienia procesu nauki poprzez automatyzację tworzenia fiszek edukacyjnych. Wykorzystując sztuczną inteligencję, aplikacja pozwala użytkownikom na szybkie generowanie wysokiej jakości kart z dowolnego tekstu, eliminując czasochłonne zadanie ich manualnego przygotowywania. Aplikacja kierowana jest do szerokiej grupy odbiorców, od studentów po profesjonalistów, którzy chcą efektywnie wykorzystywać technikę powtarzania w interwałach (spaced repetition) do utrwalania wiedzy. Wersja MVP skupia się na kluczowych funkcjonalnościach: generowaniu fiszek przez AI, zarządzaniu nimi oraz prostym systemie nauki opartym na gotowym algorytmie SM-2.

## 2. Problem użytkownika

Manualne tworzenie fiszek jest jednym z najskuteczniejszych sposobów nauki, ale jest również niezwykle czasochłonne i pracochłonne. Uczniowie i osoby uczące się często rezygnują z tej metody, ponieważ wysiłek włożony w przygotowanie materiałów jest zbyt duży w stosunku do dostępnego czasu. Brak łatwego i szybkiego sposobu na przekształcenie notatek, artykułów czy fragmentów książek w gotowe do nauki fiszki stanowi barierę w adopcji metody spaced repetition. 10xCards ma na celu rozwiązanie tego problemu, redukując czas tworzenia fiszek z godzin do minut.

## 3. Wymagania funkcjonalne

### 3.1. System kont użytkowników

- Użytkownicy mogą zakładać konto za pomocą adresu e-mail i hasła.
- Użytkownicy mogą logować się na swoje konto.
- Dane użytkownika (w tym kolekcja fiszek) są bezpiecznie przechowywane.

### 3.2. Generowanie fiszek przez AI

- Użytkownik może wkleić tekst źródłowy o długości od 1 000 do 10 000 znaków.
- AI generuje od 5 do 100 fiszek na podstawie dostarczonego tekstu.
- Wygenerowane fiszki mają format Pytanie-Odpowiedź lub Termin-Definicja.
- Awers fiszki jest ograniczony do 200 znaków, a rewers do 500 znaków.
- Podczas generowania wyświetlana jest animacja ładowania.

### 3.3. Przegląd i akceptacja fiszek

- Po wygenerowaniu, fiszki pojawiają się na liście do przeglądu.
- Użytkownik może każdą fiszkę indywidualnie:
    - Zaakceptować: fiszka jest dodawana do głównej kolekcji użytkownika.
    - Edytować: użytkownik może zmodyfikować treść awersu i rewersu przed akceptacją.
    - Odrzucić: fiszka jest trwale usuwana.
- Nieprzejrzane fiszki z sesji są zapisywane w `localStorage`, a użytkownik jest informowany o możliwości ich wznowienia przy następnej wizycie.

### 3.4. Zarządzanie kolekcją fiszek

- Wszystkie zaakceptowane fiszki (zarówno wygenerowane przez AI, jak i stworzone manualnie) znajdują się na jednej liście.
- Użytkownik może tworzyć fiszki manualnie za pomocą prostego formularza (awers/rewers).
- Użytkownik może edytować istniejące fiszki w swojej kolekcji. Edycja resetuje postęp nauki (parametry SM-2).
- Użytkownik może trwale usuwać fiszki ze swojej kolekcji.
- Zaimplementowana jest prosta, kliencka wyszukiwarka tekstowa do filtrowania fiszek na liście.

### 3.5. System nauki (Spaced Repetition)

- Aplikacja wykorzystuje gotową implementację algorytmu SM-2.
- Codziennie prezentowana jest użytkownikowi lista fiszek zaplanowanych do powtórki.
- W interfejsie nauki, po odsłonięciu odpowiedzi, użytkownik ocenia swoją znajomość, wybierając jedną z trzech opcji: "Nie wiem", "Trudne", "Łatwe".
- Ocena aktualizuje parametry SM-2 dla danej fiszki, planując jej następną powtórkę.

## 4. Granice produktu

Następujące funkcjonalności celowo NIE wchodzą w zakres wersji MVP:

- Zaawansowany, autorski algorytm powtórek (np. oparty na SuperMemo).
- Import plików w formatach takich jak PDF, DOCX, itp.
- Możliwość grupowania fiszek w talie lub foldery.
- Współdzielenie zestawów fiszek między użytkownikami.
- Integracje z zewnętrznymi platformami edukacyjnymi.
- Dedykowane aplikacje mobilne (produkt jest dostępny tylko jako aplikacja webowa).
- System logowania przez dostawców zewnętrznych (np. Google, Facebook).

## 5. Historyjki użytkowników

### ID: US-001

- Tytuł: Rejestracja nowego użytkownika
- Opis: Jako nowy użytkownik, chcę móc założyć konto za pomocą mojego adresu e-mail i hasła, abym mógł bezpiecznie przechowywać moje fiszki.
- Kryteria akceptacji:
    1. Formularz rejestracji zawiera pola na adres e-mail, hasło i potwierdzenie hasła.
    2. Walidacja po stronie klienta sprawdza, czy adres e-mail ma poprawny format.
    3. Walidacja po stronie klienta sprawdza, czy hasła w obu polach są identyczne.
    4. Po pomyślnej rejestracji, jestem automatycznie zalogowany i przekierowany na stronę główną.
    5. W przypadku błędu (np. zajęty e-mail), wyświetlany jest czytelny komunikat.

### ID: US-002

- Tytuł: Logowanie użytkownika
- Opis: Jako zarejestrowany użytkownik, chcę móc zalogować się na swoje konto, aby uzyskać dostęp do mojej kolekcji fiszek.
- Kryteria akceptacji:
    1. Formularz logowania zawiera pola na adres e-mail i hasło.
    2. Po podaniu poprawnych danych i kliknięciu "Zaloguj", uzyskuję dostęp do aplikacji.
    3. W przypadku podania błędnych danych, wyświetlany jest stosowny komunikat.

### ID: US-003

- Tytuł: Ekran powitalny dla nowych użytkowników
- Opis: Jako nowy użytkownik, po pierwszym zalogowaniu chcę zobaczyć prosty ekran powitalny, który wyjaśni mi, jak wygenerować moje pierwsze fiszki.
- Kryteria akceptacji:
    1. Ekran powitalny jest wyświetlany tylko raz, bezpośrednio po pierwszej rejestracji/logowaniu.
    2. Zawiera krótką instrukcję, jak wkleić tekst i rozpocząć generowanie.
    3. Posiada wyraźny przycisk lub link prowadzący do generatora.

### ID: US-004

- Tytuł: Generowanie fiszek z tekstu
- Opis: Jako użytkownik, chcę wkleić fragment tekstu z moich notatek i automatycznie wygenerować z niego fiszki, aby zaoszczędzić czas.
- Kryteria akceptacji:
    1. Na stronie głównej znajduje się pole tekstowe do wklejania treści.
    2. Pole tekstowe akceptuje tekst o długości od 1 000 do 10 000 znaków.
    3. Przycisk "Generuj" jest aktywny tylko wtedy, gdy długość tekstu mieści się w zadanym przedziale.
    4. Po kliknięciu "Generuj" wyświetlana jest animacja ładowania.
    5. Po zakończeniu generowania, pod formularzem pojawia się lista fiszek do przeglądu.

### ID: US-005

- Tytuł: Walidacja długości tekstu wejściowego
- Opis: Jako użytkownik, próbując wygenerować fiszki, chcę otrzymać informację zwrotną, jeśli wklejony tekst jest za krótki lub za długi.
- Kryteria akceptacji:
    1. Gdy tekst ma mniej niż 1 000 znaków, wyświetlany jest komunikat "Tekst jest za krótki. Wymagane jest minimum 1 000 znaków.".
    2. Gdy tekst ma więcej niż 10 000 znaków, wyświetlany jest komunikat "Tekst jest za długi. Maksymalna długość to 10 000 znaków.".
    3. Przycisk "Generuj" pozostaje nieaktywny w obu powyższych przypadkach.

### ID: US-006

- Tytuł: Przegląd, akceptacja i odrzucenie wygenerowanych fiszek
- Opis: Jako użytkownik, po wygenerowaniu fiszek chcę mieć możliwość ich przejrzenia, aby zadecydować, które z nich dodać do mojej kolekcji.
- Kryteria akceptacji:
    1. Każda wygenerowana fiszka na liście przeglądu ma widoczny awers i rewers.
    2. Każda fiszka posiada przyciski "Akceptuj" i "Odrzuć".
    3. Kliknięcie "Akceptuj" przenosi fiszkę do mojej głównej kolekcji i usuwa ją z listy przeglądu.
    4. Kliknięcie "Odrzuć" usuwa fiszkę z listy przeglądu bez dodawania jej do kolekcji.

### ID: US-007

- Tytuł: Edycja fiszki podczas przeglądu
- Opis: Jako użytkownik, chcę mieć możliwość poprawienia błędów lub zmiany treści wygenerowanej fiszki, zanim dodam ją do mojej kolekcji.
- Kryteria akceptacji:
    1. Każda fiszka na liście przeglądu posiada przycisk "Edytuj".
    2. Kliknięcie "Edytuj" zamienia statyczny tekst fiszki na edytowalne pola tekstowe.
    3. Po dokonaniu zmian, przycisk "Zapisz" staje się aktywny.
    4. Kliknięcie "Zapisz" zatwierdza zmiany i automatycznie akceptuje fiszkę, przenosząc ją do głównej kolekcji.

### ID: US-008

- Tytuł: Wznowienie niedokończonej sesji przeglądu
- Opis: Jako użytkownik, jeśli przypadkowo zamknę kartę przeglądarki podczas przeglądania wygenerowanych fiszek, chcę mieć możliwość wznowienia tej sesji później.
- Kryteria akceptacji:
    1. Fiszki oczekujące na przegląd są automatycznie zapisywane w `localStorage`.
    2. Gdy wrócę do aplikacji, a w `localStorage` znajduje się niezakończona sesja, wyświetlane jest powiadomienie z pytaniem "Masz nieprzejrzane fiszki. Czy chcesz do nich wrócić?".
    3. Wybór "Tak" przywraca listę fiszek do przeglądu w stanie, w jakim ją zostawiłem.
    4. Wybór "Nie" usuwa zapisaną sesję z `localStorage`.

### ID: US-009

- Tytuł: Manualne tworzenie fiszki
- Opis: Jako użytkownik, chcę mieć możliwość ręcznego dodania nowej fiszki do mojej kolekcji, gdy mam w głowie konkretne pytanie i odpowiedź.
- Kryteria akceptacji:
    1. Aplikacja udostępnia formularz z polami "Awers" i "Rewers".
    2. Walidacja sprawdza, czy oba pola nie są puste.
    3. Po wypełnieniu i zapisaniu, nowa fiszka jest dodawana bezpośrednio do mojej głównej kolekcji.

### ID: US-010

- Tytuł: Przeglądanie i wyszukiwanie kolekcji fiszek
- Opis: Jako użytkownik z dużą bazą fiszek, chcę móc szybko wyszukać konkretną kartę, aby ją edytować lub usunąć.
- Kryteria akceptacji:
    1. Wszystkie moje zaakceptowane fiszki są wyświetlane na jednej, przewijanej liście.
    2. Na stronie znajduje się pole wyszukiwania.
    3. Wpisywanie tekstu w pole wyszukiwania filtruje listę fiszek w czasie rzeczywistym, dopasowując frazę do treści awersu i rewersu.
    4. Wyszukiwanie jest niewrażliwe na wielkość liter.

### ID: US-011

- Tytuł: Edycja fiszki z kolekcji
- Opis: Jako użytkownik, chcę móc edytować fiszkę, która już znajduje się w mojej kolekcji, aby poprawić błędy lub zaktualizować informacje.
- Kryteria akceptacji:
    1. Każda fiszka na liście kolekcji ma przycisk "Edytuj".
    2. Kliknięcie "Edytuj" otwiera formularz z załadowaną treścią fiszki.
    3. Po zapisaniu zmian, treść fiszki w kolekcji jest zaktualizowana.
    4. Zapisanie edytowanej fiszki powoduje zresetowanie jej postępu w algorytmie SM-2 do stanu początkowego.

### ID: US-012

- Tytuł: Usuwanie fiszki z kolekcji
- Opis: Jako użytkownik, chcę móc trwale usunąć fiszkę z mojej kolekcji, jeśli uznam, że nie jest mi już potrzebna.
- Kryteria akceptacji:
    1. Każda fiszka na liście kolekcji ma przycisk "Usuń".
    2. Kliknięcie "Usuń" wyświetla modal z prośbą o potwierdzenie operacji.
    3. Po potwierdzeniu, fiszka jest nieodwracalnie usuwana z mojej kolekcji.

### ID: US-013

- Tytuł: Rozpoczęcie sesji nauki
- Opis: Jako użytkownik, chcę, aby aplikacja każdego dnia podpowiadała mi, które fiszki powinienem powtórzyć, abym mógł efektywnie utrwalać wiedzę.
- Kryteria akceptacji:
    1. W interfejsie znajduje się przycisk "Ucz się", który rozpoczyna sesję nauki.
    2. Sesja nauki prezentuje tylko te fiszki, których data powtórki według algorytmu SM-2 przypada na dziś lub minęła.
    3. Fiszki są prezentowane pojedynczo, najpierw tylko awersem.

### ID: US-014

- Tytuł: Ocenianie odpowiedzi podczas nauki
- Opis: Jako użytkownik, po zobaczeniu odpowiedzi na fiszce, chcę ocenić, jak dobrze ją znałem, aby algorytm mógł zaplanować kolejną powtórkę.
- Kryteria akceptacji:
    1. Po wyświetleniu awersu, kliknięcie przycisku "Pokaż odpowiedź" odsłania rewers.
    2. Po odsłonięciu rewersu pojawiają się trzy przyciski oceny: "Nie wiem", "Trudne", "Łatwe".
    3. Wybranie jednej z opcji powoduje zaktualizowanie parametrów SM-2 dla danej fiszki i wyświetlenie kolejnej karty z sesji.
    4. Po przejściu wszystkich zaplanowanych fiszek, wyświetlany jest ekran podsumowujący sesję.

## 6. Metryki sukcesu

Kluczowe wskaźniki (KPI), które będą mierzone w celu oceny sukcesu produktu:

1. Jakość generowania AI:
    - Metryka: Procent fiszek zaakceptowanych przez użytkownika (bezpośrednio lub po edycji).
    - Cel: 75%.
    - Sposób pomiaru: Śledzenie akcji (Akceptuj, Edytuj+Akceptuj, Odrzuć) na ekranie przeglądu wygenerowanych fiszek.

2. Adopcja funkcji AI:
    - Metryka: Procent fiszek w systemie stworzonych przy użyciu generatora AI w stosunku do fiszek stworzonych manualnie.
    - Cel: 75%.
    - Sposób pomiaru: Analiza źródła pochodzenia każdej nowo utworzonej fiszki w bazie danych.

3. Dodatkowe metryki jakościowe:
    - Metryka odrzuceń: Procent fiszek jawnie odrzuconych przez użytkowników na ekranie przeglądu.
    - Metryka edycji: Procent fiszek, które zostały zaakceptowane po uprzedniej edycji.
    - Sposób pomiaru: Obie metryki będą monitorowane w celu identyfikacji problemów z jakością generowania i iteracyjnego ulepszania promptów dla modelu AI.
