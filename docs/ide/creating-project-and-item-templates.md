---
title: Szablony projektów i plików
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 30a20e5810d5c361fddf8cd934863fcb1186b5d0
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58415957"
---
# <a name="project-and-item-templates"></a>Szablony projektów i elementów

Szablony projektów i elementów zapewniają do ponownego użycia udostępniające użytkownikom podstawowy kod i struktury, które można dostosowywać do własnych celów.

## <a name="visual-studio-templates"></a>szablony Visual Studio

Liczba szablonów elementów i projektów wstępnie zdefiniowane są instalowane z programem Visual Studio. Te szablony, takie jak **aplikacji sieci Web ASP.NET** i **biblioteki klas** szablony są dostępne do wyboru podczas tworzenia nowego projektu. Szablony elementów, takich jak pliki kodu, plików XML, strony HTML i arkusze stylów, są wyświetlane w **Dodaj nowy element** okna.

Te szablony zapewniają punkt wyjścia dla użytkowników, aby rozpocząć tworzenie projektów lub rozszerzania istniejących projektów. Szablony projektów dostarczają pliki, które są wymagane dla określonego typu projektu, zawierają odwołania do standardowego zestawu i ustawiają domyślne opcje kompilatora i właściwości projektu. Szablonów elementów może mieścić się stopnia skomplikowania z jednego pustego pliku, który ma określone rozszerzenie pliku, wielu plików kodu źródłowego z kodem skróconym, informacje o projektancie plików i zasoby osadzone.

Można użyć zainstalowanych szablonów, tworzyć własne niestandardowe szablony lub pobrać i używać szablonów utworzonych przez społeczność. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md) i [jak: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Zawartość szablonu

Wszystkie szablony projektów i elementów, czy zainstalowany za pomocą programu Visual Studio lub utworzone przez użytkownika, funkcję za pomocą tych samych zasad i spisu treści. Wszystkie szablony zawierają następujące elementy:

- Pliki, które można utworzyć, jeśli jest używany szablon. Te pliki obejmują pliki kodu źródłowego, zasobów osadzonych, plików projektu i tak dalej.

::: moniker range="vs-2017"

- A *.vstemplate* pliku, który zawiera metadane potrzebne do tworzenia projektu lub elementu z szablonu i wyświetlić szablon w **nowy projekt** i **Dodaj nowy element** dla systemu Windows.

::: moniker-end

::: moniker range=">=vs-2019"

- A *.vstemplate* pliku, który zawiera metadane potrzebne do tworzenia projektu lub elementu z szablonu i wyświetlić szablon na **Utwórz nowy projekt** strony lub **Dodaj nowy element** okno dialogowe.

::: moniker-end

   Aby uzyskać więcej informacji na temat *.vstemplate* plików, zobacz [parametry szablonu](../ide/template-parameters.md).

Jeśli te pliki są kompresowane do *zip* pliku i umieścić w odpowiednim folderze, Visual Studio automatycznie wyświetli je w następujących miejscach:

::: moniker range="vs-2017"

- Szablony projektów są wyświetlane w **nowy projekt** okna.

::: moniker-end

::: moniker range=">=vs-2019"

- Szablony projektu pojawiają się na **Utwórz nowy projekt** strony.

::: moniker-end

- Szablony elementu są wyświetlane w **Dodaj nowy element** okna.

Aby uzyskać więcej informacji na temat folderów szablonów, zobacz [jak: Lokalizowanie i organizacja szablonów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md)
- [Instrukcje: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Pakiety NuGet w szablonach programu Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)