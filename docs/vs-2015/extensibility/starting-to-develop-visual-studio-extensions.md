---
title: Rozpoczynanie tworzenia rozszerzeń | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 489248031633a96a4790c63e9bd8938f56c738c1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766496"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Rozpoczynanie tworzenia rozszerzeń programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli nigdy nie zostały zapisane rozszerzenia programu Visual Studio przed, prawdopodobnie masz kilka pytań. Wymieniono niektóre najbardziej typowe w tym miejscu. Jeśli nie widzisz informacji szukasz, użyj przycisków opinii (**ta strona była pomocna?** u dołu ekranu) aby poprosić o co chcesz.

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Jakie oprogramowanie należy do tworzenia rozszerzenia programu Visual Studio?
 Musisz zainstalować Visual Studio 2015 SDK oprócz programu Visual Studio 2015, aby tworzyć rozszerzenia programu Visual Studio.   Visual Studio 2015 SDK można zainstalować jako część regularnych instalacji, lub można zainstalować ją później. Aby uzyskać więcej informacji na temat instalowania programu Visual Studio SDK, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Jakiego rodzaju rzeczy można zrobić za pomocą rozszerzeń programu Visual Studio?
 Nie ma użytkownika limit, jeśli chodzi o opracowująca w wyobraźni inne rozszerzenia programu Visual Studio. Oczywiście większość rozszerzenia mają coś zrobić w pisaniu kodu, ale które nie mają w przypadku. Poniżej przedstawiono kilka przykładów rodzajów rozszerzeń, które można tworzyć:

- Obsługa języków, które nie są uwzględnione w programie Visual Studio, z obsługą kompilatora i debugowania, IntelliSense i kolorowanie składni

- Narzędzia umożliwiające zwiększenie wydajności, które rozszerzają podstawowe środowiska IDE w usłudze dodatkowe szablony, okna dialogowe refaktoryzacji, nowy kod lub okna narzędzi

- Projektant specyficznego dla domeny dla scenariuszy, takich jak obsługa danych projektu lub w chmurze

  Aby zapoznać się z przykładami rozszerzeń, zapoznaj się z [galerii Visual Studio](https://visualstudiogallery.msdn.microsoft.com/). Możesz również skorzystać z przyjrzeć się [Otwórz źródło rozszerzenia programu Visual Studio](https://github.com/Microsoft/extendvs/blob/master/CommunityExtensions.md).

## <a name="which-visual-studio-features-can-i-extend"></a>Funkcje programu Visual Studio, które można rozszerzyć?
 Teoretycznie można rozszerzyć o niemal dowolnym część programu Visual Studio: menu, paski narzędzi, polecenia, systemu windows, rozwiązania, projekty, edytory i tak dalej.

 W praktyce znaleźliśmy, czy funkcje, których większość osób chce rozszerzyć polecenia, menu i paski narzędzi, windows, funkcji IntelliSense i projektów. Poniżej podano linki do odpowiednich sekcji:

-   [Rozszerzenie menu i poleceń](../extensibility/extending-menus-and-commands.md): Dodawanie własnych elementów do programu Visual Studio, menu i paski narzędzi. Można je uruchomić nowe funkcje programu Visual Studio lub własnych aplikacji zewnętrznych pomocnika. Można również dołączyć skrótów niestandardowych elementów menu.

-   [Rozszerzanie i dostosowywanie narzędzi Windows](../extensibility/extending-and-customizing-tool-windows.md): rozszerzanie istniejących narzędzi systemu windows lub tworzenie własnych narzędzi okien. Na przykład można dodać nowe właściwości do **właściwości**, lub można utworzyć nowego okna narzędzi, aby dodać dodatkowe funkcje.

-   [Edytora i rozszerzenia usługi w języka](../extensibility/editor-and-language-service-extensions.md): dodać własne dostosowania funkcja IntelliSense obsługująca dla języków Visual Studio lub Utwórz obsługę nowych języków programowania. Można utworzyć nowego uzupełniania instrukcji, sugestie i etykietek narzędzi Szybkieinfo nowe. Dzięki żarówkom możesz dodać refaktoryzacji sugestie i poprawek kodu do obsługi nowych języków programowania.

-   [Rozszerzanie projektów](../extensibility/extending-projects.md)

-   [Rozszerzanie opcji i ustawień użytkownika](../extensibility/extending-user-settings-and-options.md)

-   [Rozszerzanie właściwości i okno właściwości](../extensibility/extending-properties-and-the-property-window.md)

-   [Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)

-   [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)

##  <a name="BKMK_ProjectTemplate"></a> Szablony projektów, które są dostarczane przez VSSDK?
 Dwa główne typy rozszerzeń to rozszerzenia pakietów VSPackage i MEF. Ogólnie rzecz biorąc rozszerzenia pakietu VSPackage są używane dla rozszerzeń korzystających z lub rozszerzenia poleceń, okien narzędzi i projektów. Rozszerzenia MEF są używane do rozszerzenie lub dostosowanie edytora programu Visual Studio.

 Rozszerzenia programu Visual C# i Visual Basic VSSDK udostępnia pusty szablon projektu VSIX, używanego razem z nowych szablonów elementów, które tworzyć polecenia menu, okien narzędzi i rozszerzenia edytora. Aby uzyskać więcej informacji, zobacz [What's New in Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md). Można też użyć tego szablonu, szablony projektów pakietu, fragmenty kodu i innych artefaktów, w celu dystrybucji do innych użytkowników.

 Dla języka C++ Kreator pakietu VSPackage zawiera kod, aby dodać polecenia menu, okien narzędzi i edytorach niestandardowych.

 Szablon Isolated Shell jest używany do pakietu rozszerzenia w wersji powłoki programu Visual Studio, którą można oznaczyć i rozpowszechniać jako własny. Poniższe tematy przedstawiają, jak rozpocząć pracę z każdym rodzajem rozszerzenia:

-   Polecenia menu: [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md)

-   Narzędzia systemu windows: [Tworzenie rozszerzenia za pomocą okna narzędzi](../extensibility/creating-an-extension-with-a-tool-window.md)

-   Rozszerzenia edytora: [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md)

-   Podstawowe pakietów VSPackage: [Tworzenie rozszerzenia za pomocą pakietu VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

-   VSIX project template: [Wprowadzenie do szablonu projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)

-   Program Visual Studio isolated shell: [Przewodnik: Tworzenie podstawowej aplikacji Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Jak uzyskać Moje rozszerzenia, aby wyglądał jak Visual Studio?
 Doskonałe porady dotyczące projektowania interfejsu użytkownika dla rozszerzenia w [dotyczące środowiska użytkownika w usłudze Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="where-can-i-find-examples-of-vssdk-code"></a>Gdzie mogę znaleźć przykłady kodu VSSDK
 Mają łącza wymienione w poprzedniej sekcji instruktaży krok po kroku, które pokazują, jak implementować określone funkcje. Możesz również znaleźć "open source" VSSDK przykłady w witrynie GitHub pod [Visual Studio Samples](https://aka.ms/vs2015sdksamples).

## <a name="how-can-i-distribute-my-extension"></a>Jak można rozpowszechniać Moje rozszerzenie?
 Można zainstalować rozszerzenia na innym komputerze lub wysyłania dla Twoich znajomych, jako plik .vsix, instalowania, klikając go dwukrotnie. Możesz dowiedzieć się więcej na temat pakietów VSIX w [wysyłania rozszerzenia programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Można również publikować swoje rozszerzenie w galerii Visual Studio, dzięki czemu widoczne dla dużej liczby klientów w programie Visual Studio. Na przykład pakowania rozszerzenie w galerii, zobacz [instruktażu: Publikowanie rozszerzenia programu Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Aby uzyskać więcej informacji na temat co należy zrobić, aby opublikować w galerii, zobacz [produkty i rozszerzenia programu Visual Studio](https://visualstudiogallery.msdn.microsoft.com/).
