---
title: Skróty myszy i klawiaturowe w diagramie klas i oknie szczegółów klasy (Projektant klas) | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3fc21eb85c46d74fabc777147b14575babd9be8b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60113017"
---
# <a name="keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer"></a>Skróty przy użyciu klawiatury i myszy w oknie Diagram klas i Szczegóły klasy (Projektant klas)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można użyć klawiatury, oprócz myszy do wykonania akcji nawigacji w Projektancie klas i w **szczegóły klasy** okna.  
  
 **W tym temacie**  
  
- [Za pomocą myszy w Projektancie klas](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#MouseClassDesigner)  
  
- [Za pomocą myszy w oknie Szczegóły klasy](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#MouseClassDetails)  
  
- [Za pomocą klawiatury w Projektancie klas](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#KeyboardClassDesigner)  
  
- [Za pomocą klawiatury w oknie Szczegóły klasy](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#KeyboardClassDetails)  
  
## <a name="MouseClassDesigner"></a> Za pomocą myszy w Projektancie klas  
 W diagramach są obsługiwane następujące akcje myszy:  
  
|Kombinacja myszy|Kontekst|Opis|  
|-----------------------|-------------|-----------------|  
|Kliknij dwukrotnie plik|elementy kształtu|Zostanie otwarty Edytor kodu.|  
||Łącznik interfejsu typu lizak|Interfejs typu lizak Rozwiń/Zwiń.|  
||Etykieta łącznika interfejsu typu lizak|Wywołuje **pokazać interfejs** polecenia.|  
|Obrót kółkiem myszy|Diagram klas|Przewijanie w pionie.|  
|SHIFT + obrót kółkiem myszy|Diagram klas|Być przewijane w poziomie.|  
|CTRL + obrót kółkiem myszy|Diagram klas|Powiększenia.|  
|CTRL + Shift + kliknięcie|Diagram klas|Powiększenia.|  
  
## <a name="MouseClassDetails"></a> Za pomocą myszy w oknie Szczegóły klasy  
 Za pomocą myszy, możesz zmienić wygląd okna Szczegóły klasy i danych, które są wyświetlane, w następujący sposób:  
  
- Kliknięcie dowolnej komórki edytowalne pozwala edytować zawartość tej komórki. Zmiany są odzwierciedlane we wszystkich miejscach, że dane są przechowywane lub wyświetlane, w tym w oknie dialogowym właściwości i w kodzie źródłowym.  
  
- Kliknij dowolną komórkę wiersza powoduje, że okno właściwości, aby wyświetlić właściwości dla elementu reprezentowanego przez ten wiersz.  
  
- Aby zmienić szerokość kolumny, przeciągnij granicę po prawej stronie nagłówka kolumny kolumna jest szerokość, która ma.  
  
- Można rozwinąć lub Zwiń przedział albo przez węzły, właściwość, klikając symbole strzałkę po lewej stronie wiersza.  
  
- W oknie Szczegóły klasy oferuje kilka przyciski do tworzenia nowych elementów członkowskich w bieżącej klasie i nawigacja pomiędzy przedziały członków w siatce okna Szczegóły klasy. Aby uzyskać więcej informacji zobacz przycisków w oknie Szczegóły klasy.  
  
## <a name="KeyboardClassDesigner"></a> Za pomocą klawiatury w Projektancie klas  
 Obsługiwane są następujące akcje klawiatury w diagramach klas:  
  
|Key|Kontekst|Opis|  
|---------|-------------|-----------------|  
|Klawisze strzałek|Kształty typów do wewnątrz|Styl drzewo nawigacji na zawartość kształtu (otaczania kształt jest obsługiwane). Klawisze lewy i prawy Rozwiń/Zwiń bieżący element przypadku rozwijania i przejdź do elementu nadrzędnego, jeśli nie (zobacz nawigacji w widoku drzewa zachowania szczegółowe).|  
||Kształty najwyższego poziomu|Przenoszenie kształtów na diagramie.|  
|SHIFT + STRZAŁKA kluczy|Kształty typów do wewnątrz|Wybór ciągłe kompilowanie składający się z elementów kształtu, takich jak składniki, zagnieżdżone typy lub przedziały. Te skróty nie obsługują otaczania.|  
|STRONA GŁÓWNA|Kształty typów do wewnątrz|Przejdź do tytułu kształtu najwyższego poziomu.|  
||Kształty najwyższego poziomu|Przejdź do pierwszego kształtu na diagramie.|  
|END|Kształty typów do wewnątrz|Przejdź do ostatniego elementu widoczne wewnątrz kształtu.|  
||Kształty najwyższego poziomu|Przejdź do ostatniego kształtu na diagramie.|  
|SHIFT + HOME|Kształt typu do wewnątrz|Wybiera elementów w obrębie kształtu, począwszy od bieżącego elementu, a kończąc na element najważniejsze na ten sam kształt.|  
|SHIFT + END|Kształt typu do wewnątrz|Wartość taka sama jak SHIFT + HOME, ale w kierunku do góry do dołu.|  
|ENTER|Wszystkie konteksty|Wywołuje akcję domyślną dla kształtu, która jest również dostępna za pośrednictwem kliknij dwukrotnie plik. W większości przypadków jest to widok kodu, ale niektóre elementy Definiuj inaczej (lizaki, nagłówki przedziału, etykiet interfejsów typu lizak).|  
|+/-|Wszystkie konteksty|W przypadku rozwijania elementem mającym aktualnie fokus te klucze Rozwiń/Zwiń element.|  
|>|Wszystkie konteksty|W przypadku elementów z elementami podrzędnymi rozszerza element jest zwinięte i przechodzi do pierwszego elementu podrzędnego.|  
|<|Wszystkie konteksty|Powoduje przejście do elementu nadrzędnego.|  
|ALT+SHIFT+L|Wewnątrz kształtów typu + kształtów typu.|Powoduje przejście do interfejsu typu lizak aktualnie wybranego kształtu, jeśli jest obecny.|  
|ALT+SHIFT+B|Wewnątrz kształtów typu + kształtów typu.|Jeśli listę typów podstawowych są wyświetlane na kształt typu i ma więcej niż jeden element, przełącza tego stanu rozszerzenia listy (Zwiń/Rozwiń).|  
|DELETE|Typ i komentarz kształtów|Wywołuje **Usuń z diagramu** polecenia.|  
||Na całą resztą.|Wywołuje **usuwanie kodu** polecenia (elementy członkowskie, parametrów, asocjacje, dziedziczenie, etykiet interfejsów typu lizak).|  
|CTRL+DELETE|Wszystkie konteksty|Wywołuje **usuwanie kodu** na wybór polecenia.|  
|TAB|Wszystkie konteksty|Powoduje przejście do następnego elementu podrzędnego w obrębie tego samego nadrzędnego (obsługuje zawijania).|  
|SHIFT+TAB|Wszystkie konteksty|Powoduje przejście do poprzedniego elementu podrzędnego w obrębie tego samego nadrzędnego (obsługuje zawijania).|  
|SPACE|Wszystkie konteksty|Włącza lub wyłącza zaznaczenie dla bieżącego elementu.|  
  
## <a name="KeyboardClassDetails"></a> Za pomocą klawiatury w oknie Szczegóły klasy  
  
> [!NOTE]
>  Następujących klawiszy dobrano w celu specjalnie, aby używane środowisko przypominało środowisko pisania kodu.  
  
 Przejdź w oknie Szczegóły klasy za pomocą następujących klawiszy:  
  
|||  
|-|-|  
|Key|Wynik|  
|, (przecinkami)|Jeśli kursor znajduje się w wierszu parametru, wpisując z przecinkiem na końcu przenosi kursor do pola nazwy parametru dalej. Jeśli kursor znajduje się w ostatnim wierszu parametru metody, przenosi kursor do \<Dodaj parametr > pola, które można użyć do utworzenia nowego parametru.<br /><br /> Jeśli kursor znajduje się gdzie indziej w oknie Szczegóły klasy, wpisując z przecinkiem na końcu dosłownie dodaje przecinek bieżącego pola.|  
|; (średnik)<br /><br /> lub<br /><br /> ) (nawiasu zamykającego)|Przenieś kursor do pola nazwy następny wiersz elementu członkowskiego w siatce okna Szczegóły klasy.|  
|Tab|Przenosi kursor do następnego pola, najpierw przejście od lewej do prawej, a następnie z góry na dół. Jeśli kursor jest przenoszona z polem, w jakiej został wpisany tekst, okno Szczegóły klasy przetwarza ten tekst i zapisuje go, jeśli nie generuje błąd.<br /><br /> Jeśli kursor znajduje się na puste pole takie jak \<Dodaj parametr >, kartę przenosi je do pierwszego pola następnego wiersza.|  
|\<space>|Przenosi kursor do następnego pola, najpierw przejście od lewej do prawej, a następnie z góry na dół. Jeśli kursor znajduje się na puste pole takie jak \<Dodaj parametr >, przenosi do pierwszego pola następnego wiersza. Należy pamiętać, że \<miejsca > wpisane natychmiast, po przecinek jest ignorowana.<br /><br /> Jeśli kursor znajduje się w polu Podsumowanie, miejsce na wpisanie dodaje znak spacji.<br /><br /> Jeśli kursor znajduje się w kolumnie Ukryj w danym wierszu, miejsce na wpisanie przełącza wartość Ukryj pola wyboru.|  
|CTRL+Tab|Przełącz do innego okna dokumentu. Na przykład przełączyć okna Szczegóły klasy można otworzyć pliku kodu.|  
|ESC (ucieczki)|Jeśli rozpoczęto wpisać tekst w polu, naciskając klawisz ESC działa jako klawiszem Cofnij przywrócenie zawartości tego pola do poprzedniej wartości. Jeśli okno Szczegóły klasy zawiera ogólne fokus, ale nie określona komórka jest ustawiony fokus, naciskając klawisz ESC powoduje przeniesienie fokusu poza okna Szczegóły klasy.|  
|Strzałka w górę i Strzałka w dół|Te klucze Przesuń kursor wiersz po wierszu w pionie w siatce okna Szczegóły klasy.|  
|Strzałka w lewo|Jeśli kursor znajduje się w kolumnie Nazwa, naciskając klawisz Strzałka w lewo Zwija bieżący węzeł w hierarchii (jeśli jest otwarty).|  
|Strzałka w prawo|Jeśli kursor znajduje się w kolumnie Nazwa, naciskając klawisz Strzałka w prawo rozwija bieżący węzeł w hierarchii (jeśli jest zwinięte).|  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie i konfigurowanie składowych typu (Projektant klas)](../ide/creating-and-configuring-type-members-class-designer.md)
