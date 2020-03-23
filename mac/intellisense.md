---
title: IntelliSense
description: Informacje dotyczące korzystania z programu IntelliSense w programie Visual Studio dla komputerów Mac
author: cobey
ms.author: cobey
ms.date: 08/16/2019
ms.openlocfilehash: 07ef1d6292e4ac88ca616d0f35e3fd831cacc649
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "75405807"
---
# <a name="intellisense"></a>IntelliSense

IntelliSense udostępnia kilka funkcji ułatwiających pisanie i edytowanie kodu. Na przykład oprócz uzupełniania kodu aparat IntelliSense zawiera również listy elementów członkowskich, informacje o parametrach i szybkie informacje.

W programie Visual Studio dla komputerów Mac intellisense jest dostarczany przez podstawową usługę edytora i jest obsługiwany w wielu językach, takich jak C#, XAML, F#, JavaScript i inne. Visual Studio dla komputerów Mac posiada również zaawansowane funkcje IntelliSense, takie jak możliwość pokazywalania uzupełnień z bibliotek, które nie zostały jeszcze zaimportowane do projektu.

## <a name="code-completion"></a>Uzupełnianie kodu

Podczas wpisywania w obsługiwanym pliku, takim jak plik kodu Języka C#, prawidłowe uzupełnienia aktualnie wpisywany ciąg będą wyświetlane na liście uzupełnień i aktualizowane podczas pisania. Ponadto jeśli usuniesz tekst, lista zostanie ponownie automatycznie zaktualizowana, aby uwzględnić szerszy zakres możliwości ukończenia danego ciągu. 

Okno ukończenia oferuje również obsługę filtrowania dołączonych uzupełnień według typu. Na przykład można ograniczyć członków listy do reprezentowania tylko typów, takich jak klasy lub delegatów. Ten proces filtrowania można włączyć, klikając określoną ikonę reprezentującą typ, który zostanie odfiltrowany, lub za pomocą skrótów klawiaturowych odpowiadających danemu typowi. Ikony, które znajdują się w dolnej części okna zakończenia, są następujące:

| Ikona                         | Nazwa          | Słowo kluczowe    | Hotkey |
| -----------------------------|---------------| -----------|--------|
| ![Ikona klas](media/classes-icon.png)  | class         | `class`    |  C
| ![Stała ikona](media/constant-icon.png) |  — stała      | `const`    |  O
| ![Ikona delegowania](media/delegate-icon.png) | delegate      | `delegate` |  D
| ![Ikona wyliczenia](media/enums-icon.png)    | enum          | `enum`     |  Z o.o.
| ![Ikona zdarzenia](media/event-icon.png)    | event         |            |  V
| ![Ikona pola](media/fields-icon.png)   | pole         |            |  Z o.o.
| ![Ikona interfejsu](media/interface-icon.png)| interface     | `interface`|  Z o.o.
| ![Ikona słowa kluczowego](media/keyword-icon.png)  | Słowa kluczowego       |            |  K.
| ![Ikona metody](media/method-icon.png)   | method        |            |  M
| ![Ikona obszaru nazw](media/namespace-icon.png)| przestrzeń nazw     | `namespace`|  Z o.o.
| ![Ikona rekwizytów](media/props-icon.png)    | property      |            |  P
| ![Ikona urywka](media/snippet-icon.png)  | Fragment       | `class`    |  Z o.o.
| ![Ikona struktury](media/struct-icon.png)   | — struktura     | `struct`   |  Z o.o.

Klikając dowolną z ikon lub naciskając odpowiednie skróty klawiszowe, lista uzupełnień ograniczy się tylko do typów zdefiniowanych przez zestaw filtrów.  

![Filtrowanie typu Intellisense](media/intellisense-typefiltering.gif)

## <a name="parameter-window"></a>Okno parametrów

Inną cechą IntelliSense jest możliwość podania listy parametrów w stosownych przypadkach. Lista parametrów zawiera szczegółowe informacje o podpisach metody dla wywoływanego kodu. Klikając na strzałki w górę / w dół w podpisie, można przełączać się między każdym z dostępnych podpisów parametrów, aby określić najbardziej odpowiednie dla Twoich potrzeb. Oprócz szczegółów typów dozwolonych danych, może istnieć również opis zdefiniowany w metodzie docelowej za pośrednictwem komentarzy XML.

![Lista parametrów](media/intellisense-parameter.png)

Po wypełnieniu parametrów, parametr, który aktualnie edytujesz, będzie pogrubiony, podczas gdy nieaktywne parametry będą miały standardową wagę. 


## <a name="triggering-completion-window-and-parameter-window"></a>Wyzwalanie okna zakończenia i okna parametrów

Okno uzupełniania zostanie wyzwolone automatycznie podczas wpisywane w pliku źródłowym. Można jednak również wyzwolić okno ukończenia `control-space`za pomocą skrótu . Ta kombinacja klawiszy spowoduje, że lista uzupełnień pojawi się w bieżącym położeniu cieszy. 

Można również ręcznie wyzwolić wygląd okna parametru, wpisując `control-shift-space`polecenie . Gdy daszka znajduje się w pozycji prawidłowej dla listy parametrów, lista parametrów pojawi się w pobliżu pozycji cieszy.

## <a name="see-also"></a>Zobacz też

- [Szybkie akcje (Visual Studio w systemie Windows)](/visualstudio/ide/quick-actions)
- [Kod refaktoryzatora (Visual Studio w systemie Windows)](/visualstudio/ide/refactoring-in-visual-studio)
