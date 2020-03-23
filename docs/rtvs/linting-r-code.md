---
title: Linting Kod R
description: Jak pracować z visual studio wbudowanej linting obsługi języka R, w tym opcje linter.
ms.date: 07/02/2018
ms.topic: conceptual
f1_keywords:
- vs.toolsoptionspages.text_editor.r.lint
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: aecf9d95fb8a3b2cda659e2694bff145424e150b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62970744"
---
# <a name="lint-r-code-in-visual-studio"></a>Kod Lint R w programie Visual Studio

Linter analizuje kod, aby ujawnić potencjalne błędy, problemy z formatowaniem i inne szumy kodu, takie jak fałszywe odstępy. Za pomocą linter pomaga również zachęcić niektórych konwencji kodowania, takich jak identyfikatory są nazwane. Takie konwencje są pomocne w zespołach i innych sytuacjach współpracy.

R Tools for Visual Studio (RTVS) zapewnia wbudowany linter dla języka R, którego zachowanie jest kontrolowane za pomocą różnych opcji opisanych w tym artykule. Te opcje znajdują się w **narzędzia** > **opcje** > **edytor** > tekstu**R** > **Lint**.

Lint jest domyślnie wyłączona. Aby włączyć lint, ustaw opcję **Wszystkie** > **włączynie lint** na **True**.

Po włączeniu linter działa w edytorze podczas pisania. Problemy pojawiają się jako zielone faliszki. Na przykład w poniższej `=` grafice RTVS zidentyfikował sześć problemów z `<-` kłaczkami, w tym użycie zamiast przypisania, brak odstępów między argumentami funkcji, użycie wielkości liter Pascala i wielkich identyfikatorów oraz użycie średnika. Najechanie kursorem na problem zawiera opis.

![Przykłady wyjścia linter dla kodu R](media/linting-01.png)

Często zmieniasz opcje linter w zależności od potrzeb projektu lub pliku. Na przykład przykładowy kod z `=` kursu online `<-` może być używany zamiast identyfikatorów przypadków pascala. Taki kod będzie wyświetlać częste ostrzeżenia linter, ponieważ domyślne opcje linter flagi tych przypadkach. Podczas pracy z tym kodem, a następnie można wyłączyć opcje zamiast spędzać czas poprawiania każdego wystąpienia.

## <a name="assignment-group"></a>Grupa przydziałów

| Opcja | Wartość domyślna | Efekt kłających się |
| --- | --- | --- |
| **Wymusić\<-** | **True** | Określa, `<-` kiedy nie jest używany do przypisywania. |

## <a name="naming-group"></a>Grupa nazewnictwa

Te opcje flagi identyfikatory, które używają różnych konwencji nazewnictwa:

| Opcja | Wartość domyślna | Efekt kłających się |
| --- | --- | --- |
| **Flaga camelCase** | **False** | Flagi identyfikatory, które używają camelCase. |
| **Flaga długie nazwy** | **False** | Flagi identyfikatorów, których nazwy przekraczają **ustawienie Maksymalna długość nazwy.** |
| **Oznaczanie wielu punktów** | **True** | Flagi identyfikatory, które używają wielu punktów. |
| **Flaga PascalCase** | **True** | Flagi identyfikatory, które używają PascalCase. |
| **Flaga snake_case** | **False** | Flagi identyfikatory, które używają podkreślenia. |
| **Flaga wielkie litery** | **True** | Flagi identyfikatory, które używają wszystkich wersalików. |
| **Maksymalna długość nazwy** | **32** | Długość zastosowana z **ustawieniem Nazwy długie flagi.** |

## <a name="spacing-group"></a>Grupa odstępów

Te opcje, z których wszystkie są domyślnie ustawione na **True,** kontrolują, gdzie linter identyfikuje odstępy problemy: po nazwy funkcji, wokół przecinków, wokół operatorów, otwieranie i zamykanie kręte pozycje, spacja przed (i miejsce wewnątrz ().

## <a name="statements-group"></a>Grupa wyciągów

| Opcja | Wartość domyślna | Efekt kłających się |
| --- | --- | --- |
| **Wiele** | **True** | Identyfikuje, gdy wiele instrukcji są w tym samym wierszu. |
| **Średnikami** | **True** | Identyfikuje zastosowania średników. |

## <a name="text-group"></a>Grupa tekstowa

| Opcja | Wartość domyślna | Efekt kłających się |
| --- | --- | --- |
| **Granica długości linii** | **False** | Określa, czy linter flagi linii dłużej niż **Max długość linii** opcji. |
| **Maksymalna długość linii** | **80** | Ustawia długość linii zastosowaną przez opcję **Limit długości linii.** |

## <a name="whitespace-group"></a>Grupa odstępów

Te opcje, z których wszystkie są domyślnie ustawione na **True,** kontrolują, gdzie linter identyfikuje problemy z odstępami: użycie kart, użycie cudzysłowów podwójnych, końcowe puste linie i końcowe odstępy.