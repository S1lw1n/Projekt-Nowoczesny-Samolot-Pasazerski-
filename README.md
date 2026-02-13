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

## Logi z konsultacji 

**Ja:** Cześć! Razem z dwoma kolegami z grupy robimy na zaliczenie model 3D samolotu pasażerskiego w Blenderze. Mamy już bazowy kadłub, ale teraz moja kolej na detale. Muszę dodać okna i drzwi. Próbowałem użyć Booleana, żeby wyciąć dziury, ale na okrągłym fuzelażu wszystko się gnie i cieniowanie wygląda fatalnie. Jak to ugryźć?

**Gemini:** Cześć! Boolean przy zaokrąglonych powierzchniach to najkrótsza droga do błędów w cieniowaniu. Na okrągłym kadłubie najlepiej użyć funkcji **Knife Project**. Pozwala ona rzutować płaski kształt na zakrzywioną powierzchnię. Narysuj obrys okna jako osobny obiekt (Plane), ustaw go przed samolotem i rzutuj na model. To zachowa gładkość bazy.

**Ja:** Próbowałem tego Knife Project, ale szczerze mówiąc, u mnie to w ogóle nie reaguje. Klikam w menu i nic się nie wycina, albo dostaję błąd, że nie znaleziono obiektów do cięcia. Masz jakiś konkretny filmik, który pokazuje to krok po kroku?

**Gemini:** Kolejność zaznaczania i tryb są tu kluczowe. Zobacz ten krótki tutorial:
* **[YouTube: Blender Knife Project tool quick guide]** (Wyszukaj: Blender Knife Project tutorial)
Pamiętaj: najpierw zaznaczasz w Object Mode swój „nóż” (obrys okna), potem z Shiftem kadłub, wchodzisz w Edit Mode i dopiero wybierasz z menu na górze Mesh > Knife Project.

**Ja:** Obejrzałem, robię dokładnie tak samo i dalej nic. Wycina mi dziury w jakichś dziwnych miejscach albo dostaję komunikat "No mesh objects found to cut". Co jeszcze może być nie tak? Przecież ustawiam okno prosto przed samolotem.

**Gemini:** Knife Project działa w oparciu o to, co aktualnie widzi Twoja kamera w rzutni. Jeśli patrzysz pod kątem, cięcie będzie krzywe lub nie trafi w obiekt. Musisz przejść do **widoku ortograficznego** (klawisz Numpad 3 dla widoku z boku). Zobacz ten drugi, bardziej szczegółowy filmik, który wyjaśnia błędy z pozycjonowaniem kamery:
* **[YouTube: Why Knife Project is NOT working - Blender Tutorial]**
Upewnij się, że Twój „nóż” jest idealnie przed kadłubem i patrzysz na nich prosto z boku.

**Ja:** Dobra, teraz w końcu załapało! Widok ortograficzny to był brakujący element. Ale teraz pojawił się kolejny problem – jak wyciąłem te otwory, to widać, że samolot jest pusty w środku. Wygląda to słabo. Muszę teraz modelować fotele i całe wnętrze? Nie dam rady tego zrobić, to za dużo roboty.

**Gemini:** Absolutnie nie modeluj środka. Skoro projekt ma być prosty, zrób **okna „na czarno”**. Zamiast wycinać dziury na wylot, po prostu zostaw te wycięte kształty jako część siatki kadłuba, ale przypisz im osobny, czarny materiał z niskim parametrem Roughness (ok. 0.1). To stworzy efekt przyciemnianych szyb i całkowicie ukryje pusty środek.

**Ja:** Genialne w swojej prostocie. Zrobiłem czarny materiał i od razu model wygląda poważniej. Teraz biorę się za turbiny. Szczerze? Nie mam pojęcia, jak zacząć modelować taki silnik, żeby nie był tylko zwykłym klocem. Masz jakieś wideo o modelowaniu turbin z cylindrów?

**Gemini:** Turbinę najlepiej budować modułowo z cylindrów. Zobacz te tutoriale, pomogą Ci zrozumieć workflow:
* **[YouTube: Modeling a simple Jet Engine in Blender]**
Zacznij od jednego cylindra na obudowę, użyj funkcji Inset (I) oraz Extrude (E) do środka, żeby stworzyć wlot. Dzięki temu turbina będzie miała głębię.

**Ja:** Wymodelowałem turbinę, ale mam problem z jej wygładzaniem. Jak włączam „Shade Smooth”, to cały silnik wygląda jak zgnieciona galareta, krawędzie, które powinny być ostre, są rozmyte. Co z tym zrobić?

**Gemini:** To problem z normalnymi. Musisz włączyć funkcję **Auto Smooth**. Wejdź w zakładkę Data Properties (zielony trójkąt), rozwiń sekcję Normals i zaznacz Auto Smooth (ustaw kąt na ok. 30 stopni). To sprawi, że płaskie powierzchnie turbiny zostaną płaskie, a tylko boki będą zaokrąglone.

**Ja:** Super, teraz silnik wygląda jak metalowy. Teraz muszę go skopiować pod drugie skrzydło. Próbowałem to zrobić ręcznie, ale nigdy nie trafiam w to samo miejsce. Jak to zrobić idealnie symetrycznie?

**Gemini:** Użyj modyfikatora **Mirror**. 
1. Wybierz turbinę.
2. Dodaj modyfikator Mirror.
3. W polu „Mirror Object” kliknij pipetę i zaznacz kadłub samolotu jako punkt odniesienia. 
Jeśli turbina wyskoczy w dziwnym miejscu, zaznacz ją i naciśnij **Ctrl + A -> All Transforms**. To zresetuje jej pozycję bazową i Mirror zadziała idealnie.

**Ja:** Spróbowałem, ale ta nowa turbina po drugiej stronie stała się przezroczysta, jakbym patrzył przez nią na wylot. Co się stało?

**Gemini:** To problem z **Normalnymi (Normals)**, które Mirror czasem odwraca „na lewą stronę”. Zaznacz turbinę, wejdź w Edit Mode, zaznacz całą siatkę (klawisz A) i naciśnij **Alt + N -> Recalculate Outside**. To naprawi kierunek ścianek i turbina będzie widoczna poprawnie.

**Ja:** Pomogło! Ostatnia prosta to podwozie. Zrobiłem koła, ale mamy problem z integracją plików. Jak koledzy ruszają samolotem w swoim pliku głównym, to moje podwozie zostaje w punkcie zero. Muszę to wszystko łączyć w jedną siatkę (Join)?

**Gemini:** Nie używaj funkcji Join, bo stracisz kontrolę nad materiałami. Użyj **Parentingu**. Zaznacz wszystkie elementy podwozia i turbiny, na samym końcu zaznacz kadłub i naciśnij **Ctrl + P -> Object**. W ten sposób kadłub zostanie „rodzicem” – jak koledzy przesuną samolot, Twoje detale polecą razem z nim.

**Ja:** W końcu wszystko działa stabilnie. Dzięki za te wszystkie tutoriale i triki z normalnymi i widokiem ortograficznym. Przekazuję finalną wersję chłopakom do renderu!

**Gemini:** Nie używaj Join. Użyj **Parentingu**. Zaznacz podwozie i turbiny, na końcu zaznacz kadłub i naciśnij **Ctrl + P -> Object**. Kadłub zostanie "rodzicem" i wszystkie Twoje części będą latać razem z nim, zachowując swoje materiały.

**Ja:** Dzięki! Wszystko działa i wygląda dokładnie tak, jak chcieliśmy
