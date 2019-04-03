---
title: Refaktoryzacja kodu
description: Rafinacja kodu za pomocą programu Visual Studio dla komputerów Mac i szybkie akcje.
author: conceptdev
ms.author: crdun
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 48e290fddd1c4b7c95ac5e76cb6cf5908247e6f6
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58856518"
---
# <a name="refactoring"></a>Refaktoryzacja

Refaktoryzacja kodu jest sposobem rozmieszczanie, restrukturyzacji i wyjaśnienia istniejącego kodu przy jednoczesnym zapewnieniu, która nie zmienia się ogólnym zachowaniom kodu.

Refaktoryzacja zapewnia lepszy wynik dotyczący bazy kodu, dzięki czemu bardziej użyteczny, czytelny i łatwego w utrzymaniu dla możesz żadnych innych deweloperów lub użytkownika, którego może odnosić się do kodu.

Program Visual Studio dla komputerów Mac integracji dzięki użyciu platformy Roslyn, platforma kompilatora .NET typu open source firmy Microsoft, pozwala na więcej operacji refaktoryzacji.

## <a name="renaming"></a>Zmiana nazwy

*Zmień nazwę* refaktoryzacji polecenie może służyć w dowolnym identyfikator kodu (na przykład nazwa klasy, nazwa właściwości itd.) aby znaleźć wszystkie wystąpienia identyfikatora, a następnie zmianę ich. Aby zmienić nazwę symbolu, kliknij prawym przyciskiem myszy na nim, a następnie wybierz **zmiany nazwy...** , lub użyj **Cmd (⌘) + R** powiązanie klucza:

![Zmień nazwę elementu menu.](media/refactoring-renaming1.png)

Spowoduje to wyróżnienie symbolu i wszelkie odwołania do niego. Po uruchomieniu, wpisując nazwę nowej automatycznie zmienia wszystkie odwołania w kodzie i zatwierdzić zmiany, naciskając klawisz **Enter**:

![Zmiana nazwy i identyfikatora](media/refactoring-renaming2.png)

## <a name="quick-actions"></a>Szybkie akcje

Szybkie akcje pozwalają na łatwe Refaktoryzacja, generowanie lub inny sposób modyfikować kodu za pomocą jednej akcji.

Szybkie akcje może służyć do:

* Zastosuj poprawkę kodu dla kodu naruszenie reguły analizatora
* Pomiń naruszenie reguły analizator kodu
* Stosowanie refaktoryzacji (na przykład wbudowanej zmiennej tymczasowej)
* Generuj kod (na przykład wprowadzić zmienną lokalną)

Szybkie akcje, które można zastosować za pomocą żarówki ![ikoną żarówki](media/quick-actions-light-bulb-icon.png) lub śrubokręt ![ikonę śrubokręt](media/quick-actions-screwdriver-icon.png) ikony, lub naciskając **opcji (⌥)** +  **Wprowadź** gdy kursor jest ustawiony na wiersz kodu, w którym akcja jest dostępna. Zostanie wyświetlony błąd żarówki z funkcją ![ikona żarówki z funkcją błędu](media/quick-actions-error-light-bulb-icon.png) czy istnieje czerwona fala wskazująca na wystąpienie błędu, a program Visual Studio zawiera poprawki dla tego błędu.

W dowolnym języku innych firm może zapewnić Diagnostyka niestandardowa i sugestie, na przykład jako część zestawu SDK i programu Visual Studio żarówki dostarczone, na podstawie tych reguł.

### <a name="quick-action-icons"></a>Ikony szybka akcja
Ikona, który jest wyświetlany, gdy dostępna jest szybka akcja oznacza wskazanie typu poprawkę lub refaktoryzacji, która jest dostępna. *Śrubokręt* ![ikonę śrubokręt](media/quick-actions-screwdriver-icon.png) ikona wskazuje, wystarczy, że istnieją akcje dostępne zmienić kod, ale niekoniecznie nie należy używać. *Żółta ikona żarówki* ![ikoną żarówki](media/quick-actions-light-bulb-icon.png) ikona wskazuje, akcje są dostępne, *powinien* czy, aby poprawić kod. *Błąd żarówki* ![ikona żarówki z funkcją błędu](media/quick-actions-error-light-bulb-icon.png) ikona wskazuje, jest dostępna akcja, która naprawia błąd w kodzie.

### <a name="to-see-a-light-bulb-or-screwdriver"></a>Aby zobaczyć żarówkę lub śrubokręt

- Jeśli dostępna jest poprawka, żarówki spontanicznie wyświetlane po umieszczeniu wskaźnika myszy w lokalizacji błędu.

   ![Ikona żarówki z umieszczeniu wskaźnika myszy](media/refactoring-lightbulb-hover.png)

- Żarówki i śrubokręty są wyświetlane na lewym marginesie edytor, gdy Przenieś karetkę do wiersza kodu, dla których dostępna jest szybka akcja.

- Naciśnij klawisz **opcji (⌥)**+**Enter** dowolnym miejscu w wierszu, aby wyświetlić listę dostępnych szybkie akcje i refaktoryzacje.

![Wyświetl elementy kontekstu](media/refactoring-context-action.png)

Wszystkie akcje kontekstowe kursor umożliwia podgląd co zostaną dodane lub usunięte z Twojego kodu.

![Opcja kontekstu wprowadź elementów](media/refactoring-image2a.png)

Aby włączyć te opcje, należy wybrać *Włącz analizę źródła otwartych plików* w opcjach **programu Visual Studio dla komputerów Mac > Preferencje > Edytor tekstu > analizę źródła**:

![Włączanie analizy źródła](media/refactoring-options.png)

Istnieje ponad 100 możliwych działań, które mogą być sugerowane, które są włączone lub wyłączone, przechodząc do **programu Visual Studio dla komputerów Mac > Preferencje > analizę źródła > C# > Akcje kodu** i zaznaczenie lub unselecting pole obok pozycji Akcja:

![Akcje analizy źródło języka C#](media/refactoring-image3a.png)

### <a name="common-quick-actions"></a>Typowe szybkie akcje

Dowiedz się więcej o typowe szybkie akcje w [typowe szybkie akcje](/visualstudio/ide/common-quick-actions) artykułu.

## <a name="source-analysis"></a>Analiza źródła

Analiza źródła analizuje kod na bieżąco, podkreślenie potencjalnych błędów i naruszeń stylu i zapewniając automatyczne poprawki jako kontekst akcji.

Aby wyświetlić wszystkie wyniki analizy źródła dla każdego pliku w dowolnym momencie, wyświetlanie paska przewijania po prawej stronie edytora tekstu:

![Pasek boczny analizy źródła](media/refactoring-image4a.png)

Kliknięcie okręgu u góry można wykonać iterację każdego sugestię o najpoważniejszych problemów wyświetlone pierwsze. Kursor w wierszu lub wynik wyświetla problem można naprawić za pomocą kontekstu akcji:

![Element analizy źródła](media/refactoring-image5.png)

## <a name="related-video"></a>Pokrewne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Refactoring-Code/player]

## <a name="see-also"></a>Zobacz także

- [Szybkie akcje (Visual Studio Windows)](/visualstudio/ide/quick-actions)
- [Refaktoryzacja kodu (Visual Studio Windows)](/visualstudio/ide/refactoring-in-visual-studio)