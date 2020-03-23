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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302953"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Co nowego w dziedzinie projektowania w programie Visual Studio 2017

## <a name="live-dependency-validation"></a>Sprawdzanie poprawności zależności na żywo

Usuwanie niechcianych zależności jest ważną częścią zarządzania długiem technicznym. Visual Studio zapewnia weryfikacji na żywo zależności, w tym dokładne informacje o problemach, takich jak gdzie się znajdują. Sprawdzanie poprawności zależności na żywo wykorzystuje w pełni zalety nowych funkcji na liście błędów i edytorze.

![Sprawdzanie poprawności zależności na żywo w działaniu](media/dep-validation-whatsnew-01.png)

Środowisko tworzenia zostało zmienione, aby sprawdzanie poprawności zależności było bardziej wykrywalne i bardziej dostępne. Terminologia została zmieniona z "Diagram warstwy" na "Diagram zależności".

**Architektura** menu zawiera teraz polecenie do bezpośredniego tworzenia diagramu zależności:

![Element zależności na żywo w menu Architektura](media/dep-validation-whatsnew-02.png)

Nazwy i opisy właściwości warstw zostały zmienione, aby uczynić je bardziej znaczącymi:

![Zaktualizowane nazwy właściwości zależności na żywo](media/dep-validation-whatsnew-03.png)

Natychmiast zobaczysz wpływ zmian w wynikach analizy dla bieżącego kodu w rozwiązaniu za każdym razem, gdy zapisujesz diagram. Nie trzeba czekać na zakończenie sprawdzania **poprawności zależności** polecenia.

Aby uzyskać więcej informacji, zobacz [ten wpis w blogu](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Projektanci UML zostali usunięci

Projektanci UML zostały usunięte z programu Visual Studio.

* Diagramy UML są teraz prezentowane jako pliki XML
* Eksplorator modelu UML już nie istnieje
* Odwołania do projektu modelowania nie są już używane do sprawdzania poprawności zależności
* Węzeł "Odwołuje się do warstw" w Eksploratorze rozwiązań nie jest już wyświetlany
* Akcja kompilacji "Sprawdź poprawność" na diagramie zależności (warstwa) nie jest już używana — zadanie kompilacji zostało usunięte
* Struktura projektu jest utrzymywana w przypadku zaokrąglania między wersjami
* Nadal można otwierać, tworzyć, edytować i zapisywać diagram zależności (warstwy) jako XML
* Elementy robocze TFS połączone z diagramem zależności (warstwa) nie są dostępne na powierzchni projektowej
* Powrót do łączenia z dsl lub warstwy nie jest już obsługiwany
* Rozszerzalność UML w sdku modelowania nie jest już obsługiwana

Obsługa wizualizacji architektury kodu .NET i C++ jest dostępna za pośrednictwem [map kodu.](map-dependencies-across-your-solutions.md)

Jeśli jesteś znaczącym użytkownikiem projektantów UML, możesz nadal używać programu Visual Studio 2015 lub wcześniejszych wersji, podczas gdy zdecydujesz się na alternatywne narzędzie dla potrzeb UML.

Aby uzyskać więcej informacji, zobacz [ten wpis w blogu](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Obsługa edycji dla architektury i narzędzi do modelowania

Visual Studio jest dostępny w kilku wersjach. Nie wszystkie z nich zapewniają obsługę architektury i narzędzi modelowania. W poniższej tabeli przedstawiono dostępność każdego narzędzia.

|**Funkcja**|**Wersja enterprise**|**Wydanie profesjonalne**|**Edycja społecznościowa**|
|-|-|-|-|
|**Mapy kodu**|Tak|Obsługuje tylko czytanie map kodu, filtrowanie map kodu, dodawanie nowych węzłów ogólnych i tworzenie nowego wykresu kierowanego z zaznaczenia.|-|
|**Diagramy zależności**|Tak|Obsługuje tylko odczyt diagramów zależności.|Obsługuje tylko odczyt diagramów zależności.|
|**Wykresy skierowane (diagramy** DGML)|Tak|Tak|Tak|
|**Klon kodu**|Tak|-|-|
