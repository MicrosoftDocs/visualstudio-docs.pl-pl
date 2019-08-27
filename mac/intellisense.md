---
title: IntelliSense
description: Informacje o korzystaniu z technologii IntelliSense w Visual Studio dla komputerów Mac
author: cobey
ms.author: cobey
ms.date: 08/16/2019
ms.openlocfilehash: 3e99c31b1ab4d12532d701e4626ac9c1aae7df56
ms.sourcegitcommit: 0bd63f3bc429ae059b9df6e45c6b8dcae6152940
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2019
ms.locfileid: "70026958"
---
# <a name="intellisense"></a>IntelliSense

Technologia IntelliSense udostępnia kilka funkcji, które ułatwiają zwiększenie możliwości pisania i edytowania kodu. Na przykład oprócz uzupełniania kodu aparat IntelliSense zawiera również listę elementów członkowskich, informacje o parametrach i szybkie informacje.

W Visual Studio dla komputerów Mac technologia IntelliSense jest udostępniana przez podstawową usługę edytora i jest obsługiwana w wielu językach, takich jak C#XAML, F#JavaScript i innych. Visual Studio dla komputerów Mac również funkcje zaawansowane funkcje IntelliSense, takie jak możliwość wyświetlania uzupełnień z bibliotek, które nie zostały jeszcze zaimportowane do projektu.

## <a name="code-completion"></a>Uzupełnianie kodu

Podczas wpisywania w obsługiwanym pliku, na przykład C# pliku kodu, prawidłowe uzupełnianie ciągu, który jest aktualnie wpisywany, będą wyświetlane na liście uzupełniania i aktualizowane podczas wpisywania. Ponadto po usunięciu tekstu lista zostanie ponownie zaktualizowana w celu uwzględnienia szerszego zakresu możliwości ukończenia danego ciągu. 

Okno uzupełniania oferuje również obsługę filtrowania uwzględnionych uzupełnień według typu. Na przykład można ograniczyć składowe listy tylko do reprezentowania typów, takich jak klasy lub Delegaty. Ten proces filtrowania można włączyć za pomocą kliknięcia określonej ikony reprezentującej typ, który będzie filtrowany, lub za pomocą skrótów klawiaturowych odpowiadających danemu typowi. Ikony, które znajdują się u dołu okna zakończenia, są następujące:

| Ikona                         | Nazwa          | Słowo kluczowe    | Klawisz skrótu |
| -----------------------------|---------------| -----------|--------|
| ![Ikona klas](media/classes-icon.png)  | class         | `class`    |  ⌥ C
| ![Ikona stałej](media/constant-icon.png) | — stała      | `const`    |  ⌥ O
| ![Ikona delegata](media/delegate-icon.png) | delegate      | `delegate` |  ⌥ D
| ![Ikona wyliczenia](media/enums-icon.png)    | enum          | `enum`     |  ⌥ E
| ![Ikona zdarzenia](media/event-icon.png)    | zdarzenie         |            |  ⌥ V
| ![Ikona pola](media/fields-icon.png)   | pole         |            |  ⌥ F
| ![Ikona interfejsu](media/interface-icon.png)| interface     | `interface`|  ⌥ I
| ![Ikona słowa kluczowego](media/keyword-icon.png)  | kodu       |            |  ⌥ K
| ![Ikona metody](media/method-icon.png)   | — metoda        |            |  ⌥ M
| ![Ikona przestrzeni nazw](media/namespace-icon.png)| — przestrzeń nazw     | `namespace`|  ⌥ N
| ![Ikona właściwości](media/props-icon.png)    | property      |            |  ⌥ P
| ![Ikona fragmentu kodu](media/snippet-icon.png)  | fragment kodu       | `class`    |  ⌥ S
| ![Ikona struktury](media/struct-icon.png)   | — struktura     | `struct`   |  ⌥ S

Kliknięcie dowolnej ikony lub naciśnięcie odpowiednich klawiszy skrótu spowoduje ograniczenie listy uzupełniania tylko do typów zgodnie z definicją zestawu filtrów.  

![Filtrowanie typów IntelliSense](media/intellisense-typefiltering.gif)

## <a name="show-import-items"></a>Pokaż elementy importu

Domyślnie funkcja IntelliSense będzie wyświetlać tylko uzupełniania z bibliotek, które zostały zaimportowane do projektu. Na przykład, jeśli nie `System.Collections.Generic` zaimportowano go za pośrednictwem `using` tego elementu, `List<>`nie można wykonać operacji. Aby wyświetlić uzupełniania z bibliotek, które nie zostały zaimportowane, należy włączyć opcję **Pokaż elementy importu** w preferencjach dla Visual Studio dla komputerów Mac. To ustawienie można znaleźć w obszarze **preferencje > Edytor tekstu > IntelliSense**:

![IntelliSense — Pokaż elementy importu](media/intellisense-showimport.png)

Po włączeniu **pozycji Importuj elementy** zostaną uwzględnione zakończenia, które nie zostały jeszcze zaimportowane. Po wybraniu elementu, który odnosi się do niezadeklarowanej biblioteki `using` , instrukcja dla tej biblioteki zostanie automatycznie dodana do nagłówka pliku kodu. Nazwa biblioteki, do której należy uzupełnienie, jest również wyświetlana wraz z samą ukończeniem.

![Pokaż listę elementów importu](media/intellisense-importaction.png)

## <a name="parameter-window"></a>Okno parametrów

Kolejną funkcją IntelliSense jest możliwość udostępnienia listy parametrów, tam gdzie jest to konieczne. Lista parametrów zawiera szczegółowe informacje o sygnaturach metod dla wywoływanego kodu. Klikając strzałki w górę/w dół w podpisie, możesz przechodzić przez każdy z dostępnych podpisów parametrów, aby określić najbardziej odpowiednie dla Twoich potrzeb. Oprócz szczegółowych informacji o typach dozwolonych danych może być również opis zdefiniowany w metodzie docelowej za pośrednictwem komentarzy XML.

![Lista parametrów](media/intellisense-parameter.png)

Podczas wypełniania parametrów parametr, który jest aktualnie edytowany, zostanie pogrubiony, podczas gdy nieaktywne parametry będą mieć wagę standardową. 


## <a name="triggering-completion-window-and-parameter-window"></a>Wyzwalanie okna uzupełniania i okna parametrów

Okno uzupełniania zostanie wyzwolone automatycznie podczas wpisywania w pliku źródłowym. Można jednak również wyzwolić okno uzupełniania za pomocą skrótu `control-space`. Ta kombinacja klawiszy spowoduje, że lista uzupełniania zostanie wyświetlona w bieżącej pozycji karetki. 

Możesz również ręcznie wyzwolić wygląd okna parametrów, wpisując `control-shift-space`. Gdy karetka znajduje się w położeniu, które jest prawidłowe dla listy parametrów, lista parametrów pojawi się blisko położenia karetki.

## <a name="see-also"></a>Zobacz także

- [Szybkie akcje (Visual Studio w systemie Windows)](/visualstudio/ide/quick-actions)
- [Kod refaktoryzacji (Visual Studio w systemie Windows)](/visualstudio/ide/refactoring-in-visual-studio)
