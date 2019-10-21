---
title: Szablony projektów i plików
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1590317bf2749cc1aeef8a4c3bfbf2937c8404c7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652594"
---
# <a name="project-and-item-templates"></a>Szablony projektów i elementów

Szablony projektów i elementów udostępniają klasy wielokrotnego użytku, które zapewniają użytkownikom pewien podstawowy kod i strukturę, które można dostosować do własnych celów.

## <a name="visual-studio-templates"></a>szablony Visual Studio

Wiele wstępnie zdefiniowanych szablonów projektu i elementów jest instalowanych z programem Visual Studio. Te szablony, takie jak **ASP.NET aplikacji sieci Web** i szablonów **bibliotek klas** , są dostępne do wyboru podczas tworzenia nowego projektu. Szablony elementów, takie jak pliki kodu, pliki XML, strony HTML i arkusze stylów, są wyświetlane w oknie **Dodaj nowy element** .

Te szablony stanowią punkt wyjścia dla użytkowników, którzy rozpoczną tworzenie projektów lub rozwijają istniejące projekty. Szablony projektów dostarczają pliki, które są wymagane dla określonego typu projektu, zawierają odwołania do standardowego zestawu i ustawiają domyślne opcje kompilatora i właściwości projektu. Szablony elementów mogą być bardziej skomplikowane od pojedynczego pustego pliku, który ma określone rozszerzenie pliku, do wielu plików kodu źródłowego z kodem zastępczym, plików informacji projektanta i zasobów osadzonych.

Możesz korzystać z zainstalowanych szablonów, tworzyć własne szablony niestandardowe lub pobierać i używać szablonów utworzonych przez społeczność. Aby uzyskać więcej informacji, zobacz [How to: Create Project Templates](../ide/how-to-create-project-templates.md) and [How to: Create Item templates](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Zawartość szablonu

Wszystkie szablony projektów i elementów, niezależnie od tego, czy zostały zainstalowane z programem Visual Studio lub utworzone przez użytkownika, działają przy użyciu tych samych zasad i mają podobną zawartość. Wszystkie szablony zawierają następujące elementy:

- Pliki, które można utworzyć, jeśli jest używany szablon. Te pliki obejmują pliki kodu źródłowego, zasoby osadzone, pliki projektu i tak dalej.

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

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie szablonów projektu](../ide/how-to-create-project-templates.md)
- [Instrukcje: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)
- [Tagi szablonu](template-tags.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Pakiety NuGet w szablonach programu Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)