# Raport z realizacji projektu 3D: Nowoczesny Samolot Pasażerski

## 1. Opis projektu i skład zespołu
Projekt polegał na stworzeniu modelu 3D prostego samolotu pasażerskiego w programie Blender. Praca była realizowana w zespole trzyosobowym, a końcowy model charakteryzuje się estetyką "low-poly" z naciskiem na czystą geometrię zewnętrzną.

Sklad zespolu: Ivan Berezka, Mikita Tsarkovich, Daniil Yakaulev

* **Mój zakres odpowiedzialności:** * Przygotowanie detali kadłuba (okna).
    * Modelowanie silników turbinowych (turbofan).
    * Konstrukcja podstawowego podwozia.
    * Integracja mechaniczna elementów (Parenting) oraz optymalizacja wyświetlania (Normals).

## 2. Wykorzystanie AI w procesie twórczym
W trakcie realizacji zadania korzystałem z modelu językowego Gemini jako konsultanta technicznego. AI pełniło rolę mentora, który:
* Sugerował odpowiednie techniki modelowania dla początkujących.
* Dostarczał linki do konkretnych materiałów edukacyjnych (YouTube).
* Pomagał w rozwiązywaniu błędów technicznych (troubleshooting), co pozwoliło na płynną realizację projektu bez przestojów.

## 3. Kluczowe rozwiązania techniczne
* **Technika Knife Project:** Zastosowana do stworzenia okien. Pozwoliło to na naniesienie detali na zakrzywiony kadłub bez wprowadzania błędów w cieniowaniu, które generowało narzędzie Boolean.
* **Maskowanie wnętrza (Black Glass Method):** Aby uniknąć modelowania pustego wnętrza samolotu, okna zostały wykończone jako czarne, błyszczące płaszczyzny. Rozwiązanie to nadało modelowi nowoczesny wygląd i ukryło brak wyposażenia kabiny.
* **Modelowanie modułowe i Symetria:** Turbiny oraz podwozie zostały wykonane jako osobne obiekty z użyciem modyfikatora **Mirror** (z kadłubem jako obiektem odniesienia), co zapewniło idealną symetrię i oszczędność czasu.
* **Zarządzanie Normalnymi i Shadingiem:** Wykorzystano funkcję **Auto Smooth** oraz przeliczanie normalnych (**Recalculate Outside**), aby wyeliminować błędy w wyświetlaniu ścianek (tzw. zgnieciona geometria).
* **Parenting:** Wszystkie elementy zostały przypisane do kadłuba relacją **Parent-Child**, co umożliwiło spójne poruszanie modelem w pliku głównym zespołu.

## 4. Wykorzystane źródła edukacyjne
* Tutoriale YouTube: *Blender Knife Project tool quick guide*, *Basic Jet Engine Modeling*, *Parenting objects in Blender*.
* Dokumentacja techniczna Blendera.
* Konsultacje merytoryczne z AI Gemini (logi poniżej).

---

## Logi z konsultacji (Przebieg prac)

**Ja:** Cześć! Pracuję z dwoma kolegami z grupy nad projektem samolotu w Blenderze. Kadłub już mamy, ale ja teraz muszę dodać okna. Próbowałem je wyciąć Booleanem, ale na okrągłym fuzelażu wszystko się gnie i cieniowanie wygląda fatalnie. Jak to zrobić najprościej?

**Gemini:** Cześć! Przy zakrzywionym kadłubie Boolean niszczy strukturę siatki. Najlepiej użyć funkcji **Knife Project**. Narysuj obrys okna jako osobny Plane, ustaw go przed samolotem i rzutuj na model (`Mesh > Knife Project`). To pozwoli Ci zachować idealną gładkość kadłuba.

**Ja:** Próbowałem, ale ten Knife Project u mnie nie reaguje. Masz jakiś filmik, który pokazuje to krok po kroku? Nie wiem, co zaznaczyć najpierw.

**Gemini:** Kolejność zaznaczania jest kluczowa. Zobacz ten tutorial: **YouTube: Blender Knife Project tutorial**. Pamiętaj: najpierw zaznaczasz "nóż" (obrys okna), potem z Shiftem kadłub, wchodzisz w **Edit Mode** i dopiero wybierasz `Mesh > Knife Project`.

**Ja:** Dobra, wycięło kształty. Ale teraz przez dziury widać, że samolot jest pusty w środku. Muszę modelować całe wnętrze? Chciałbym tego uniknąć.

**Gemini:** Nie modeluj środka. Zrób **okna "na czarno"**. Zamiast wycinać dziury na wylot, po prostu zostaw te kształty na kadłubie i nadaj im osobny, czarny materiał z niskim *Roughness* (ok. 0.1). To będzie wyglądać jak przyciemniane szyby i całkowicie ukryje pusty środek.

**Ja:** Świetny pomysł, wygląda to teraz profesjonalnie. Teraz turbiny. Nie wiem, jak zacząć, żeby miały sensowny kształt. Masz jakieś wideo o modelowaniu turbin z cylindrów?

**Gemini:** Turbinę najlepiej zrobić metodą modułową. Zobacz ten materiał: **YouTube: Modeling a simple Jet Engine in Blender**. Zacznij od zwykłego cylindra, użyj funkcji *Inset* (I) oraz *Extrude* (E) do środka, żeby stworzyć wlot powietrza.

**Ja:** Wymodelowałem jedną turbinę, ale po włączeniu "Shade Smooth" wygląda jak zgnieciona galareta. Co z tym zrobić?

**Gemini:** Wejdź w zakładkę **Data Properties** (zielony trójkąt), rozwiń **Normals** i zaznacz **Auto Smooth**. To sprawi, że płaskie powierzchnie turbiny zostaną płaskie, a tylko boki będą zaokrąglone.

**Ja:** Użyłem modyfikatora Mirror na turbinie, ale ta nowa stała się przezroczysta z jednej strony. Co jest nie tak?

**Gemini:** To problem z **Normalnymi (Normals)**. Mirror czasem odwraca kierunek ścianek. Zaznacz turbinę, wejdź w Edit Mode, zaznacz wszystko (A) i naciśnij **Alt + N -> Recalculate Outside**. Sprawdź też, czy nie masz włączonego "Backface Culling" w ustawieniach widoku.

**Ja:** Pomogło! Mirror też siedzi idealnie po zrobieniu **Ctrl + A (All Transforms)**. Ostatnia rzecz: koła zostają w miejscu, jak koledzy ruszają samolotem. Muszę to wszystko łączyć w jedną siatkę (Join)?

**Gemini:** Nie używaj Join. Użyj **Parentingu**. Zaznacz podwozie i turbiny, na końcu zaznacz kadłub i naciśnij **Ctrl + P -> Object**. Kadłub zostanie "rodzicem" i wszystkie Twoje części będą latać razem z nim, zachowując swoje materiały.

**Ja:** Dzięki! Wszystko działa i wygląda dokładnie tak, jak chcieliśmy
