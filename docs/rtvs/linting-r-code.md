---
title: Kod Zaznaczanie błędów języka R
description: Jak pracować z obsługą Zaznaczanie błędów kompilacji w programie Visual Studio dla języka R, włącznie z opcjami linter.
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970744"
---
# <a name="lint-r-code-in-visual-studio"></a>Kod lint języka R w programie Visual Studio

Linter analizuje kod, aby wyświetlić potencjalnych błędów, problemów z formatowaniem tekstu i innych szumu kodu, takich jak znak odstępu fałszywe. Za pomocą linter pomaga również zachęcać określonych konwencji kodowania, takie jak nazewnictwa identyfikatorów. Takie konwencje są pomocne w obrębie zespołów i innych sytuacjach współpracy.

R Tools for Visual Studio (RTVS) zapewnia wbudowane linter języka R, z zachowaniem jest kontrolowany przy użyciu różnych opcji opisanych w tym artykule. Te opcje można znaleźć w **narzędzia** > **opcje** > **edytora tekstów** > **R**  >  **Lint**.

Lint jest domyślnie wyłączona. Aby włączyć lint, ustaw **wszystkich** > **povolit lint** opcję **True**.

Po włączeniu linter działa w edytorze podczas pisania. Problemy są traktowane jako zielone symbole. Na poniższym rysunku, na przykład RTVS ustaliła, że sześciu problemów lint, w tym użycie `=` zamiast `<-` przydziału, brak odstępów wokół argumentów funkcji, użyj pisanymi wielkimi literami, wielkie litery identyfikatorów i użyj średnika . Kursor problemu zawiera opis.

![Przykładowe dane wyjściowe linter kod R](media/linting-01.png)

Często zmieniać linter opcje w zależności od potrzeb projektu lub pliku. Na przykład użyć przykładowego kodu z kursu online `=` zamiast `<-` wraz z identyfikatorami pisanymi wielkimi literami. Taki kod zostanie wyświetlony częste linter ostrzeżenia, ponieważ domyślne opcje linter Flaga tych przypadkach. Następnie podczas pracy z tym kodem, można wyłączyć opcji, nie trzeba spędzać czas poprawiania każde wystąpienie.

## <a name="assignment-group"></a>Przypisania grupy

| Opcja | Wartość domyślna | Efekt lint |
| --- | --- | --- |
| **Wymuszanie \<-** | **True** | Określa, kiedy `<-` nie jest używany do przypisania. |

## <a name="naming-group"></a>Nazwy grupy

Te opcje Flaga identyfikatorów, które używają różnych konwencji nazewnictwa:

| Opcja | Wartość domyślna | Efekt lint |
| --- | --- | --- |
| **Flaga camelCase** | **False** | Identyfikatory flagi, które używają camelCase. |
| **Długie nazwy flagi** | **False** | Flagi identyfikatory, których nazwy przekracza **maksymalna długość nazwy** ustawienie. |
| **Flaga wielu punktów.** | **True** | Flagi identyfikatorów, które używają wielu punktów. |
| **Flag PascalCase** | **True** | Identyfikatory flagi, które używają PascalCase. |
| **Flaga snake_case** | **False** | Flagi identyfikatorów, które zawierać znaki podkreślenia. |
| **Flaga wielkimi literami** | **True** | Identyfikatory flagi używających wersalików. |
| **Maksymalna długość nazwy** | **32** | Długość stosowane z **Flaga długich nazw** ustawienie. |

## <a name="spacing-group"></a>Odstępy między grupy

Te opcje, które są ustawione na **True** domyślnie kontrolować, gdzie linter identyfikuje problemy odstępy: po nazwy funkcji w całym przecinkami dookoła operatorów, otwierające i zamykające nawiasy pozycji odstęp przed (i spację wewnątrz ().

## <a name="statements-group"></a>Grupy instrukcji

| Opcja | Wartość domyślna | Efekt lint |
| --- | --- | --- |
| **Wiele** | **True** | Określa, w przypadku wielu instrukcji w tym samym wierszu. |
| **Średnikami** | **True** | Identyfikuje używa średnikami. |

## <a name="text-group"></a>Grupy tekstu

| Opcja | Wartość domyślna | Efekt lint |
| --- | --- | --- |
| **Limit długości wiersza** | **False** | Określa, czy linter flagi wierszy przekracza **maksymalna długość wiersza** opcji. |
| **Maksymalna długość wiersza** | **80** | Ustawia długość wiersza stosowane przez **limit długości wiersza** opcji. |

## <a name="whitespace-group"></a>Grupa białe znaki

Te opcje, które są ustawione na **True** domyślnie kontrolować, gdzie linter identyfikuje problemy odstępu: Korzystanie z kart, użyj podwójnych cudzysłowów, końcowe puste wiersze i końcowe białe znaki.