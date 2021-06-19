---
title: Co nowego w dziedzinie projektowania w programie Visual Studio 2017
description: Dowiedz się więcej o nowych funkcjach projektowania kodu, takich jak weryfikacja zależności na żywo, które są dostępne w Visual Studio 2017 r.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: ed67836507d8328a4ba394986564820c6af7308f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388103"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Co nowego w dziedzinie projektowania w programie Visual Studio 2017

## <a name="live-dependency-validation"></a>Weryfikacja zależności na żywo

Usuwanie niechcianych zależności jest ważną częścią zarządzania długiem technicznym. Visual Studio zapewnia weryfikację zależności na żywo, w tym dokładne informacje o problemach, takie jak ich zlokalizowanie. Walidacja zależności na żywo w pełni wykorzystuje nowe funkcje na liście błędów i w edytorze.

![Walidacja zależności na żywo w działaniu](media/dep-validation-whatsnew-01.png)

Środowisko tworzenia zostało zmienione, aby walidacja zależności była bardziej wykrywalna i bardziej dostępna. Terminologia została zmieniona z "Diagram warstwowy" na "Diagram zależności".

Menu **Architektura** zawiera teraz polecenie , które umożliwia bezpośrednie utworzenie diagramu zależności:

![Element zależności na żywo w menu Architektura](media/dep-validation-whatsnew-02.png)

Nazwy i opisy właściwości warstw zostały zmienione, aby były bardziej zrozumiałe:

![Zaktualizowane nazwy właściwości zależności na żywo](media/dep-validation-whatsnew-03.png)

Po każdym zapisaniu diagramu natychmiast zobaczysz wpływ zmian w wynikach analizy dla bieżącego kodu w rozwiązaniu. Nie musisz czekać na ukończenie polecenia **Validate Dependencies** (Weryfikuj zależności).

Aby uzyskać więcej informacji, zobacz [ten wpis w blogu](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Projektanci UML zostały usunięci

Projektanci UML zostały usunięci z Visual Studio.

* Diagramy UML są teraz prezentowane jako pliki XML
* Eksplorator modeli UML już nie istnieje
* Odwołania do projektu modelowania nie są już używane do walidacji zależności
* Węzeł "Odwołania do warstwy" w Eksplorator rozwiązań nie jest już wyświetlany
* Akcja kompilacji "Weryfikuj" na diagramie zależności (warstwy) nie jest już używana — zadanie kompilacji zostało usunięte
* Struktura projektu jest utrzymywana w celu rundy między wersjami
* Nadal można otwierać, tworzyć, edytować i zapisywać diagram zależności (warstwa) jako XML
* Elementy robocze TFS połączone z diagramem zależności (warstwa) nie są dostępne na powierzchni projektowej
* Back linking from to DSL or a Layer is no longer supported (Łączenie z powrotem z dsl lub warstwy nie jest już obsługiwane)
* Rozszerzalność UML w zestawie SDK modelowania nie jest już obsługiwana

Obsługa wizualizacji architektury kodu .NET i C++ jest dostępna za pośrednictwem [map kodu](map-dependencies-across-your-solutions.md).

Jeśli jesteś znaczącym użytkownikiem projektantów UML, możesz nadal korzystać z wersji Visual Studio 2015 lub starszych, podczas gdy ty decydujesz się na alternatywne narzędzie do potrzeb UML.

Aby uzyskać więcej informacji, zobacz [ten wpis w blogu](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Obsługa wersji dla architektury i narzędzi do modelowania

Visual Studio jest dostępna w kilku wersjach. Nie wszystkie z nich zapewniają obsługę architektury i narzędzi do modelowania. W poniższej tabeli przedstawiono dostępność każdego narzędzia.

|**Funkcja**|**Wersja Enterprise**|**Wersja Professional**|**Community Edition**|
|-|-|-|-|
|**Mapy kodu**|Tak|Obsługuje tylko odczytywanie map kodu, filtrowanie map kodu, dodawanie nowych węzłów ogólnych i tworzenie nowego grafu bezpośredniego z zaznaczenia.|-|
|**Diagramy zależności**|Tak|Obsługuje tylko odczytywanie diagramów zależności.|Obsługuje tylko odczytywanie diagramów zależności.|
|**Wykresy skierowane** (diagramy DGML)|Tak|Tak|Tak|
|**Klonowanie kodu**|Tak|-|-|
