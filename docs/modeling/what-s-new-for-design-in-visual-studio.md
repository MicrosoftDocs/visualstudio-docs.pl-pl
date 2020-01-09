---
title: Co nowego w dziedzinie projektowania w programie Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 6f81cc32604abe6d90ac0d263574e97df35c63bd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593502"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Co nowego w dziedzinie projektowania w programie Visual Studio 2017

## <a name="live-dependency-validation"></a>Weryfikacja zależności na żywo

Usunięcie niechcianych zależności jest ważną częścią zarządzania Twojej długu technicznego. Program Visual Studio zapewnia dynamiczną weryfikację zależności, w tym dokładne informacje o problemach, takich jak lokalizacja ich lokalizacji. Weryfikacja zależności na żywo ma pełne zalety nowych funkcji w Lista błędów i edytorze.

![Weryfikacja zależności na żywo w działaniu](media/dep-validation-whatsnew-01.png)

Środowisko autorskie zostało zmienione w celu ułatwienia odnajdywania i bardziej dostępności weryfikacji zależności. Terminologia została zmieniona z "diagram warstwowy" na "diagram zależności".

**Architektury** menu zawiera teraz polecenia, aby bezpośrednio utworzyć diagram zależności:

![Element zależności na żywo w menu architektury](media/dep-validation-whatsnew-02.png)

Nazwy i opisy właściwości warstwy zostały zmienione, aby zwiększyć ich czytelność:

![Nazwy właściwości zależności na żywo zaktualizowane](media/dep-validation-whatsnew-03.png)

Od razu zobaczysz wpływ zmian w wynikach analizy dla bieżącego kodu w rozwiązaniu przy każdym zapisaniu diagramu. Nie musisz czekać na ukończenie polecenia **Weryfikuj zależności** .

Aby uzyskać więcej informacji, zobacz [ten wpis w blogu](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Usunięto projektantów UML

Projektanci UML zostali usunięci z programu Visual Studio.

* Diagramy UML są teraz uporządkowane jako pliki XML
* Eksplorator modelu UML już nie istnieje.
* Modelowanie projektu odwołania nie są już używane do sprawdzania poprawności zależności
* Węzeł "Odwołania do warstwy" w Eksploratorze rozwiązań nie będzie już wyświetlany
* Akcja kompilacji "Weryfikuj" na diagramie zależności (warstwy) nie jest już używany — zadanie kompilacji została usunięta.
* Struktura projektu jest utrzymywana ze względu na Pełna zgodnooć wersji między wersjami
* Użytkownik może nadal Otwórz, tworzenia, edytowania i zapisać diagram zależności (warstwy) jako XML
* Elementy robocze TFS połączyć diagram zależności (warstwy) nie są dostępne na powierzchni projektowej
* Zaplecze — łączenie z DSL lub warstwy nie jest już obsługiwana
* Rozszerzalność UML w zestaw Modeling SDK nie jest już obsługiwana

Obsługa wizualizacji architektury .NET i C++ kodu jest dostępna za pomocą [map kodu](map-dependencies-across-your-solutions.md).

Jeśli jesteś użytkownikiem znaczące projektantów UML, można nadal używać programu Visual Studio 2015 i jego wcześniejsze wersje podczas decyzję w sprawie narzędziem alternatywne do własnych potrzeb UML.

Aby uzyskać więcej informacji, zobacz [ten wpis w blogu](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="a-nameversionsupport-edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Obsługa wersji narzędzia architektury i modelowania

Program Visual Studio jest dostępny w kilku wersjach. Nie wszystkie te zapewniają obsługę architekturę i narzędzia do modelowania. W poniższej tabeli przedstawiono Dostępność poszczególnych narzędzi.

|**Funkcja**|**Wersja Enterprise**|**W wersji Professional**|**Wersja Community edition**|
|-|-|-|-|
|**Mapy kodu**|Tak|Mapy tylko filtrowania kodu obsługuje map kodu do czytania, dodawanie nowych węzłów ogólny i tworzenie nowy Graf skierowany z zaznaczenia.|-|
|**Diagramów zależności**|Tak|Obsługuje tylko odczytywanie diagramów zależności.|Obsługuje tylko odczytywanie diagramów zależności.|
|**Ukierunkowanych wykresów** (diagramy DGML)|Tak|Tak|Tak|
|**Klonowanie kodu**|Tak|-|-|
