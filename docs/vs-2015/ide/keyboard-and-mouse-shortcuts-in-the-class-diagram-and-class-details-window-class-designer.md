---
title: Skróty klawiaturowe i myszy na diagramie klas i Okno szczegółów klasy (Projektant klas) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdetails.window
helpviewer_keywords:
- class diagrams, keyboard shortcuts
- class diagrams, mouse shortcuts
ms.assetid: c12d8dac-9902-4fde-b721-2a8116da53b7
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5865059e60907397ae7d69b230676ac63a5c3386
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543120"
---
# <a name="keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer"></a>Skróty przy użyciu klawiatury i myszy w oknie Diagram klas i Szczegóły klasy (Projektant klas)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz użyć klawiatury oprócz myszy do wykonywania akcji nawigacyjnych w Projektant klas i w oknie **Szczegóły klasy** .

 **W tym temacie**

- [Używanie myszy w Projektant klas](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#MouseClassDesigner)

- [Używanie myszy w Okno szczegółów klasy](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#MouseClassDetails)

- [Używanie klawiatury w Projektant klas](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#KeyboardClassDesigner)

- [Używanie klawiatury w Okno szczegółów klasy](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#KeyboardClassDetails)

## <a name="using-the-mouse-in-class-designer"></a><a name="MouseClassDesigner"></a> Używanie myszy w Projektant klas
 Następujące akcje myszy są obsługiwane na diagramach klas:

|Kombinacja myszy|Kontekst|Opis|
|-----------------------|-------------|-----------------|
|Kliknij dwukrotnie|elementy kształtu|Otwiera edytor kodu.|
||Łącznik typu lizak|Rozwiń/Zwiń lizak.|
||Etykieta łącznika lizaka|Wywołuje polecenie **show interface** .|
|Kółko myszy|Diagram klas|Przewiń w pionie.|
|SHIFT + kółko myszy|Diagram klas|Przewiń w poziomie.|
|CTRL + kółko myszy|Diagram klas|Zmieniać.|
|CTRL + SHIFT + kliknięcie|Diagram klas|Zmieniać.|

## <a name="using-the-mouse-in-the-class-details-window"></a><a name="MouseClassDetails"></a> Używanie myszy w Okno szczegółów klasy
 Za pomocą myszy można zmienić wygląd okna Szczegóły klasy i wyświetlane dane w następujący sposób:

- Kliknięcie dowolnej edytowalnej komórki umożliwia edytowanie zawartości tej komórki. Zmiany są odzwierciedlone we wszystkich miejscach, w których dane są przechowywane lub wyświetlane, w tym w okno Właściwości i w kodzie źródłowym.

- Kliknięcie dowolnej komórki w wierszu powoduje, że okno Właściwości wyświetlić właściwości elementu reprezentowanego przez ten wiersz.

- Aby zmienić szerokość kolumny, przeciągnij granicę po prawej stronie nagłówka kolumny do momentu, gdy kolumna będzie mieć żądaną szerokość.

- Można rozwinąć lub zwinąć przedział lub węzły właściwości, klikając symbole strzałek na lewo od wiersza.

- Okno szczegółów klasy oferuje kilka przycisków do tworzenia nowych elementów członkowskich w bieżącej klasie i nawigowania między przedziałami elementów członkowskich w siatce Okno szczegółów klasy. Aby uzyskać więcej informacji, zobacz przyciski Okno szczegółów klasy.

## <a name="using-the-keyboard-in-class-designer"></a><a name="KeyboardClassDesigner"></a> Używanie klawiatury w Projektant klas
 Następujące akcje klawiatury są obsługiwane na diagramach klas:

|Klucz|Kontekst|Opis|
|---------|-------------|-----------------|
|Klawisze strzałek|Wewnątrz kształtów typu|Nawigacja w stylu drzewa w zawartości kształtu (obsługiwane jest Zawijanie wokół kształtu). Lewe i prawe klawisze rozszerzają/zwijają bieżący element, jeśli są rozwijane i przechodź do elementu nadrzędnego (jeśli nie) (zobacz Nawigowanie w widoku drzewa, aby uzyskać szczegółowe zachowanie).|
||Kształty najwyższego poziomu|Przesuwanie kształtów na diagramie.|
|SHIFT + klawisze strzałek|Wewnątrz kształtów typu|Tworzenie ciągłego wyboru składającego się z elementów Shape, takich jak elementy członkowskie, zagnieżdżone typy lub przedziały. Skróty te nie obsługują zawijania.|
|STRONA GŁÓWNA|Wewnątrz kształtów typu|Przejdź do tytułu kształtu najwyższego poziomu.|
||Kształty najwyższego poziomu|Przejdź do pierwszego kształtu na diagramie.|
|END|Wewnątrz kształtów typu|Przejdź do ostatniego widocznego elementu wewnątrz kształtu.|
||Kształty najwyższego poziomu|Przejdź do ostatniego kształtu na diagramie.|
|SHIFT + HOME|Wewnątrz kształtu typu|Wybiera elementy w obrębie kształtu, rozpoczynając od bieżącego elementu i kończąc na najwyższego poziomu w tym samym kształcie.|
|SHIFT + END|Wewnątrz kształtu typu|Analogicznie jak SHIFT + HOME, ale w kierunku do góry.|
|ENTER|Wszystkie konteksty|Wywołuje akcję domyślną na kształcie, który jest również dostępny przez dwukrotne kliknięcie. W większości przypadków jest to widok kod, ale niektóre elementy definiują go inaczej (lizaki, nagłówki przedziałów, etykiety lizaków).|
|+/-|Wszystkie konteksty|Jeśli aktualnie fokus jest rozwijalny, te klucze rozszerzają/zwijają elementy.|
|>|Wszystkie konteksty|W przypadku elementów z elementami podrzędnymi rozszerza on element, jeśli jest zwinięty i przechodzi do pierwszego elementu podrzędnego.|
|<|Wszystkie konteksty|Powoduje przejście do elementu nadrzędnego.|
|ALT + SHIFT + L|Wewnątrz typu Shapes + on Type Shapes.|Przechodzi do lizaka aktualnie zaznaczonego kształtu, jeśli jest obecny.|
|ALT + SHIFT + B|Wewnątrz typu Shapes + on Type Shapes.|Jeśli lista typ podstawowy jest pokazywana w kształcie typu i ma więcej niż jeden element, spowoduje to przełączenie stanu rozszerzenia listy (Zwiń/rozwiń).|
|DELETE|Na kształtach typu i komentarza|Wywołuje polecenie **Usuń z diagramu** .|
||Na wszystkich innych.|Wywołuje polecenie **Delete from Code** (elementy członkowskie, parametry, skojarzenia, dziedziczenie, etykiety lizaka).|
|CTRL + DELETE|Wszystkie konteksty|Wywołuje polecenie **usunięcia z kodu** przy wyborze.|
|TAB|Wszystkie konteksty|Przechodzi do następnego elementu podrzędnego w obrębie tego samego elementu nadrzędnego (obsługuje Zawijanie).|
|SHIFT+TAB|Wszystkie konteksty|Przechodzi do poprzedniego elementu podrzędnego w obrębie tego samego elementu nadrzędnego (obsługuje Zawijanie).|
|ODSTĘP|Wszystkie konteksty|Przełącza zaznaczenie bieżącego elementu.|

## <a name="using-the-keyboard-in-the-class-details-window"></a><a name="KeyboardClassDetails"></a> Używanie klawiatury w Okno szczegółów klasy

> [!NOTE]
> Następujące kluczowe powiązania zostały wybrane do naśladowania środowiska wpisywania kodu.

 Użyj następujących klawiszy, aby przejść do okna Szczegóły klasy:

|Klucz|Wynik|
|-|-|
|, (przecinek)|Jeśli kursor znajduje się w wierszu parametru, wpisanie przecinka przenosi kursor do pola Nazwa następnego parametru. Jeśli kursor znajduje się w ostatnim wierszu parametru metody, przenosi kursor do \<add parameter> pola, którego można użyć do utworzenia nowego parametru.<br /><br /> Jeśli kursor znajduje się w innym miejscu Okno szczegółów klasy, wpisanie przecinka powoduje dodanie przecinka w bieżącym polu.|
|; Dziel<br /><br /> lub<br /><br /> ) (nawias zamykający)|Przenieś kursor do pola Nazwa następnego wiersza elementu członkowskiego w siatce Okno szczegółów klasy.|
|Tab|Przenosi kursor do następnego pola, najpierw przesuwając od lewej do prawej i od góry do dołu. Jeśli kursor jest przenoszony z pola, w którym wpisano tekst, Okno szczegółów klasy przetwarza ten tekst i zapisuje go, jeśli nie wygenerował błędu.<br /><br /> Jeśli kursor znajduje się w pustym polu, takim jak \<add parameter> , karta przenosi ją do pierwszego pola następnego wiersza.|
|\<space>|Przenosi kursor do następnego pola, najpierw przesuwając od lewej do prawej i od góry do dołu. Jeśli kursor znajduje się w pustym polu, takim jak \<add parameter> , przenosi do pierwszego pola następnego wiersza. Należy zauważyć, że \<space> wpisane bezpośrednio po przecinku jest ignorowane.<br /><br /> Jeśli kursor znajduje się w polu podsumowania, wpisanie spacji powoduje dodanie znaku spacji.<br /><br /> Jeśli kursor znajduje się w kolumnie Ukryj w danym wierszu, wpisanie spacji powoduje przełączenie wartości pola wyboru Ukryj.|
|CTRL + TAB|Przejdź do okna innego dokumentu. Na przykład Przełącz się z Okno szczegółów klasy do pliku Open Code.|
|ESC (Escape)|Jeśli rozpoczęto wpisywanie tekstu w polu, naciśnięcie klawisza ESC działa jako klawisz cofania, przywraca zawartość pola do poprzedniej wartości. Jeśli Okno szczegółów klasy ma ogólny fokus, ale żadna konkretna komórka nie ma fokusu, naciśnięcie klawisza ESC przenosi fokus z Okno szczegółów klasy.|
|Strzałka w górę i Strzałka w dół|Te klucze umożliwiają przeniesienie kursora z wiersza do wiersza w pionie w siatce Okno szczegółów klasy.|
|Strzałka w lewo|Jeśli kursor znajduje się w kolumnie Nazwa, naciśnięcie strzałki w lewo zwija bieżący węzeł w hierarchii (jeśli jest otwarty).|
|Strzałka w prawo|Jeśli kursor znajduje się w kolumnie Nazwa, naciśnięcie strzałki w prawo rozszerza bieżący węzeł w hierarchii (jeśli jest zwinięty).|

## <a name="see-also"></a>Zobacz też
 [Tworzenie i konfigurowanie typów członków (Projektant klas)](../ide/creating-and-configuring-type-members-class-designer.md)
