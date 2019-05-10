---
title: Co nowego w dziedzinie projektowania w programie Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: dc75c7414e0fff18f76d14f8f9a4e0779a9e7a2b
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476535"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Co nowego w dziedzinie projektowania w programie Visual Studio 2017

## <a name="live-dependency-validation"></a>Weryfikacja zależności na żywo

Usunięcie niechcianych zależności jest ważną częścią zarządzania Twojej długu technicznego. Program Visual Studio udostępnia na żywo weryfikacji zależności, w tym dokładne informacje na temat problemów, na przykład, gdzie się znajdują. Zależności na żywo weryfikacji przyjmuje pełne korzyści wynikające z nowych funkcji w edytorze i lista błędów.

![Weryfikacja zależności na żywo w działaniu](media/dep-validation-whatsnew-01.png)

Środowisko tworzenia zmienił się weryfikacji zależności mogą szybciej odnajdywać i łatwiej dostępne. Terminologii zmienił się z "Diagramu warstwowego" "Diagram zależności".

**Architektury** menu zawiera teraz polecenia, aby bezpośrednio utworzyć diagram zależności:

![Element zależności na żywo w menu architektury](media/dep-validation-whatsnew-02.png)

Warstwa właściwości nazwy i opisy zostały zmienione, aby były bardziej zrozumiały:

![Nazwy właściwości zależności na żywo zaktualizowane](media/dep-validation-whatsnew-03.png)

Możesz natychmiast zobaczyć wpływ zmian w wynikach analizy dla bieżącego kodu w rozwiązaniu każdorazowo, gdy zapisać diagram. Nie trzeba czekać na zakończenie **weryfikacji zależności** polecenia.

Aby uzyskać więcej informacji, zobacz [ten wpis w blogu](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Usunięto projektantów UML

Projektantów UML zostały usunięte z programu Visual Studio.

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

Obsługa wizualizacji architektury .NET i C++ kod jest dostępny za pośrednictwem [map kodu](map-dependencies-across-your-solutions.md).

Jeśli jesteś użytkownikiem znaczące projektantów UML, można nadal używać programu Visual Studio 2015 i jego wcześniejsze wersje podczas decyzję w sprawie narzędziem alternatywne do własnych potrzeb UML.

Aby uzyskać więcej informacji, zobacz [ten wpis w blogu](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="a-nameversionsupport-edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Obsługa wersji narzędzia architektury i modelowania

Program Visual Studio jest dostępna w wielu wersjach. Nie wszystkie te zapewniają obsługę architekturę i narzędzia do modelowania. W poniższej tabeli przedstawiono Dostępność poszczególnych narzędzi.

|**Funkcja**|**Wersja Enterprise**|**W wersji Professional**|**Wersja Community edition**|
|-|-|-|-|
|**Mapy kodu**|Tak|Mapy tylko filtrowania kodu obsługuje map kodu do czytania, dodawanie nowych węzłów ogólny i tworzenie nowy Graf skierowany z zaznaczenia.|-|
|**Diagramów zależności**|Tak|Obsługuje tylko odczytywanie diagramów zależności.|Obsługuje tylko odczytywanie diagramów zależności.|
|**Ukierunkowanych wykresów** (diagramy DGML)|Tak|Yes|Tak|
|**Klonowanie kodu**|Tak|-|-|