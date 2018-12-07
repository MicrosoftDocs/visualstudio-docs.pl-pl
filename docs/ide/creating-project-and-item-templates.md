---
title: Szablony projektów i plików
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 04aa647d378e956c7a2394b7c3fc2a187a7c5963
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049288"
---
# <a name="project-and-item-templates"></a>Szablony projektów i elementów

Szablony projektów i elementów zapewniają do ponownego użycia udostępniające użytkownikom podstawowy kod i struktury, które można dostosowywać do własnych celów.

## <a name="visual-studio-templates"></a>szablony Visual Studio

Liczba szablonów elementów i projektów wstępnie zdefiniowane są instalowane z programem Visual Studio. Na przykład, Visual Basic i C# **Windows Forms App** i **biblioteki klas** szablonów, które są wyświetlane w **nowy projekt** okno dialogowe są szablony projektów. Pozycja Pokaż szablony w **Dodaj nowy element** okna dialogowego i zawierają elementy, takie jak pliki kodu, plików XML, strony HTML i arkusze stylów.

Te szablony zapewniają punkt wyjścia dla użytkowników, aby rozpocząć tworzenie projektów lub rozszerzania istniejących projektów. Szablony projektów dostarczają pliki, które są wymagane dla określonego typu projektu, zawierają odwołania do standardowego zestawu i ustawiają domyślne opcje kompilatora i właściwości projektu. Szablonów elementów może mieścić się stopnia skomplikowania z jednego pustego pliku, który ma określone rozszerzenie pliku, wielu plików kodu źródłowego z kodem skróconym, informacje o projektancie plików i zasoby osadzone.

Możesz użyć zainstalowanych szablonów w **nowy projekt** i **Dodaj nowy element** okien dialogowych, tworzyć własne szablony lub pobrać i używać szablonów utworzonych przez społeczność. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md) i [porady: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Zawartość szablonu

Wszystkie szablony projektów i elementów, czy zainstalowany za pomocą programu Visual Studio lub utworzone przez użytkownika, funkcję za pomocą tych samych zasad i spisu treści. Wszystkie szablony zawierają następujące elementy:

- Pliki, które można utworzyć, jeśli jest używany szablon. Te pliki obejmują pliki kodu źródłowego, zasobów osadzonych, plików projektu i tak dalej.

- Jeden *.vstemplate* zawierający metadane potrzebne do wyświetlenia szablonu w **nowy projekt** i **Dodaj nowy element** okna dialogowe i umożliwia utworzenie projektu lub elementu z szablon. Aby uzyskać więcej informacji na temat *.vstemplate* plików, zobacz [parametry szablonu](../ide/template-parameters.md).

Jeśli te pliki są kompresowane do *zip* pliku i umieścić w odpowiednim folderze, Visual Studio automatycznie wyświetli je w następujących miejscach:

- Szablony projektów są wyświetlane w **nowy projekt** okno dialogowe.

- Szablony elementu są wyświetlane w **Dodaj nowy element** okno dialogowe.

Aby uzyskać więcej informacji na temat folderów szablonów, zobacz [porady: lokalizowanie i organizacja szablonów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Zobacz także

- [Porady: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md)
- [Porady: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Pakiety NuGet w szablonach programu Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)