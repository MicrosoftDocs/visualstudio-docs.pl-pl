---
title: Skróty klawiaturowe i myszy dla Projektant klas
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.classdetails.window
helpviewer_keywords:
- class diagrams, keyboard shortcuts
- class diagrams, mouse shortcuts
ms.assetid: c12d8dac-9902-4fde-b721-2a8116da53b7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30932a6c94bc6104aeea0244f06f471d0a639b21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533669"
---
# <a name="keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window"></a>Skróty klawiaturowe i myszy w diagramie klas i oknie Szczegóły klasy

Możesz użyć klawiatury oprócz myszy do wykonywania akcji nawigacyjnych w **Projektant klas** i w oknie **Szczegóły klasy** .

## <a name="use-the-mouse-in-class-designer"></a>Używanie myszy w Projektant klas

Następujące akcje myszy są obsługiwane na diagramach klas:

|Kombinacja myszy|Kontekst|Opis|
| - |-------------|-----------------|
|Kliknij dwukrotnie|elementy kształtu|Otwiera edytor kodu.|
|Kliknij dwukrotnie|Łącznik typu lizak|Rozwiń/Zwiń lizak.|
|Kliknij dwukrotnie|Etykieta łącznika lizaka|Wywołuje polecenie **show interface** .|
|Kółko myszy|Diagram klas|Przewiń w pionie.|
|**SHIFT** + kółko myszy|Diagram klas|Przewiń w poziomie.|
|**Ctrl** + kółko myszy|Diagram klas|Zmieniać.|
|**Ctrl** + **SHIFT** + kliknięcie|Diagram klas|Zmieniać.|

## <a name="use-the-mouse-in-the-class-details-window"></a>Używanie myszy w oknie Szczegóły klasy

Za pomocą myszy można zmienić wygląd okna **Szczegóły klasy** oraz dane, które są wyświetlane w następujący sposób:

- Kliknięcie dowolnej edytowalnej komórki umożliwia edytowanie zawartości tej komórki. Zmiany zostaną odzwierciedlone we wszystkich miejscach, w których dane są przechowywane lub wyświetlane, w tym w oknie **Właściwości** i w kodzie źródłowym.

- Kliknięcie dowolnej komórki wiersza powoduje, że okno **Właściwości** wyświetla właściwości elementu reprezentowanego przez ten wiersz.

- Aby zmienić szerokość kolumny, przeciągnij granicę po prawej stronie nagłówka kolumny do momentu, gdy kolumna będzie mieć żądaną szerokość.

- Można rozwinąć lub zwinąć przedział lub węzły właściwości, klikając symbole strzałek na lewo od wiersza.

- Okno **Szczegóły klasy** zawiera kilka przycisków służących do tworzenia nowych elementów członkowskich w bieżącej klasie i nawigowania między przedziałami elementów członkowskich w siatce okna **Szczegóły klasy** .

## <a name="use-the-keyboard-in-class-designer"></a>Używanie klawiatury w Projektant klas

Następujące akcje klawiatury są obsługiwane na diagramach klas:

|Klucz|Kontekst|Opis|
|---------|-------------|-----------------|
|**Klawisze strzałek**|Wewnątrz kształtów typu|Nawigacja w stylu drzewa w zawartości kształtu (obsługiwane jest Zawijanie wokół kształtu). Lewe i prawe klawisze rozszerzają/zwijają bieżący element, jeśli są rozwijane i przechodź do elementu nadrzędnego (jeśli nie) (zobacz Nawigowanie w widoku drzewa, aby uzyskać szczegółowe zachowanie).|
|**Klawisze strzałek**|Kształty najwyższego poziomu|Przesuwanie kształtów na diagramie.|
|**SHIFT** + **klawisze strzałek**|Wewnątrz kształtów typu|Tworzenie ciągłego wyboru składającego się z elementów Shape, takich jak elementy członkowskie, zagnieżdżone typy lub przedziały. Skróty te nie obsługują zawijania.|
|**Strona główna**|Wewnątrz kształtów typu|Przejdź do tytułu kształtu najwyższego poziomu.|
|**Strona główna**|Kształty najwyższego poziomu|Przejdź do pierwszego kształtu na diagramie.|
|**Punktów**|Wewnątrz kształtów typu|Przejdź do ostatniego widocznego elementu wewnątrz kształtu.|
|**Punktów**|Kształty najwyższego poziomu|Przejdź do ostatniego kształtu na diagramie.|
|**SHIFT** + **Strona główna**|Wewnątrz kształtu typu|Wybiera elementy w obrębie kształtu, rozpoczynając od bieżącego elementu i kończąc na najwyższego poziomu w tym samym kształcie.|
|**SHIFT** + **Koniec**|Wewnątrz kształtu typu|Analogicznie **Shift**jak + **Strona główna** przesunięcia, ale w kierunku do góry.|
|**Wejść**|Wszystkie konteksty|Wywołuje akcję domyślną na kształcie, który jest również dostępny przez dwukrotne kliknięcie. W większości przypadków jest to widok kod, ale niektóre elementy definiują go inaczej (lizaki, nagłówki przedziałów, etykiety lizaków).|
|**+** lub **-**|Wszystkie konteksty|Jeśli aktualnie fokus jest rozwijalny, te klucze rozszerzają lub zwijają elementy.|
|**>**|Wszystkie konteksty|W przypadku elementów z elementami podrzędnymi rozszerza on element, jeśli jest zwinięty i przechodzi do pierwszego elementu podrzędnego.|
|**<**|Wszystkie konteksty|Powoduje przejście do elementu nadrzędnego.|
|**Alt** + **SHIFT** + **L**|Wewnątrz typu Shapes + on Type Shapes.|Przechodzi do lizaka aktualnie zaznaczonego kształtu, jeśli jest obecny.|
|**Alt** + **SHIFT** + **B**|Wewnątrz typu Shapes + on Type Shapes.|Jeśli lista typ podstawowy jest pokazywana w kształcie typu i ma więcej niż jeden element, spowoduje to przełączenie stanu rozszerzenia listy (Zwiń/rozwiń).|
|**Usuń**|Na kształtach typu i komentarza|Wywołuje polecenie **Usuń z diagramu** .|
|**Usuń**|Na wszystkich innych.|Wywołuje polecenie **Delete from Code** (elementy członkowskie, parametry, skojarzenia, dziedziczenie, etykiety lizaka).|
|**Ctrl** + **Usuń**|Wszystkie konteksty|Wywołuje polecenie **usunięcia z kodu** przy wyborze.|
|**Tabulator**|Wszystkie konteksty|Przechodzi do następnego elementu podrzędnego w obrębie tego samego elementu nadrzędnego (obsługuje Zawijanie).|
|**SHIFT** + **Karta**|Wszystkie konteksty|Przechodzi do poprzedniego elementu podrzędnego w obrębie tego samego elementu nadrzędnego (obsługuje Zawijanie).|
|**Spacja**|Wszystkie konteksty|Przełącza zaznaczenie bieżącego elementu.|

## <a name="use-the-keyboard-in-the-class-details-window"></a>Korzystanie z klawiatury w oknie Szczegóły klasy

> [!NOTE]
> Następujące kluczowe powiązania zostały wybrane do naśladowania środowiska wpisywania kodu.

Użyj następujących klawiszy, aby przejść do okna **Szczegóły klasy** :

|Klucz|Wynik|
|-|-|
|**,** (przecinek)|Jeśli kursor znajduje się w wierszu parametru, wpisanie przecinka przenosi kursor do pola Nazwa następnego parametru. Jeśli kursor znajduje się w ostatnim wierszu parametru metody, przenosi kursor do \<add parameter> pola, którego można użyć do utworzenia nowego parametru.<br /><br /> Jeśli kursor znajduje się w innym miejscu w oknie **Szczegóły klasy** , wpisanie przecinka powoduje dodanie przecinka w bieżącym polu.|
|**;** (średnik) lub **)** (nawias zamykający)|Przenieś kursor do pola Nazwa następnego wiersza elementu członkowskiego w siatce okna **Szczegóły klasy** .|
|**Tabulator**|Przenosi kursor do następnego pola, najpierw przesuwając od lewej do prawej i od góry do dołu. Jeśli kursor jest przenoszony z pola, w którym wpisano tekst, **Szczegóły klasy** przetwarzają ten tekst i zapisuje je, jeśli nie wygenerowały błędu.<br /><br /> Jeśli kursor znajduje się w pustym polu, takim jak \<add parameter> , karta przenosi ją do pierwszego pola następnego wiersza.|
|**Spacja**|Przenosi kursor do następnego pola, najpierw przesuwając od lewej do prawej i od góry do dołu. Jeśli kursor znajduje się w pustym polu, takim jak \<add parameter> , przenosi do pierwszego pola następnego wiersza. Należy zauważyć, że \<space> wpisane bezpośrednio po przecinku jest ignorowane.<br /><br /> Jeśli kursor znajduje się w polu podsumowania, wpisanie spacji powoduje dodanie znaku spacji.<br /><br /> Jeśli kursor znajduje się w kolumnie Ukryj w danym wierszu, wpisanie spacji powoduje przełączenie wartości pola wyboru Ukryj.|
|**Ctrl** + **Karta**|Przejdź do okna innego dokumentu. Na przykład Przełącz się z okna **Szczegóły klasy** do pliku Open Code.|
|**Esc**|Jeśli rozpoczęto wpisywanie tekstu w polu, naciśnięcie klawisza ESC działa jako klawisz cofania, przywraca zawartość pola do poprzedniej wartości. Jeśli Okno szczegółów klasy ma ogólny fokus, ale żadna określona komórka nie ma fokusu, naciśnięcie klawisza ESC przenosi fokus z okna **Szczegóły klasy** .|
|**Strzałka w górę** i **Strzałka w dół**|Te klucze umożliwiają przeniesienie kursora z wiersza do wiersza w pionie w siatce okna **Szczegóły klasy** .|
|**Strzałka w lewo**|Jeśli kursor znajduje się w kolumnie Nazwa, naciśnięcie strzałki w lewo zwija bieżący węzeł w hierarchii (jeśli jest otwarty).|
|**Strzałka w prawo**|Jeśli kursor znajduje się w kolumnie Nazwa, naciśnięcie strzałki w prawo rozszerza bieżący węzeł w hierarchii (jeśli jest zwinięty).|

## <a name="see-also"></a>Zobacz też

- [Tworzenie i konfigurowanie składowych typów](creating-and-configuring-type-members.md)
- [Korzystanie wyłącznie z klawiatury](../reference/how-to-use-the-keyboard-exclusively.md)
- [Domyślne skróty klawiaturowe w programie Visual Studio](../default-keyboard-shortcuts-in-visual-studio.md)
- [Skróty klawiaturowe w programie Blend](../../xaml-tools/keyboard-shortcuts-in-blend.md)
