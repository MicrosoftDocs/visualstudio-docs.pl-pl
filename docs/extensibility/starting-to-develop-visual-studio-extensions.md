---
title: Rozpoczęcie opracowywania rozszerzeń programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 09/18/2017
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 744475e61458f7b91ce08fba4d17046df36f5558
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699738"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Rozpoczynanie tworzenia rozszerzeń Visual Studio

Jeśli nigdy wcześniej nie napisałeś rozszerzenia programu Visual Studio, prawdopodobnie masz kilka pytań. Wymieniliśmy tu niektóre z najczęstszych. Jeśli nie widzisz informacji, których szukasz, użyj przycisków opinii **(Czy ta strona była pomocna?** u dołu ekranu), aby zapytać o to, co chcesz.

> [!NOTE]
> Ten artykuł dotyczy programu Visual Studio w systemie Windows. Aby zapoznać się z programem Visual Studio dla komputerów Mac, zobacz [Rozszerzanie programu Visual Studio dla komputerów Mac](/visualstudio/mac/extending-visual-studio-mac). Aby uzyskać dostęp do programu Visual Studio Code, zobacz [Interfejs API rozszerzenia kodu programu Visual Studio](https://code.visualstudio.com/api).

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Jakie oprogramowanie jest potrzebne do tworzenia rozszerzeń programu Visual Studio?

Należy zainstalować visual studio SDK oprócz programu Visual Studio w celu opracowania rozszerzeń programu Visual Studio. Można zainstalować visual studio SDK w ramach regularnej instalacji lub można zainstalować go później. Aby uzyskać więcej informacji na temat instalowania zestawu SDK programu Visual Studio, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Jakie rzeczy można zrobić z rozszerzeniami programu Visual Studio?

Niebo jest granicą, jeśli chodzi o wyobrażanie sobie różnych rozszerzeń programu Visual Studio. Oczywiście większość rozszerzeń ma coś wspólnego z pisaniem kodu, ale tak nie musi być. Oto kilka przykładów rodzajów rozszerzeń, które można utworzyć:

- Obsługa języków, które nie są uwzględnione w programie Visual Studio, z kolorowaniem składni, intellisense i obsługą kompilatora i debugowania

- Narzędzia zwiększające produktywność, które rozszerzają podstawowe środowisko IDE o dodatkowe szablony, refaktoryzowanie kodu, nowe okna dialogowe lub okna narzędzi

- Projektanci specyficzna dla scenariuszy, takich jak projektowanie danych lub obsługa chmury

Przykłady rozszerzeń można zapoznać się z [programem Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Wiele rozszerzeń jest dostępnych jako open source, a marketplace zawiera łącza do ich repozytorium GitHub.

## <a name="which-visual-studio-features-can-i-extend"></a>Które funkcje programu Visual Studio można rozszerzyć?

Teoretycznie można rozszerzyć prawie dowolną część programu Visual Studio: menu, paski narzędzi, polecenia, okna, rozwiązania, projekty, edytory i tak dalej.

W praktyce odkryliśmy, że funkcje, które większość ludzi chce rozszerzyć, to polecenia, menu i paski narzędzi, okna, IntelliSense i projekty. Oto linki do odpowiednich sekcji:

- [Rozszerzanie menu i poleceń:](../extensibility/extending-menus-and-commands.md)dodawanie własnych elementów do menu i pasków narzędzi programu Visual Studio. Można ich używać do uruchamiania nowych funkcji programu Visual Studio lub własnych zewnętrznych aplikacji pomocniczych. Można również podać niestandardowe skróty dla elementów menu.

- [Rozszerzanie i dostosowywanie narzędzia Windows:](../extensibility/extending-and-customizing-tool-windows.md)rozszerzanie istniejących okien narzędzi lub tworzenie własnych okien narzędzi. Na przykład można dodać nowe właściwości do **właściwości**lub utworzyć nowe okno narzędzia, aby dodać dodatkowe funkcje.

- [Rozszerzenia usługi edytora i języka:](../extensibility/editor-and-language-service-extensions.md)dodaj własne dostosowania do intellisense dostępne dla języków programu Visual Studio lub utwórz obsługę nowych języków programowania. Można utworzyć nowe uzupełnienia instrukcji, sugestie i nowe etykietki narzędzi QuickInfo. Za pomocą żarówek można dodawać sugestie refaktoryzacji i poprawki kodu do obsługi nowych języków programowania.

- [Rozszerzanie projektów](../extensibility/extending-projects.md)

- [Rozszerzanie opcji i ustawień użytkownika](../extensibility/extending-user-settings-and-options.md)

- [Rozszerzanie właściwości i okno właściwości](../extensibility/extending-properties-and-the-property-window.md)

- [Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)

- [Visual Studio Shell (izolowany)](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

## <a name="what-project-templates-are-provided-by-the-vssdk"></a><a name="BKMK_ProjectTemplate"></a>Jakie szablony projektów są dostarczane przez VSSDK?
 Dwa główne typy rozszerzeń to VSPackages i rozszerzenia MEF. Ogólnie rzecz biorąc rozszerzenia VSPackage są używane dla rozszerzeń, które używają lub rozszerzają polecenia, okna narzędzi i projekty. Rozszerzenia MEF są używane do rozszerzania lub dostosowywania edytora visual studio.

 W przypadku rozszerzeń języka Visual C# i Visual Basic zestaw VSSDK udostępnia pusty szablon projektu VSIX, którego można używać razem z nowymi szablonami elementów, które tworzą polecenia menu, okna narzędzi i rozszerzenia edytora. Można również użyć tego szablonu do pakowania szablonów projektu, fragmentów kodu i innych artefaktów do dystrybucji do innych użytkowników.

 W przypadku języka C++ kreator VSPackage udostępnia kod służący do dodawania poleceń menu, okien narzędzi i edytorów niestandardowych.

 Szablon Izolowanej powłoki służy do pakowania rozszerzenia w wersji powłoki programu Visual Studio, która można oznaczyć i rozpowszechniać jako własne. W poniższych tematach pokazano, jak rozpocząć pracę z każdym rodzajem rozszerzenia:

- Polecenia menu: [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md)

- Okna narzędzi: [Tworzenie rozszerzenia z oknem narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md)

- Rozszerzenia edytora: [tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- Podstawowe pakiety VSPackages: [Tworzenie rozszerzenia z pakietem VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

- Szablon projektu VSIX: [Wprowadzenie do szablonu projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Jak uzyskać rozszerzenie, aby wyglądało jak visual studio?
 Uzyskaj doskonałe wskazówki dotyczące projektowania interfejsu użytkownika dla rozszerzenia w [wskazówki dotyczące środowiska użytkownika](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)programu Visual Studio.

## <a name="where-can-i-find-examples-of-vssdk-code"></a>Gdzie można znaleźć przykłady kodu VSSDK?
 Każde z łączy wymienionych w poprzedniej sekcji mają wskazówki krok po kroku, które pokazują, jak zaimplementować określone funkcje. Przykłady vssdk open source można również znaleźć w usłudze GitHub w [programie Visual Studio Samples.](https://github.com/Microsoft/VSSDK-Extensibility-Samples)

## <a name="how-can-i-distribute-my-extension"></a>Jak mogę rozpowszechniać moje rozszerzenie?
 Rozszerzenie można zainstalować na innym komputerze lub wysłać do znajomych jako plik vsix, który instalujesz, klikając je dwukrotnie. Więcej informacji o pakietach VSIX można znaleźć na [wysyłce rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Rozszerzenie można również opublikować w witrynie Visual Studio Marketplace, co powoduje, że jest ono widoczne dla dużej liczby klientów programu Visual Studio. Na przykład pakowania rozszerzenia do portalu Marketplace zobacz [Instruktaż: Publikowanie rozszerzenia programu Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Aby uzyskać więcej informacji na temat tego, co należy zrobić, aby opublikować w portalu Marketplace, zobacz [Produkty i rozszerzenia dla programu Visual Studio](/azure/devops/extend/overview?view=vsts).

## <a name="see-also"></a>Zobacz też

- [Rozszerzenie programu Visual Studio dla komputerów Mac](/visualstudio/mac/extending-visual-studio-mac)
- [Rozszerzanie kodu programu Visual Studio](https://code.visualstudio.com/api)
