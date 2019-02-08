---
title: Skróty myszy i klawiaturowe w Projektancie klas
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.classdetails.window
helpviewer_keywords:
- class diagrams, keyboard shortcuts
- class diagrams, mouse shortcuts
ms.assetid: c12d8dac-9902-4fde-b721-2a8116da53b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a867986f26037473f5a45341f8d454b560c586ff
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55951933"
---
# <a name="keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window"></a>Skróty myszy i klawiatury w oknie Diagram klas i szczegóły klasy

Można użyć klawiatury, oprócz myszy do wykonania akcji nawigacji w **projektanta klas** i **szczegóły klasy** okna.

## <a name="use-the-mouse-in-class-designer"></a>Za pomocą myszy w Projektancie klas

W diagramach są obsługiwane następujące akcje myszy:

|Kombinacja myszy|Kontekst|Opis|
| - |-------------|-----------------|
|Kliknij dwukrotnie plik|elementy kształtu|Zostanie otwarty Edytor kodu.|
|Kliknij dwukrotnie plik|Łącznik interfejsu typu lizak|Interfejs typu lizak Rozwiń/Zwiń.|
|Kliknij dwukrotnie plik|Etykieta łącznika interfejsu typu lizak|Wywołuje **pokazać interfejs** polecenia.|
|Obrót kółkiem myszy|Diagram klas|Przewijanie w pionie.|
|**SHIFT** + kółko myszy|Diagram klas|Być przewijane w poziomie.|
|**CTRL** + kółko myszy|Diagram klas|Powiększenia.|
|**CTRL**+**Shift** + kliknięcie|Diagram klas|Powiększenia.|

## <a name="use-the-mouse-in-the-class-details-window"></a>Za pomocą myszy w oknie Szczegóły klasy

Za pomocą myszy, można zmienić wygląd **szczegóły klasy** okna i danych wyświetlanych w następujący sposób:

- Kliknięcie dowolnej komórki edytowalne pozwala edytować zawartość tej komórki. Zmiany są odzwierciedlane we wszystkich miejscach, że dane są przechowywane lub wyświetlana, tym **właściwości** okna w kodzie źródłowym.

- Kliknij dowolną komórkę wiersza powoduje, że **właściwości** okno, aby wyświetlić właściwości dla elementu reprezentowanego przez ten wiersz.

- Aby zmienić szerokość kolumny, przeciągnij granicę po prawej stronie nagłówka kolumny kolumna jest szerokość, która ma.

- Można rozwinąć lub Zwiń przedział albo przez węzły, właściwość, klikając symbole strzałkę po lewej stronie wiersza.

- **Szczegóły klasy** okna oferuje kilka przyciski do tworzenia nowych elementów członkowskich w bieżącej klasie i nawigacja pomiędzy przedziały członków w **szczegóły klasy** siatki okna.

## <a name="use-the-keyboard-in-class-designer"></a>Używanie klawiatury w Projektancie klas

Obsługiwane są następujące akcje klawiatury w diagramach klas:

|Key|Kontekst|Opis|
|---------|-------------|-----------------|
|**Klawisze strzałek**|Kształty typów do wewnątrz|Styl drzewo nawigacji na zawartość kształtu (otaczania kształt jest obsługiwane). Klawisze lewy i prawy Rozwiń/Zwiń bieżący element przypadku rozwijania i przejdź do elementu nadrzędnego, jeśli nie (zobacz nawigacji w widoku drzewa zachowania szczegółowe).|
|**Klawisze strzałek**|Kształty najwyższego poziomu|Przenoszenie kształtów na diagramie.|
|**SHIFT**+**klawisze strzałek**|Kształty typów do wewnątrz|Wybór ciągłe kompilowanie składający się z elementów kształtu, takich jak składniki, zagnieżdżone typy lub przedziały. Te skróty nie obsługują otaczania.|
|**Strona główna**|Kształty typów do wewnątrz|Przejdź do tytułu kształtu najwyższego poziomu.|
|**Strona główna**|Kształty najwyższego poziomu|Przejdź do pierwszego kształtu na diagramie.|
|**End**|Kształty typów do wewnątrz|Przejdź do ostatniego elementu widoczne wewnątrz kształtu.|
|**End**|Kształty najwyższego poziomu|Przejdź do ostatniego kształtu na diagramie.|
|**SHIFT**+**strona główna**|Kształt typu do wewnątrz|Wybiera elementów w obrębie kształtu, począwszy od bieżącego elementu, a kończąc na element najważniejsze na ten sam kształt.|
|**SHIFT**+**zakończenia**|Kształt typu do wewnątrz|Taki sam jak **Shift**+**Home** , ale w kierunku do góry do dołu.|
|**Wprowadź**|Wszystkie konteksty|Wywołuje akcję domyślną dla kształtu, która jest również dostępna za pośrednictwem kliknij dwukrotnie plik. W większości przypadków jest to widok kodu, ale niektóre elementy Definiuj inaczej (lizaki, nagłówki przedziału, etykiet interfejsów typu lizak).|
|**+** i **-**|Wszystkie konteksty|W przypadku rozwijania elementem mającym aktualnie fokus te klucze rozwiń lub Zwiń element.|
|**>**|Wszystkie konteksty|W przypadku elementów z elementami podrzędnymi rozszerza element jest zwinięte i przechodzi do pierwszego elementu podrzędnego.|
|**<**|Wszystkie konteksty|Powoduje przejście do elementu nadrzędnego.|
|**ALT**+**Shift**+**L**|Wewnątrz kształtów typu + kształtów typu.|Powoduje przejście do interfejsu typu lizak aktualnie wybranego kształtu, jeśli jest obecny.|
|**ALT**+**Shift**+**B**|Wewnątrz kształtów typu + kształtów typu.|Jeśli listę typów podstawowych są wyświetlane na kształt typu i ma więcej niż jeden element, przełącza tego stanu rozszerzenia listy (Zwiń/Rozwiń).|
|**Delete**|Typ i komentarz kształtów|Wywołuje **Usuń z diagramu** polecenia.|
|**Delete**|Na całą resztą.|Wywołuje **usuwanie kodu** polecenia (elementy członkowskie, parametrów, asocjacje, dziedziczenie, etykiet interfejsów typu lizak).|
|**Ctrl**+**Delete**|Wszystkie konteksty|Wywołuje **usuwanie kodu** na wybór polecenia.|
|**Karta**|Wszystkie konteksty|Powoduje przejście do następnego elementu podrzędnego w obrębie tego samego nadrzędnego (obsługuje zawijania).|
|**SHIFT**+**kartę**|Wszystkie konteksty|Powoduje przejście do poprzedniego elementu podrzędnego w obrębie tego samego nadrzędnego (obsługuje zawijania).|
|**SPACJA**|Wszystkie konteksty|Włącza lub wyłącza zaznaczenie dla bieżącego elementu.|

## <a name="use-the-keyboard-in-the-class-details-window"></a>Używanie klawiatury w oknie Szczegóły klasy

> [!NOTE]
> Następujących klawiszy dobrano w celu specjalnie, aby używane środowisko przypominało środowisko pisania kodu.

Aby przejść za pomocą następujących klawiszy **szczegóły klasy** okna:

|||
|-|-|
|Key|Wynik|
|**,** (przecinek)|Jeśli kursor znajduje się w wierszu parametru, wpisując z przecinkiem na końcu przenosi kursor do pola nazwy parametru dalej. Jeśli kursor znajduje się w ostatnim wierszu parametru metody, przenosi kursor do \<Dodaj parametr > pola, które można użyć do utworzenia nowego parametru.<br /><br /> Jeśli kursor znajduje się gdzie indziej w **szczegóły klasy** okna, wpisując z przecinkiem na końcu dosłownie dodaje przecinek w bieżącej wartości pola.|
|**;**  (średnik) lub **)** (zamykający nawias)|Przesuń kursor do pola nazwy następny wiersz elementu członkowskiego w **szczegóły klasy** siatki okna.|
|**Karta**|Przenosi kursor do następnego pola, najpierw przejście od lewej do prawej, a następnie z góry na dół. Jeśli kursor jest przenoszona z polem, w jakiej został wpisany tekst, **szczegóły klasy** przetwarza ten tekst i zapisuje go, jeśli nie generuje błąd.<br /><br /> Jeśli kursor znajduje się na puste pole takie jak \<Dodaj parametr >, kartę przenosi je do pierwszego pola następnego wiersza.|
|**SPACJA**|Przenosi kursor do następnego pola, najpierw przejście od lewej do prawej, a następnie z góry na dół. Jeśli kursor znajduje się na puste pole takie jak \<Dodaj parametr >, przenosi do pierwszego pola następnego wiersza. Należy pamiętać, że \<miejsca > wpisane natychmiast, po przecinek jest ignorowana.<br /><br /> Jeśli kursor znajduje się w polu Podsumowanie, miejsce na wpisanie dodaje znak spacji.<br /><br /> Jeśli kursor znajduje się w kolumnie Ukryj w danym wierszu, miejsce na wpisanie przełącza wartość Ukryj pola wyboru.|
|**Ctrl**+**Tab**|Przełącz do innego okna dokumentu. Na przykład zmienić **szczegóły klasy** okna można otworzyć pliku kodu.|
|**ESC**|Jeśli rozpoczęto wpisać tekst w polu, naciskając klawisz ESC działa jako klawiszem Cofnij przywrócenie zawartości tego pola do poprzedniej wartości. Jeśli okno Szczegóły klasy zawiera ogólne fokus, ale nie określona komórka jest ustawiony fokus, naciskając klawisz ESC powoduje przeniesienie fokusu opuszczenie **szczegóły klasy** okna.|
|**Strzałka w górę** i **Strzałka w dół**|Te klucze Przesuń kursor wiersz po wierszu w pionie w **szczegóły klasy** siatki okna.|
|**Strzałka w lewo**|Jeśli kursor znajduje się w kolumnie Nazwa, naciskając klawisz Strzałka w lewo Zwija bieżący węzeł w hierarchii (jeśli jest otwarty).|
|**Strzałka w prawo**|Jeśli kursor znajduje się w kolumnie Nazwa, naciskając klawisz Strzałka w prawo rozwija bieżący węzeł w hierarchii (jeśli jest zwinięte).|

## <a name="see-also"></a>Zobacz także

- [Tworzenie i konfigurowanie składowych typów](creating-and-configuring-type-members.md)