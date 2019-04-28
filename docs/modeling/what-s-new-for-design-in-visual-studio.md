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
ms.openlocfilehash: fb7ef710d117318d475e32f19b5ca2511b94f8bc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63386924"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Co nowego w dziedzinie projektowania w programie Visual Studio 2017

## <a name="live-dependency-validation"></a>Weryfikacja zależności na żywo

Usunięcie niechcianych zależności jest ważną częścią zarządzania Twojej długu technicznego. Na żywo weryfikacji zależności jest teraz dołączone, zapewniając dokładne informacje o problemach i pełni korzystanie z nowych funkcji w edytorze i lista błędów.

![Weryfikacja zależności na żywo w działaniu](media/dep-validation-whatsnew-01.png)

Środowisko tworzenia zmienił się weryfikacji zależności mogą szybciej odnajdywać i bardziej dostępny, zmiana terminologii z "Diagramu warstwowego" do "Diagram zależności".

**Architektury** menu zawiera teraz polecenia, aby bezpośrednio utworzyć diagram zależności:

![Element zależności na żywo w menu architektury](media/dep-validation-whatsnew-02.png)

... i nazwy właściwości warstwy w diagram zależności i ich opisy, zostały zmienione, aby były bardziej zrozumiały:

![Nazwy właściwości zależności na żywo zaktualizowane](media/dep-validation-whatsnew-03.png)

Zobaczysz teraz wpływ zmian bezpośrednio w wynikach analizy dla bieżącego kodu w rozwiązaniu każdorazowo, gdy zapisać diagram. Nie trzeba już czekać na zakończenie polecenia "Weryfikacji zależności".

Aby uzyskać więcej informacji, zobacz [ten wpis w blogu](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Usunięto projektantów UML

Projektantów UML zostały usunięte z tej wersji programu Visual Studio Enterprise.

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

Jednak pomoc techniczna dotycząca wizualizacja architektury kodu .NET i C++ jest dostępna za pośrednictwem [map kodu](map-dependencies-across-your-solutions.md)i znaczne ulepszenia do weryfikacji zależności opisane powyżej.

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