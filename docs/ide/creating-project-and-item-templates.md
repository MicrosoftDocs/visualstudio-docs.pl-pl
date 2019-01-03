---
title: Szablony projektów i plików
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 276a670356acafcb17d644aa8b524a0138232158
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53849784"
---
# <a name="project-and-item-templates"></a>Szablony projektów i elementów

Szablony projektów i elementów zapewniają do ponownego użycia udostępniające użytkownikom podstawowy kod i struktury, które można dostosowywać do własnych celów.

## <a name="visual-studio-templates"></a>szablony Visual Studio

Liczba szablonów elementów i projektów wstępnie zdefiniowane są instalowane z programem Visual Studio. Na przykład, Visual Basic i C# **Windows Forms App** i **biblioteki klas** szablonów, które są wyświetlane w **nowy projekt** okno dialogowe są szablony projektów. Pozycja Pokaż szablony w **Dodaj nowy element** okna dialogowego i zawierają elementy, takie jak pliki kodu, plików XML, strony HTML i arkusze stylów.

Te szablony zapewniają punkt wyjścia dla użytkowników, aby rozpocząć tworzenie projektów lub rozszerzania istniejących projektów. Szablony projektów dostarczają pliki, które są wymagane dla określonego typu projektu, zawierają odwołania do standardowego zestawu i ustawiają domyślne opcje kompilatora i właściwości projektu. Szablonów elementów może mieścić się stopnia skomplikowania z jednego pustego pliku, który ma określone rozszerzenie pliku, wielu plików kodu źródłowego z kodem skróconym, informacje o projektancie plików i zasoby osadzone.

Możesz użyć zainstalowanych szablonów w **nowy projekt** i **Dodaj nowy element** okien dialogowych, tworzyć własne szablony lub pobrać i używać szablonów utworzonych przez społeczność. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md) i [jak: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Zawartość szablonu

Wszystkie szablony projektów i elementów, czy zainstalowany za pomocą programu Visual Studio lub utworzone przez użytkownika, funkcję za pomocą tych samych zasad i spisu treści. Wszystkie szablony zawierają następujące elementy:

- Pliki, które można utworzyć, jeśli jest używany szablon. Te pliki obejmują pliki kodu źródłowego, zasobów osadzonych, plików projektu i tak dalej.

- Jeden *.vstemplate* zawierający metadane potrzebne do wyświetlenia szablonu w **nowy projekt** i **Dodaj nowy element** okna dialogowe i umożliwia utworzenie projektu lub elementu z szablon. Aby uzyskać więcej informacji na temat *.vstemplate* plików, zobacz [parametry szablonu](../ide/template-parameters.md).

Jeśli te pliki są kompresowane do *zip* pliku i umieścić w odpowiednim folderze, Visual Studio automatycznie wyświetli je w następujących miejscach:

- Szablony projektów są wyświetlane w **nowy projekt** okno dialogowe.

- Szablony elementu są wyświetlane w **Dodaj nowy element** okno dialogowe.

Aby uzyskać więcej informacji na temat folderów szablonów, zobacz [jak: Lokalizowanie i organizacja szablonów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md)
- [Instrukcje: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Pakiety NuGet w szablonach programu Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)