---
title: Nowości dotyczące projektowania
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- what's new [VIsual Studio ALM], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio ALM], What's New
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bdea0b8e24347e608ad0e1736b55e34acb4e5854
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53956026"
---
# <a name="whats-new-for-design-in-visual-studio"></a>Co nowego w dziedzinie projektowania w programie Visual Studio

## <a name="live-dependency-validation"></a>Weryfikacja zależności na żywo

Usunięcie niechcianych zależności jest ważną częścią zarządzania Twojej długu technicznego. Na żywo weryfikacji zależności jest teraz dołączone, zapewniając dokładne informacje o problemach i pełni korzystanie z nowych funkcji w edytorze i lista błędów.

![Weryfikacja zależności na żywo w działaniu](media/dep-validation-whatsnew-01.png)

Środowisko tworzenia zmienił się weryfikacji zależności mogą szybciej odnajdywać i bardziej dostępny, zmiana terminologii z "Diagramu warstwowego" do "Diagram zależności".

**Architektury** menu zawiera teraz polecenia, aby bezpośrednio utworzyć diagram zależności:

![Element zależności na żywo w menu architektury](media/dep-validation-whatsnew-02.png)

... i nazwy właściwości warstwy w diagram zależności i ich opisy, zostały zmienione, aby były bardziej zrozumiały:

![Nazwy właściwości zależności na żywo zaktualizowane](media/dep-validation-whatsnew-03.png)

Zobaczysz teraz wpływ zmian bezpośrednio w wynikach analizy dla bieżącego kodu w rozwiązaniu każdorazowo, gdy zapisać diagram. Nie trzeba już czekać na zakończenie polecenia "Weryfikacji zależności".

Aby uzyskać więcej informacji, zobacz [ten wpis w blogu](https://blogs.msdn.microsoft.com/devops/2016/10/07/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

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

Aby uzyskać więcej informacji, zobacz [ten wpis w blogu](https://blogs.msdn.microsoft.com/devops/2016/10/14/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="a-nameversionsupport-edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Obsługa wersji narzędzia architektury i modelowania

Visual Studio 2017 jest dostępny w wielu wersjach. Nie wszystkie te zapewniają obsługę architekturę i narzędzia do modelowania. W poniższej tabeli przedstawiono Dostępność poszczególnych narzędzi.

|**Funkcja**|**Wersja Enterprise**|**W wersji Professional**|**Wersja Community edition**|
|-|-|-|-|
|**Mapy kodu**|Tak|Mapy tylko filtrowania kodu obsługuje map kodu do czytania, dodawanie nowych węzłów ogólny i tworzenie nowy Graf skierowany z zaznaczenia.|-|
|**Diagramów zależności**|Tak|Obsługuje tylko odczytywanie diagramów zależności.|Obsługuje tylko odczytywanie diagramów zależności.|
|**Ukierunkowanych wykresów** (diagramy DGML)|Tak|Yes|Tak|
|**Klonowanie kodu**|Tak|-|-|