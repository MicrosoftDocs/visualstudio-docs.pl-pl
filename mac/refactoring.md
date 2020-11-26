---
title: Refaktoryzacja kodu
description: Poprawiaj kod przy użyciu Visual Studio dla komputerów Mac i szybkie akcje.
author: jmatthiesen
ms.author: jomatthi
ms.date: 07/03/2020
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 3892117e5c84a71f258d4e019105fca0a8cf9c5b
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189241"
---
# <a name="refactoring"></a>Refaktoryzacja

Refaktoryzacja kodu jest sposobem na ponowne rozmieszczenie, restrukturyzację i wyjaśnienie istniejącego kodu przy zapewnieniu, że ogólne zachowanie kodu nie ulegnie zmianie.

Refaktoryzacja generuje bazę kodu dotyczący, dzięki czemu jest bardziej użyteczny, czytelny i konserwowany dla Ciebie lub dowolnego innego dewelopera lub użytkownika, który może odwoływać się do kodu.

Integracja Visual Studio dla komputerów Mac z usługą Roslyn — platforma kompilatora .NET Open Source firmy Microsoft umożliwia wykonywanie dodatkowych operacji refaktoryzacji.

## <a name="renaming"></a>Zmiana nazwy

Polecenia *zmiany nazwy* można użyć dla dowolnego identyfikatora kodu (na przykład nazwy klasy, nazwy właściwości itp.), aby znaleźć wszystkie wystąpienia tego identyfikatora i je zmienić. Aby zmienić nazwę symbolu, kliknij go prawym przyciskiem myszy i wybierz polecenie **Zmień nazwę...** lub Użyj **polecenia CMD (⌘) + R** Key Binding:

![Zmień nazwę elementu menu](media/refactoring-renaming1.png)

Podświetla symbol i wszystkie odwołania do niego. Po rozpoczęciu wpisywania nowej nazwy automatycznie zmienia wszystkie odwołania w kodzie i można zatwierdzić zmiany, naciskając klawisz **Enter**:

![Zmiana nazwy i identyfikator](media/refactoring-renaming2.png)

## <a name="quick-actions-and-refactorings"></a>Szybkie akcje i operacje refaktoryzacji

Szybkie akcje i refaktoryzacje umożliwiają łatwe refaktoryzację, generowanie lub modyfikowanie kodu przy użyciu jednej akcji.

Szybkie akcje mogą służyć do:

* Zastosuj poprawkę kodu dla naruszenia reguły analizatora kodu
* Pomijanie naruszenia reguły analizatora kodu
* Zastosuj refaktoryzację (na przykład w wbudowanej zmiennej tymczasowej)
* Generuj kod (na przykład wprowadź zmienną lokalną)

Szybkie akcje można stosować przy użyciu ikon żarówki żarówki ![ ](media/quick-actions-light-bulb-icon.png) lub ![ śrubokrętów ](media/quick-actions-screwdriver-icon.png) , lub naciskając przycisk **opcji (⌥)** + **Enter** , gdy kursor znajduje się w wierszu kodu, dla którego akcja jest dostępna. Zobaczysz ikonę żarówki błędów żarówki z błędem ![ ](media/quick-actions-error-light-bulb-icon.png) , jeśli istnieje czerwona zygzakowata wskazująca na błąd, a dla tego błędu jest dostępna poprawka.

W przypadku dowolnego języka osoby trzecie mogą zapewnić niestandardową diagnostykę i sugestie, na przykład w ramach zestawu SDK, a żarówki programu Visual Studio w oparciu o te reguły.

### <a name="quick-action-icons"></a>Ikony szybkiej akcji
Ikona wyświetlana, gdy szybka akcja jest dostępna, zawiera wskazanie typu poprawki lub refaktoryzacji, która jest dostępna. *screwdriver* ![ Ikona ikony śrubokrętu śrubokręta ](media/quick-actions-screwdriver-icon.png) wskazuje, że dostępne są akcje umożliwiające zmianę kodu, ale nie należy ich używać. Ikona *żółtej* żarówki żarówki ![ ](media/quick-actions-light-bulb-icon.png) wskazującej, że istnieją dostępne akcje, które *należy* wykonać, aby poprawić kod. Ikona *żarówki błędu* żarówki błędów ![ wskazuje, ](media/quick-actions-error-light-bulb-icon.png) że jest dostępna akcja, która naprawia błąd w kodzie.

### <a name="to-see-a-light-bulb-or-screwdriver"></a>Aby zobaczyć żarówkę lub śrubokręt

- Jeśli poprawka jest dostępna, żarówki są spontanicznie wyświetlane po umieszczeniu wskaźnika myszy w lokalizacji błędu.

   ![Żarówka z przesuwaniem myszy](media/refactoring-lightbulb-hover.png)

- Żarówki i śrubokręty są wyświetlane na lewym marginesie edytora po przesunięciu karetki do wiersza kodu, dla którego jest dostępna szybka akcja lub Refaktoryzacja.

- Naciśnij pozycję **Option (⌥)** + **Enter** w dowolnym miejscu w wierszu, aby wyświetlić listę dostępnych szybkich akcji i refaktoryzacji.

![Wyświetl elementy kontekstu](media/refactoring-context-action.png)

Umieszczenie kursora na dowolnym z akcji kontekstowych zapewnia podgląd elementów, które zostaną dodane lub usunięte z kodu.

![Opcja wprowadzania elementów kontekstu](media/refactoring-image2a.png)

Aby włączyć te opcje, należy wybrać opcję *Włącz analizę źródła otwartych plików* w opcjach, **Visual Studio dla komputerów Mac > preferencji > Edytor tekstu > analiza źródła**:

![Włączanie analizy źródła](media/refactoring-options.png)

Istnieje ponad 100 możliwych akcji, które można zasugerować, które są włączane lub wyłączane, przechodząc do **Visual Studio dla komputerów Mac preferencji > > analiza źródła > C# > akcji kodu** i zaznaczając lub usuwając zaznaczenie pola obok akcji:

![Akcje analizy źródła języka C#](media/refactoring-image3a.png)

### <a name="common-quick-actions"></a>Typowe szybkie akcje

Możesz dowiedzieć się więcej o typowych szybkich akcjach w artykule [typowe szybkie akcje](/visualstudio/ide/common-quick-actions) .

## <a name="source-analysis"></a>Analiza źródła

Analiza źródła analizuje kod na bieżąco przez podkreślanie potencjalnych błędów i naruszeń stylu oraz dostarczanie autopoprawek jako akcji kontekstowych.

W dowolnym momencie możesz wyświetlić wszystkie wyniki analizy źródłowej dowolnego pliku, wyświetlając pasek przewijania po prawej stronie edytora tekstu:

![Pasek boczny analizy źródła](media/refactoring-image4a.png)

Po kliknięciu kółka u góry można wykonać iterację poszczególnych sugestii z najwyższymi problemami dotyczącymi ważności, które są wyświetlane jako pierwsze. Umieszczenie wskaźnika myszy na pojedynczym wyniku lub w wierszu powoduje wyświetlenie problemu, który można naprawić za pomocą akcji kontekstu:

![Element analizy źródła](media/refactoring-image5.png)

## <a name="related-video"></a>Pokrewne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Refactoring-Code/player]

## <a name="see-also"></a>Zobacz też

- [Szybkie akcje (Visual Studio w systemie Windows)](/visualstudio/ide/quick-actions)
- [Kod refaktoryzacji (Visual Studio w systemie Windows)](/visualstudio/ide/refactoring-in-visual-studio)
