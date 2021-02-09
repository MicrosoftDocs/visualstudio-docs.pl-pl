---
title: Zaznaczanie błędów kod R
description: Jak korzystać z obsługi kompilacji Zaznaczanie błędów w programie Visual Studio dla języka R, w tym opcji Linter.
ms.date: 07/02/2018
ms.topic: conceptual
f1_keywords:
- vs.toolsoptionspages.text_editor.r.lint
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 1c32bffbd25a39ff2053dea22930365860ed04a7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873661"
---
# <a name="lint-r-code-in-visual-studio"></a>Lint kod R w programie Visual Studio

Linter analizuje kod, aby odsłonić potencjalne błędy, problemy z formatowaniem i inne zakłócenia kodu, takie jak fałszywe. Korzystanie z Linter również pomaga zachęcić do pewnych konwencji kodowania, takich jak identyfikatory. Takie konwencje są przydatne w zespołach i w innych sytuacjach wspólnych.

R Tools for Visual Studio (RTVS) to wbudowana Linter dla języka R, którego zachowanie jest kontrolowane za pomocą różnych opcji opisanych w tym artykule. Te opcje są dostępne w   >  **opcji** narzędzia  >  **Edytor tekstu**  >  **R**  >  **lint**.

Lint jest domyślnie wyłączona. Aby włączyć lint, ustaw dla opcji **All**  >  **enable lint** **wartość true**.

Po włączeniu Linter jest uruchamiany w edytorze podczas wpisywania. Problemy są wyświetlane jako zielono. Na poniższej ilustracji, na przykład, RTVS zidentyfikował sześć lintych problemów, w tym użycie `=` zamiast `<-` dla przypisania, brak odstępów wokół argumentów funkcji, użycie przypadku Pascala i wielkich identyfikatorów oraz użycie średnika. Umieszczenie kursora nad problemem zawiera opis.

![Przykłady danych wyjściowych Linter dla kodu R](media/linting-01.png)

Często zmienia się opcje Linter w zależności od potrzeb projektu lub pliku. Przykładowo można użyć przykładowego kodu z kursu online `=` zamiast z `<-` identyfikatorów przypadku w języku Pascal. Taki kod będzie wyświetlał częste ostrzeżenia Linter, ponieważ domyślne opcje Linter flagą te przypadki. Podczas pracy z tym kodem można wyłączyć opcje zamiast spędzać czas korygowania każdego wystąpienia.

## <a name="assignment-group"></a>Grupa przypisania

| Opcja | Wartość domyślna | Lint efekt |
| --- | --- | --- |
| **Określają \<-** | **True** | Określa, kiedy `<-` nie jest używany do przypisywania. |

## <a name="naming-group"></a>Grupa nazewnictwa

Te opcje służą do określania identyfikatorów, które używają różnych konwencji nazewnictwa:

| Opcja | Wartość domyślna | Lint efekt |
| --- | --- | --- |
| **Oflaguj camelCase** | **False** | Identyfikatory flag używające camelCase. |
| **Oflaguj długie nazwy** | **False** | Identyfikatory flag, których nazwy przekraczają **maksymalną długość nazwy** . |
| **Oflaguj wiele kropek** | **True** | Identyfikatory flag używające wielu kropek. |
| **Oflaguj PascalCase** | **True** | Identyfikatory flag używające PascalCase. |
| **Snake_case flagi** | **False** | Identyfikatory flag używające podkreśleń. |
| **Oflaguj wielkie litery** | **True** | Identyfikatory flag używające wersalików. |
| **Maksymalna długość nazwy** | **32** | Długość zastosowana z ustawieniem **flagi Long Names** . |

## <a name="spacing-group"></a>Grupa odstępów

Te opcje, dla których wszystkie są domyślnie ustawione na **wartość true** , kontrolują, gdzie Linter identyfikują problemy z odstępami: po nazwach funkcji, wokół przecinków, wokół operatorów, otwieraniu i zamykaniu pozycji klamrowych, spacja przed znakiem ().

## <a name="statements-group"></a>Grupa instrukcji

| Opcja | Wartość domyślna | Lint efekt |
| --- | --- | --- |
| **Wielokrotn** | **True** | Określa, kiedy wiele instrukcji znajduje się w tym samym wierszu. |
| **Średnikami** | **True** | Identyfikuje użycie średników. |

## <a name="text-group"></a>Grupa tekstowa

| Opcja | Wartość domyślna | Lint efekt |
| --- | --- | --- |
| **Limit długości wiersza** | **False** | Określa, czy flagi Linter są dłuższe niż **Maksymalna długość wiersza** . |
| **Maksymalna długość linii** | **80** | Ustawia długość wiersza zastosowana przez opcję **limitu długości wiersza** . |

## <a name="whitespace-group"></a>Grupa białych znaków

Te opcje, dla których wszystkie są domyślnie ustawione na **true** , kontrolują, gdzie Linter identyfikują problemy ze znakami: użycie kart, użycie podwójnych cudzysłowów, końcowe puste wiersze i końcowe odstępy.