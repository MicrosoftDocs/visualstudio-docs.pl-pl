---
title: Szablony projektów i plików
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 2cc932a2407aeb4951bab970a0edc6e2b2a5fcc9
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409049"
---
# <a name="project-and-item-templates"></a>Szablony projektów i elementów

Szablony projektów i elementów zapewniają do ponownego użycia udostępniające użytkownikom podstawowy kod i struktury, które można dostosowywać do własnych celów.

## <a name="visual-studio-templates"></a>szablony Visual Studio

Liczba szablonów elementów i projektów wstępnie zdefiniowane są instalowane z programem Visual Studio. Te szablony, takie jak **ASP.NET aplikacji sieci Web** i szablonów **bibliotek klas** , są dostępne do wyboru podczas tworzenia nowego projektu. Szablony elementów, takie jak pliki kodu, pliki XML, strony HTML i arkusze stylów, są wyświetlane w oknie **Dodaj nowy element** .

Te szablony zapewniają punkt wyjścia dla użytkowników, aby rozpocząć tworzenie projektów lub rozszerzania istniejących projektów. Szablony projektów dostarczają pliki, które są wymagane dla określonego typu projektu, zawierają odwołania do standardowego zestawu i ustawiają domyślne opcje kompilatora i właściwości projektu. Szablonów elementów może mieścić się stopnia skomplikowania z jednego pustego pliku, który ma określone rozszerzenie pliku, wielu plików kodu źródłowego z kodem skróconym, informacje o projektancie plików i zasoby osadzone.

Możesz korzystać z zainstalowanych szablonów, tworzyć własne szablony niestandardowe lub pobierać i używać szablonów utworzonych przez społeczność. Aby uzyskać więcej informacji, zobacz [How to: Create Project Templates](../ide/how-to-create-project-templates.md) and [How to: Create Item templates](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Zawartość szablonu

Wszystkie szablony projektów i elementów, czy zainstalowany za pomocą programu Visual Studio lub utworzone przez użytkownika, funkcję za pomocą tych samych zasad i spisu treści. Wszystkie szablony zawierają następujące elementy:

- Pliki, które można utworzyć, jeśli jest używany szablon. Te pliki obejmują pliki kodu źródłowego, zasobów osadzonych, plików projektu i tak dalej.

::: moniker range="vs-2017"

- Plik *. vstemplate* , który zawiera metadane, które są konieczne do utworzenia projektu lub elementu z szablonu oraz wyświetlanie szablonu w **nowym projekcie** i **Dodawanie okien nowego elementu** .

::: moniker-end

::: moniker range=">=vs-2019"

- Plik *. vstemplate* , który zawiera metadane, które są konieczne do utworzenia projektu lub elementu z szablonu i wyświetlenia szablonu na stronie **Utwórz nowy projekt** lub w oknie dialogowym **Dodaj nowy element** .

::: moniker-end

   Aby uzyskać więcej informacji na temat plików *. vstemplate* , zobacz [Tagi szablonów](template-tags.md) i [Parametry szablonu](../ide/template-parameters.md).

Gdy te pliki są kompresowane do pliku *zip* i umieszczane w prawidłowym folderze, program Visual Studio automatycznie wyświetli je w następujących miejscach:

::: moniker range="vs-2017"

- Szablony projektu są wyświetlane w oknie **Nowy projekt** .

::: moniker-end

::: moniker range=">=vs-2019"

- Szablony projektu są wyświetlane na stronie **Utwórz nowy projekt** .

::: moniker-end

- Szablony elementów są wyświetlane w oknie **Dodaj nowy element** .

Aby uzyskać więcej informacji na temat folderów szablonów, zobacz [How to: Lokalizowanie i organizowanie szablonów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Tworzenie szablonów projektu](../ide/how-to-create-project-templates.md)
- [Instrukcje: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)
- [Tagi szablonu](template-tags.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Pakiety NuGet w szablonach programu Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
