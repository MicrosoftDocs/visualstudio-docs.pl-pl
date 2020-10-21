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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "92299509"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Co nowego w dziedzinie projektowania w programie Visual Studio 2017

## <a name="live-dependency-validation"></a>Walidacja aktywnej zależności

Usuwanie niechcianych zależności jest ważną częścią zarządzania długiem technicznym. Program Visual Studio zapewnia dynamiczną weryfikację zależności, w tym dokładne informacje o problemach, takich jak lokalizacja ich lokalizacji. Weryfikacja zależności na żywo ma pełne zalety nowych funkcji w Lista błędów i edytorze.

![Weryfikacja zależności na żywo w akcji](media/dep-validation-whatsnew-01.png)

Środowisko autorskie zostało zmienione w celu ułatwienia odnajdywania i bardziej dostępności weryfikacji zależności. Terminologia została zmieniona z "diagram warstwowy" na "diagram zależności".

Menu **Architektura** zawiera teraz polecenie umożliwiające bezpośrednie utworzenie diagramu zależności:

![Aktywny element zależności w menu architektura](media/dep-validation-whatsnew-02.png)

Nazwy i opisy właściwości warstwy zostały zmienione, aby zwiększyć ich czytelność:

![Nazwy właściwości zaktualizowanej zależności na żywo](media/dep-validation-whatsnew-03.png)

Od razu zobaczysz wpływ zmian w wynikach analizy dla bieżącego kodu w rozwiązaniu przy każdym zapisaniu diagramu. Nie musisz czekać na ukończenie polecenia **Weryfikuj zależności** .

Aby uzyskać więcej informacji, zobacz [ten wpis w blogu](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Projektanci UML zostali usunięci

Projektanci UML zostali usunięci z programu Visual Studio.

* Diagramy UML są teraz prezentowane jako pliki XML
* Eksplorator modelu UML już nie istnieje
* Odwołania do projektu modelowania nie są już używane na potrzeby walidacji zależności
* Węzeł "odwołania do warstwy" w Eksplorator rozwiązań nie jest już wyświetlany
* Akcja kompilacji "Validate" na diagramie zależności (warstwy) nie jest już używana — zadanie kompilacji zostało usunięte
* Struktura projektu jest utrzymywana do dwustronnego wyłączania między wersjami
* Nadal można otwierać, tworzyć, edytować i zapisywać zależności (warstwy) jako XML
* Elementy robocze TFS połączone z diagramem zależności (warstwy) nie są dostępne na powierzchni projektowej
* Łączenie z powrotem z do języka DSL lub warstwy nie jest już obsługiwane
* Rozszerzalność UML w zestawie SDK modelowania nie jest już obsługiwana

Obsługa wizualizacji architektury .NET i kodu C++ jest dostępna za pomocą [map kodu](map-dependencies-across-your-solutions.md).

Jeśli jesteś znaczącym użytkownikiem projektantów UML, możesz nadal korzystać z programu Visual Studio 2015 lub wcześniejszych wersji, gdy zdecydujesz się na alternatywne narzędzia dla potrzeb UML.

Aby uzyskać więcej informacji, zobacz [ten wpis w blogu](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Obsługa wersji dla architektury i narzędzi modelowania

Program Visual Studio jest dostępny w kilku wersjach. Nie wszystkie z nich zapewniają obsługę architektury i narzędzi modelowania. W poniższej tabeli przedstawiono dostępność każdego narzędzia.

|**Funkcja**|**Wersja Enterprise**|**Wersja Professional**|**Wersja Community**|
|-|-|-|-|
|**Mapy kodu**|Tak|Obsługuje tylko odczytywanie map kodu, filtrowanie map kodu, dodawanie nowych węzłów ogólnych i tworzenie nowego ukierunkowanego wykresu na podstawie zaznaczenia.|-|
|**Diagramy zależności**|Tak|Obsługuje tylko odczytywanie diagramów zależności.|Obsługuje tylko odczytywanie diagramów zależności.|
|**Wykresy ukierunkowane** (diagramy dgml)|Tak|Tak|Tak|
|**Klonowanie kodu**|Tak|-|-|
