---
title: Refaktoryzacja kodu
description: Udoskonalanie kodu przy użyciu programu Visual Studio dla komputerów Mac i szybkich akcji.
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 5a87b87f3a14462daec1e069fe222164818d2a19
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "67691297"
---
# <a name="refactoring"></a>Refaktoryzacja

Refaktoryzacja kodu jest sposobem, aby zmienić rozmieszczenie, restrukturyzacji i wyjaśnienia istniejącego kodu, zapewniając jednocześnie, że ogólne zachowanie kodu nie zmienia.

Refaktoryzowanie tworzy zdrowszą bazę kodu, dzięki czemu jest bardziej użyteczny, czytelny i owalny dla Ciebie lub innego dewelopera lub użytkownika, który może odnosić się do kodu.

Integracja programu Visual Studio for Mac z Roslyn, platformą kompilatora .NET typu open source firmy Microsoft, umożliwia więcej operacji refaktoryzacji.

## <a name="renaming"></a>Zmienianie nazw

Polecenie *Zmień nazwę* refaktoryzacji może służyć do dowolnego identyfikatora kodu (na przykład nazwa klasy, nazwa właściwości itp.), aby znaleźć wszystkie wystąpienia tego identyfikatora i zmienić je. Aby zmienić nazwę symbolu, kliknij na niego prawym przyciskiem myszy i wybierz **polecenie Zmień nazwę...** lub użyj powiązania **klawiszy Cmd (♡) + R:**

![Zmienianie nazwy elementu menu](media/refactoring-renaming1.png)

To wyróżnia symbol i wszelkie odniesienia do niego. Po rozpoczęciu wpisywania nowej nazwy automatycznie zmienia wszystkie odwołania w kodzie i można zatwierdzić zmiany, naciskając **klawisz Enter:**

![Zmiana nazwy i identyfikator](media/refactoring-renaming2.png)

## <a name="quick-actions"></a>Szybkie akcje

Szybkie akcje umożliwiają łatwe refaktoryzowanie, generowanie lub modyfikowanie kodu za pomocą jednej akcji.

Szybkie akcje mogą być używane do:

* Stosowanie poprawki kodu w przypadku naruszenia reguły analizatora kodu
* Pomijanie naruszenia reguły analizatora kodu
* Stosowanie refaktoryzacji (na przykład zmiennej tymczasowej wbudowanej)
* Generowanie kodu (na przykład wprowadzenie zmiennej lokalnej)

Szybkie akcje można zastosować za pomocą ![ikony](media/quick-actions-light-bulb-icon.png) żarówki ![żarówki lub](media/quick-actions-screwdriver-icon.png) ikony śrubokręta lub naciskając **option (♠)**+**Wprowadź,** gdy kursor znajduje się w wierszu kodu, dla którego dostępna jest akcja. Zostanie wyświetlony błąd żarówki ![błąd żarówki ikony](media/quick-actions-error-light-bulb-icon.png) żarówki, jeśli istnieje czerwony squiggle wskazujący błąd i Visual Studio ma poprawkę dostępną dla tego błędu.

W dowolnym języku strony trzecie mogą zapewnić niestandardowe diagnostyki i sugestie, na przykład jako część SDK i visual studio żarówki zapalają się na podstawie tych reguł.

### <a name="quick-action-icons"></a>Ikony szybkiej akcji
Ikona, która pojawia się, gdy dostępna jest szybka akcja, wskazuje typ dostępnej poprawki lub refaktoryzacji. Ikona ![śrubokręta wskazuje tylko, że istnieją działania dostępne do zmiany kodu, ale nie należy ich używać. *screwdriver* ](media/quick-actions-screwdriver-icon.png) ](media/quick-actions-light-bulb-icon.png) *Ikona ikony żółtej żarówki* ![wskazuje, że są dostępne działania, które *należy* wykonać, aby poprawić swój kod. Ikona ikony błędu](media/quick-actions-error-light-bulb-icon.png) *żarówki błędu żarówki* ![wskazuje, że jest dostępna akcja, która rozwiązuje błąd w kodzie.

### <a name="to-see-a-light-bulb-or-screwdriver"></a>Aby zobaczyć żarówkę lub śrubokręt

- Jeśli poprawka jest dostępna, żarówki pojawiają się spontanicznie po najechaniu myszą w miejscu błędu.

   ![Żarówka z unoszącą się myszą](media/refactoring-lightbulb-hover.png)

- Żarówki i śrubokręty pojawiają się na lewym marginesie edytora po przeniesieniu daszka do linii kodu, dla której dostępna jest szybka akcja.

- Naciśnij **opcję (♠)**+**Wprowadź** w dowolnym miejscu w wierszu, aby wyświetlić listę dostępnych szybkich akcji i refaktoryzacji.

![Wyświetlanie elementów kontekstu](media/refactoring-context-action.png)

Najechanie kursorem na dowolną z akcji kontekstu zapewnia podgląd tego, co zostanie dodane lub usunięte z kodu.

![Opcja Wprowadź elementy kontekstu](media/refactoring-image2a.png)

Aby włączyć te opcje, należy wybrać *włącz analizę źródła otwartych plików* w opcjach Visual Studio > **Preferencje > Edytor tekstu > analiza źródła:**

![Włączanie analizy źródła](media/refactoring-options.png)

Istnieje ponad 100 możliwych akcji, które można zasugerować, które są włączone lub wyłączone, przeglądając **program Visual Studio > Preferencje > analiza źródła > akcje kodu > C#** i zaznaczając lub odznaczając pole obok akcji:

![Akcje analizy źródła w języku C#](media/refactoring-image3a.png)

### <a name="common-quick-actions"></a>Typowe szybkie akcje

Więcej informacji na temat typowych szybkich akcji można dowiedzieć się w artykule [Typowe szybkie akcje.](/visualstudio/ide/common-quick-actions)

## <a name="source-analysis"></a>Analiza źródła

Analiza źródła analizuje kod na bieżąco, podkreślając potencjalne błędy i naruszenia stylu i zapewniając automatyczne poprawki jako akcje kontekstu.

Wszystkie wyniki analizy źródłowej dla dowolnego pliku można wyświetlić w dowolnym momencie, przeglądając pasek przewijania po prawej stronie edytora tekstu:

![Pasek boczny analizy źródła](media/refactoring-image4a.png)

Jeśli klikniesz na okrąg u góry, możesz iterować za pomocą każdej sugestii, z najwyższymi problemami z ważnością wyświetlanymi jako pierwsze. Najechanie kursorem na pojedynczy wynik lub linię powoduje wyświetlenie problemu, który można rozwiązać za pomocą akcji kontekstowych:

![Element analizy źródła](media/refactoring-image5.png)

## <a name="related-video"></a>Podobne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Refactoring-Code/player]

## <a name="see-also"></a>Zobacz też

- [Szybkie akcje (Visual Studio w systemie Windows)](/visualstudio/ide/quick-actions)
- [Kod refaktoryzatora (Visual Studio w systemie Windows)](/visualstudio/ide/refactoring-in-visual-studio)