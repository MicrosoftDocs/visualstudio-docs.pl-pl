---
title: Szablony dla projektów i plików
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301952"
---
# <a name="project-and-item-templates"></a>Szablony projektów i elementów

Szablony projektów i elementów zapewniają wycinki wielokrotnego użytku, które zapewniają użytkownikom podstawowy kod i strukturę, które mogą dostosować do własnych celów.

## <a name="visual-studio-templates"></a>szablony Visual Studio

W programie Visual Studio jest instalowanych wiele wstępnie zdefiniowanych szablonów projektów i elementów. Te szablony, takie jak **ASP.NET szablony aplikacji sieci Web** i **biblioteki klas,** są dostępne do wyboru podczas tworzenia nowego projektu. Szablony elementów, takie jak pliki kodu, pliki XML, strony HTML i Arkusze stylów, są wyświetlane w oknie **Dodawanie nowego elementu.**

Szablony te stanowią punkt wyjścia dla użytkowników, aby rozpocząć tworzenie projektów lub rozwinąć istniejące projekty. Szablony projektów dostarczają pliki, które są wymagane dla określonego typu projektu, zawierają odwołania do standardowego zestawu i ustawiają domyślne opcje kompilatora i właściwości projektu. Szablony elementów mogą składać się ze złożoności od pojedynczego pustego pliku, który ma określone rozszerzenie pliku, do wielu plików kodu źródłowego z kodem skrótowym, plików informacji projektanta i zasobów osadzonych.

Możesz użyć zainstalowanych szablonów, tworzyć własne szablony niestandardowe lub pobierać i używać szablonów utworzonych przez społeczność. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md) i [Jak: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Zawartość szablonu

Wszystkie szablony projektu i elementów, czy zainstalowane w programie Visual Studio lub utworzone przez Ciebie, działają przy użyciu tych samych zasad i mają podobną zawartość. Wszystkie szablony zawierają następujące elementy:

- Pliki, które można utworzyć, jeśli jest używany szablon. Pliki te obejmują pliki kodu źródłowego, zasoby osadzone, pliki projektu i tak dalej.

::: moniker range="vs-2017"

- Plik *vstemplate,* który zawiera metadane potrzebne do utworzenia projektu lub elementu z szablonu i wyświetlania szablonu w oknach **Nowy projekt** i Dodaj nowy **element.**

::: moniker-end

::: moniker range=">=vs-2019"

- Plik *vstemplate,* który zawiera metadane potrzebne do utworzenia projektu lub elementu z szablonu i wyświetlania szablonu na stronie **Tworzenie nowego projektu** lub w oknie dialogowym Dodawanie nowego **elementu.**

::: moniker-end

   Aby uzyskać więcej informacji o plikach *vstemplate,* zobacz [Znaczniki szablonów](template-tags.md) i [parametry szablonu](../ide/template-parameters.md).

Gdy te pliki są skompresowane do pliku *zip* i umieszczone w odpowiednim folderze, program Visual Studio automatycznie wyświetla je w następujących miejscach:

::: moniker range="vs-2017"

- Szablony projektów są wyświetlane w oknie **Nowy projekt.**

::: moniker-end

::: moniker range=">=vs-2019"

- Szablony projektów są wyświetlane na stronie **Tworzenie nowego projektu.**

::: moniker-end

- Szablony elementów są wyświetlane w oknie **Dodaj nowy element.**

Aby uzyskać więcej informacji o folderach szablonów, zobacz [Jak: Lokalizowanie i organizowanie szablonów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Zobacz też

- [Jak: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md)
- [Jak: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)
- [Tagi szablonów](template-tags.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Pakiety NuGet w szablonach programu Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
