---
title: Co nowego w zestawie SDK programu Visual Studio 2015 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d47e40a5c38eeb7898aa179282fa55bbe17ef1d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75917331"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Co nowego w&#39;s w zestawie SDK programu Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zestaw Visual Studio SDK zawiera następujące nowe i zaktualizowane funkcje programu Visual Studio 2015, Visual Studio 2015 zaktualizowane i Visual Studio 2017.

## <a name="visual-studio-2017"></a>Visual Studio 2017

Począwszy od programu Visual Studio 2017, skanowanie w poszukiwaniu niestandardowych szablonów projektów i elementów nie będzie już wykonywane. Zamiast tego rozszerzenie musi dostarczyć pliki manifestu szablonu opisujące lokalizację instalacji tych szablonów. Aby zaktualizować rozszerzenia VSIX, można użyć programu Visual Studio 2017. W przypadku wdrożenia rozszerzenia przy użyciu pliku MSI musisz ręcznie wygenerować pliki manifestu szablonu. Aby uzyskać więcej informacji, zobacz [uaktualnianie niestandardowych Szablony projektów i elementów dla programu Visual Studio 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). Schemat manifestu szablonu jest udokumentowany w [dokumentacji schematu manifestu szablonu programu Visual Studio](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).

## <a name="vs-2015-sdk-update-1"></a>VS 2015 SDK Update 1
 Aktualizacja Update 1 zawiera narzędzia, które ułatwiają rozszerzenie pracy z motywami kolorów i usługą obrazów programu Visual Studio.

 Te tematy znajdują się w sekcji [VSSDK Utilities](../extensibility/internals/vssdk-utilities.md) :

- Narzędzia do tworzenia [kolorów](../extensibility/internals/color-theming-tools.md) ułatwiające tworzenie i edytowanie niestandardowych kolorów dla programu Visual Studio.

- [Narzędzia usługi obrazów](../extensibility/internals/image-service-tools.md) umożliwiają współpracę z plikami manifestu obrazu programu Visual Studio.

## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Nowy sposób dodawania zestawu Visual Studio SDK do programu Visual Studio
 Począwszy od programu Visual Studio 2015, nie trzeba oddzielnie pobierać zestawu SDK programu Visual Studio. Zamiast tego można go zainstalować w ramach normalnego procesu instalacji. można też zainstalować go później. Gdy otworzysz lub utworzysz rozwiązanie VSIX, program Visual Studio wyświetli żądanie instalacji Visual Studio Extensibility Tools. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="new-ways-of-creating-extensions"></a>Nowe sposoby tworzenia rozszerzeń
 Począwszy od zestawu SDK programu Visual Studio 2015, dostępne są różne opcje tworzenia rozszerzeń, w zależności od języka programowania, którego używasz.

### <a name="visual-c-and-visual-basic"></a>Visual C# i Visual Basic
 W przypadku języków C# i Visual Basic istnieje pełen zakres szablonów elementów projektu, które umożliwiają tworzenie pakietów VSPackage, poleceń menu, okien narzędzi, klasyfikatorów edytora, edytorów edytora i rozszerzeń marginesów edytora. Można dodać dowolne lub wszystkie z nich do standardowego projektu VSIX. Aby uzyskać więcej informacji, zobacz:

- [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md)

- [Tworzenie rozszerzenia za pomocą okna narzędzi](../extensibility/creating-an-extension-with-a-tool-window.md)

- [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- [Tworzenie rozszerzenia za pomocą pakietu VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

     Kreator pakietu VSPackage nie tworzy już rozszerzeń w języku C# lub Visual Basic.

### <a name="c"></a>C++
 W przypadku języka C++ Kreator pakietu VSPackage obsługuje polecenia menu, okna narzędzi i edytory niestandardowe. Poszukaj go w oknie dialogowym **Nowy projekt** w **Visual C++/rozszerzalności**.

## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Zestawy odwołań SDK VS za pośrednictwem NuGet
 Aby zwiększyć przenośność i udostępnianie projektów rozszerzalności, można użyć wersji NuGet zestawów odwołań programu VS SDK.  Są one dostępne w [NuGet.org](https://www.nuget.org/) publikowanych przez [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) i mogą być łatwo dodawane do projektu lub rozwiązania za pomocą okna dialogowego odwołania programu Visual Studio **/Zarządzanie pakietami NuGet** . Można dodawać poszczególne odwołania do określonych zestawów rozszerzalnych lub dodać wszystkie odwołania do zestawów programu VS SDK jednocześnie przy użyciu [meta](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)SDK programu vs. Aby dowiedzieć się więcej o pakiecie NuGet, zobacz [Omówienie narzędzia NuGet](/nuget/) i [Zarządzanie pakietami NuGet przy użyciu okna dialogowego](/nuget/consume-packages/install-use-packages-visual-studio).

 W przypadku korzystania z wersji NuGet zestawów referencyjnych programu VS SDK inny użytkownik nie musi instalować zestawu SDK programu VS, aby otworzyć i skompilować projekt.  Zestawy odwołań NuGet i narzędzia kompilacji programu VS SDK zostaną automatycznie zainstalowane na komputerze dla tego projektu.

 Szablony elementów zestawu SDK programu VS używają narzędzia NuGet do uzyskiwania odwołań i narzędzi do kompilowania, dzięki czemu można domyślnie uzyskać korzyści wynikające z używania NuGet.

> [!NOTE]
> Można nadal korzystać z zainstalowanych zestawów odwołań programu VS SDK z projektami (znajdującymi się w obszarze \<Visual Studio Install Location> \ VSSDK\VisualStudioIntegration\Common\Assemblies), a istniejące projekty rozszerzalności nie muszą być uaktualniane, aby używać pakietów NuGet.  W oknie dialogowym odwołania do projektu **/Dodaj odwołanie** nadal można użyć zainstalowanych zestawów odwołań programu VS SDK.
>
> Jeśli chcesz zmodyfikować istniejące projekty, aby używać narzędzia NuGet, zobacz [How to: migruje pakietów VSPackage do Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) , który zawiera sekcję dotyczącą aktualizowania projektów rozszerzalności do pakietów NuGet.

## <a name="light-bulbs"></a>Żarówki
 Jeden z najbardziej atrakcyjnych nowych sposobów pisania kodu rozszerzenia jest dostarczany przez projekt Roslyn. Aby uzyskać więcej informacji, zobacz [Roslyn](https://github.com/dotnet/Roslyn).

 Żarówki to nowa funkcja, która jest dostarczana z VSSDK. Są one ikonami używanymi w edytorze programu Visual Studio, które rozszerzają się w celu wyświetlenia zestawu akcji refaktoryzacji kodu lub poprawek dla problemów zidentyfikowanych przez wbudowane analizatory kodu. Aby uzyskać więcej informacji, zobacz [Przewodnik: wyświetlanie sugestii żarówki](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).

## <a name="updated-user-experience-guidelines"></a>Zaktualizowane wskazówki dotyczące środowiska użytkownika
 Projektowanie nowych rozszerzeń lub funkcji dla programu Visual Studio? Zapoznaj się z zaktualizowanymi i rozszerzonymi [wskazówkami dotyczącymi środowiska użytkownika programu Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Znajdziesz [tokeny koloru](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [rozmiary czcionek](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [specyfikacje układu okna dialogowego](../extensibility/ux-guidelines/layout-for-visual-studio.md)i inne wskazówki, których potrzebujesz, aby bezproblemowo zintegrować nowy interfejs użytkownika z programem Visual Studio.
