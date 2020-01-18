---
title: Rozpoczynanie tworzenia rozszerzeń programu Visual Studio | Microsoft Docs
ms.date: 09/18/2017
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 63fa0db72a01ddf1f6e1003fc27cf6a28128e036
ms.sourcegitcommit: e3c3d2b185b689c5e32ab4e595abc1ac60b6b9a8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2020
ms.locfileid: "76269129"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Rozpoczynanie tworzenia rozszerzeń Visual Studio

Jeśli wcześniej nie zapisano rozszerzenia programu Visual Studio, prawdopodobnie masz pewne pytania. Poniżej wymieniono niektóre z najpopularniejszych. Jeśli nie widzisz szukanych informacji, użyj przycisków opinii (**czy ta strona była pomocna?** w dolnej części ekranu), aby dowiedzieć się, co chcesz zrobić.

> [!NOTE]
> Ten artykuł ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [rozszerzanie Visual Studio dla komputerów Mac](/visualstudio/mac/extending-visual-studio-mac). Aby uzyskać Visual Studio Code, zobacz [Visual Studio Code rozszerzenia interfejsu API](https://code.visualstudio.com/api).

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Jakie oprogramowanie jest potrzebne do opracowania rozszerzeń programu Visual Studio?

Aby tworzyć rozszerzenia programu Visual Studio, należy zainstalować zestaw SDK programu Visual Studio oprócz programu Visual Studio. Zestaw Visual Studio SDK można zainstalować w ramach zwykłej konfiguracji. można też zainstalować go później. Aby uzyskać więcej informacji na temat instalowania zestawu Visual Studio SDK, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Jakiego rodzaju rzeczy można zrobić za pomocą rozszerzeń programu Visual Studio?

Limit czasu dla przestrzeni powietrznej, który jest dostępny do urojonia różnych rozszerzeń programu Visual Studio. Oczywiście większość rozszerzeń ma coś do wykonania w przypadku pisania kodu, ale nie musi to mieć znaczenia. Poniżej przedstawiono kilka przykładów typów rozszerzeń, które można skompilować:

- Obsługa języków, które nie znajdują się w programie Visual Studio, z kolorami składni, technologią IntelliSense i obsługą kompilatora i debugowania

- Narzędzia do zwiększania produktywności, które zwiększają podstawowe środowisko IDE dzięki dodatkowym szablonom, refaktoryzacji kodu, nowym dialogom lub oknach narzędzi

- Projektantów specyficznych dla domeny na potrzeby scenariuszy, takich jak projektowanie danych lub obsługa chmury

Przykłady rozszerzeń można znaleźć w [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Wiele rozszerzeń jest otwartych źródeł, a witryna Marketplace zawiera linki do repozytorium GitHub.

## <a name="which-visual-studio-features-can-i-extend"></a>Które funkcje programu Visual Studio można rozciągnąć?

Teoretycznie można przystąpić tylko do dowolnej części programu Visual Studio: menu, paski narzędzi, polecenia, okna, rozwiązania, projekty, Edytory i tak dalej.

W tej sprawie znaleźliśmy, że funkcje, które większość osób chce zwiększyć, to polecenia, menu i paski narzędzi, Windows, IntelliSense i projekty. Poniżej znajdują się linki do odpowiednich sekcji:

- [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md): Dodaj własne elementy do menu i pasków narzędzi programu Visual Studio. Można ich używać do uruchamiania nowych funkcji programu Visual Studio lub własnych zewnętrznych aplikacji pomocniczych. Możesz również udostępnić niestandardowe skróty dla elementów menu.

- [Rozszerzanie i dostosowywanie okien narzędzi](../extensibility/extending-and-customizing-tool-windows.md): rozszerzanie istniejących okien narzędzi lub tworzenie własnych okien narzędzi. Na przykład można dodać nowe właściwości do **Właściwości**lub utworzyć nowe okno narzędzi, aby dodać dodatkowe funkcje.

- [Rozszerzenia edytora i usługi językowej](../extensibility/editor-and-language-service-extensions.md): Dodaj własne dostosowania do funkcji IntelliSense dostarczonej dla języków programu Visual Studio lub Utwórz obsługę nowych języków programowania. Można tworzyć nowe uzupełniania instrukcji, sugestie i nowe etykietki narzędzi sekcji szybkich informacji. Żarówki umożliwiają dodawanie sugestii refaktoryzacji i poprawek kodu do obsługi nowych języków programowania.

- [Rozszerzanie projektów](../extensibility/extending-projects.md)

- [Rozszerzanie opcji i ustawień użytkownika](../extensibility/extending-user-settings-and-options.md)

- [Rozszerzanie właściwości i okno właściwości](../extensibility/extending-properties-and-the-property-window.md)

- [Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)

- [Visual Studio Isolated Shell](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

## <a name="BKMK_ProjectTemplate"></a>Jakie szablony projektów są udostępniane przez VSSDK?
 Dwa główne typy rozszerzeń to rozszerzenia pakietów VSPackage i MEF. Ogólnie rzecz biorąc, rozszerzenia pakietu VSPackage są używane dla rozszerzeń, które używają lub rozszerzają polecenia, okna narzędzi i projekty. Rozszerzenia MEF służą do rozszerzania lub dostosowywania edytora programu Visual Studio.

 W przypadku C# rozszerzeń wizualizacji i Visual Basic, VSSDK zawiera pusty szablon projektu VSIX, którego można użyć razem z szablonami nowych elementów, które tworzą polecenia menu, okna narzędzi i rozszerzenia edytora. Tego szablonu można również użyć do spakowania szablonów projektu, fragmentów kodu i innych artefaktów do dystrybucji dla innych użytkowników.

 W C++przypadku programu Kreator pakietu VSPackage udostępnia kod umożliwiający Dodawanie poleceń menu, okien narzędzi i edytorów niestandardowych.

 Szablon powłoki izolowanej służy do pakowania rozszerzenia w wersji powłoki programu Visual Studio, którą można oznakować i rozpowszechniać jako własne. W poniższych tematach pokazano, jak rozpocząć pracę z każdym rodzajem rozszerzenia:

- Polecenia menu: [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md)

- Okna narzędzi: [Tworzenie rozszerzenia przy użyciu okna narzędzi](../extensibility/creating-an-extension-with-a-tool-window.md)

- Rozszerzenia edytora: [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- Podstawowa pakietów VSPackage: [Tworzenie rozszerzenia za pomocą pakietu VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

- Szablon projektu VSIX: [wprowadzenie z szablonem projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Jak mogę Uzyskaj moje rozszerzenie, aby wyglądało jak Visual Studio?
 Uzyskaj doskonałe wskazówki dotyczące projektowania interfejsu użytkownika dla rozszerzenia w [wytycznych dotyczących środowiska użytkownika programu Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="where-can-i-find-examples-of-vssdk-code"></a>Gdzie mogę znaleźć przykłady kodu VSSDK?
 Wszystkie linki wymienione w poprzedniej sekcji zawierają przewodnik krok po kroku pokazujący sposób implementacji określonych funkcji. Przykłady VSSDK Open Source można znaleźć w witrynie GitHub w [przykładach programu Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="how-can-i-distribute-my-extension"></a>Jak mogę rozpowszechnić rozszerzenie?
 Możesz zainstalować rozszerzenie na innym komputerze lub wysłać je do znajomych jako plik. vsix, który instalujesz, klikając go dwukrotnie. Więcej informacji o pakietach VSIX można znaleźć podczas [wysyłania rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Możesz również opublikować swoje rozszerzenie na Visual Studio Marketplace, co sprawia, że jest widoczne dla dużej liczby klientów programu Visual Studio. Przykład pakowania rozszerzenia do portalu Marketplace zawiera [Przewodnik: Publikowanie rozszerzenia programu Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Aby uzyskać więcej informacji o tym, co należy zrobić w celu opublikowania w portalu Marketplace, zobacz [produkty i rozszerzenia dla programu Visual Studio](/azure/devops/extend/overview?view=vsts).

## <a name="see-also"></a>Zobacz także

- [Rozszerzenie programu Visual Studio dla komputerów Mac](/visualstudio/mac/extending-visual-studio-mac)
- [Rozszerzanie Visual Studio Code](https://code.visualstudio.com/api)
