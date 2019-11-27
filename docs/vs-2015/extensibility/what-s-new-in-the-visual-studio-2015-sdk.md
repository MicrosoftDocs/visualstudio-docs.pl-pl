---
title: What's New in Visual Studio 2015 SDK | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6735f929f52387f4cb40406d6918894e72bb40d3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299689"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Co&#39;nowego w Visual Studio 2015 SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK ma następujące nowe i zaktualizowane funkcje programu Visual Studio 2015, Visual Studio 2015, aktualizowane i programu Visual Studio 2017.

## <a name="visual-studio-2017"></a>Visual Studio 2017

Począwszy od programu Visual Studio 2017, skanowanie w poszukiwaniu szablonów elementów i projektów niestandardowych zostanie już wykonane. Zamiast tego rozszerzenia, należy podać plik manifestu szablonu, które opisują lokalizację instalacji tych szablonów. Za pomocą programu Visual Studio 2017 można zaktualizować rozszerzenia VSIX. W przypadku wdrożenia przy użyciu Instalatora MSI rozszerzenia, musisz ręcznie wygenerować plik manifestu szablonu. Aby uzyskać więcej informacji, zobacz [uaktualnianie niestandardowych Szablony projektów i elementów dla programu Visual Studio 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). Schemat manifestu szablonu jest udokumentowany w [dokumentacji schematu manifestu szablonu programu Visual Studio](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).

## <a name="vs-2015-sdk-update-1"></a>Program VS 2015 SDK z aktualizacją Update 1
 Aktualizacja Update 1 obejmuje narzędzia ułatwiające rozszerzenia dobrze współpracować z motywów kolorów i usługi obrazów programu Visual Studio.

 Te tematy znajdują się w sekcji [VSSDK Utilities](../extensibility/internals/vssdk-utilities.md) :

- Narzędzia do tworzenia [kolorów](../extensibility/internals/color-theming-tools.md) ułatwiające tworzenie i edytowanie niestandardowych kolorów dla programu Visual Studio.

- [Narzędzia usługi obrazów](../extensibility/internals/image-service-tools.md) umożliwiają współpracę z plikami manifestu obrazu programu Visual Studio.

## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Nowy sposób dodawania zestawu SDK programu Visual Studio do programu Visual Studio
 Począwszy od programu Visual Studio 2015, nie trzeba pobrać program Visual Studio SDK osobno. Zamiast tego można zainstalować go jako część procesu normalnej instalacji lub użytkownik może zainstalować ją później. Po otwarciu lub utworzyć rozwiązania VSIX programu Visual Studio zapyta, aby zainstalować narzędzia rozszerzalności programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="new-ways-of-creating-extensions"></a>Nowe sposoby tworzenia rozszerzeń
 Począwszy od programu Visual Studio 2015 SDK mają różne sposoby tworzenia rozszerzenia, w zależności od tego, jaki język programowania jest używany.

### <a name="visual-c-and-visual-basic"></a>Visual C# i Visual Basic
 W języku C# i Visual Basic istnieje wiele różnych szablonów elementów projektów, które umożliwiają tworzenie pakietów VSPackage, polecenia menu, okien narzędzi, Edytor klasyfikatorów, zakończeń edytora i rozszerzenia marginesu edytora. Można dodać wybranych lub wszystkich z nich do standardowych projektów VSIX. Aby uzyskać więcej informacji, zobacz:

- [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md)

- [Tworzenie rozszerzenia za pomocą okna narzędzi](../extensibility/creating-an-extension-with-a-tool-window.md)

- [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- [Tworzenie rozszerzenia za pomocą pakietu VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

     Kreator pakietu VSPackage nie tworzy już rozszerzenia w języku C# lub Visual Basic.

### <a name="c"></a>C++
 Dla języka C++ Kreator pakietu VSPackage obsługuje polecenia menu, okien narzędzi i edytorach niestandardowych. Poszukaj go w oknie dialogowym **Nowy projekt** w **wizualizacji C++ /rozszerzalności**.

## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Zestawów odwołań zestawu SDK programu VS, za pomocą narzędzia NuGet
 Zwiększyć możliwości przenoszenia i udostępniania projektów rozszerzeń można użyć wersji NuGet zestawów odwołań zestawu SDK programu VS.  Są one dostępne w [NuGet.org](https://www.nuget.org/) publikowanych przez [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) i mogą być łatwo dodawane do projektu lub rozwiązania za pomocą okna dialogowego odwołania programu Visual Studio **/Zarządzanie pakietami NuGet** . Można dodawać poszczególne odwołania do określonych zestawów rozszerzalnych lub dodać wszystkie odwołania do zestawów programu VS SDK jednocześnie przy użyciu [meta](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)SDK programu vs. Aby dowiedzieć się więcej o pakiecie NuGet, zobacz [Omówienie narzędzia NuGet](https://docs.microsoft.com/nuget/) i [Zarządzanie pakietami NuGet przy użyciu okna dialogowego](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-visual-studio).

 Gdy używasz wersji NuGet zestawów odwołań zestawu SDK programu VS, inny użytkownik nie musi zainstalować zestaw SDK programu VS, aby otworzyć i skompilować projekt.  NuGet zestawy referencyjne i narzędzia do kompilacji zestawu SDK automatycznie zostanie zainstalowana na komputerze dla tego projektu.

 Szablony elementów zestawu SDK NuGet na użytek odniesień do nich i narzędzia kompilacji, dzięki czemu uzyskujesz zalety NuGet domyślnie.

> [!NOTE]
> Można nadal korzystać z zainstalowanych zestawów odwołań programu VS SDK wraz z projektami (znajdującymi się w obszarze \<lokalizacji instalacji programu Visual Studio > \ VSSDK\VisualStudioIntegration\Common\Assemblies), a istniejące projekty rozszerzalności nie muszą zostać uaktualnione, aby używać pakietów NuGet.  W oknie dialogowym odwołania do projektu **/Dodaj odwołanie** nadal można użyć zainstalowanych zestawów odwołań programu VS SDK.
>
> Jeśli chcesz zmodyfikować istniejące projekty, aby używać narzędzia NuGet, zobacz [How to: migruje pakietów VSPackage do Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) , który zawiera sekcję dotyczącą aktualizowania projektów rozszerzalności do pakietów NuGet.

## <a name="light-bulbs"></a>Żarówki
 Jedną z najbardziej atrakcyjnych nowych sposobów pisania kodu rozszerzenia jest zapewniana przez projekt Roslyn. Aby uzyskać więcej informacji, zobacz [Roslyn](https://github.com/dotnet/Roslyn).

 Ikony żarówek są nową funkcję, która jest dostarczana z VSSDK. Są one ikony stosowane przy w edytorze programu Visual Studio, które pozwalają wyświetlić zestaw akcji refaktoryzacji kodu lub poprawki dla problemów identyfikowane za pomocą analizatorów kodu wbudowanego. Aby uzyskać więcej informacji, zobacz [Przewodnik: wyświetlanie sugestii żarówki](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).

## <a name="updated-user-experience-guidelines"></a>Wskazówki dotyczące interfejsu zaktualizowany użytkownik
 Projektowanie nowych rozszerzeń lub funkcje programu Visual Studio? Zapoznaj się z zaktualizowanymi i rozszerzonymi [wskazówkami dotyczącymi środowiska użytkownika programu Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Znajdziesz [tokeny koloru](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [rozmiary czcionek](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [specyfikacje układu okna dialogowego](../extensibility/ux-guidelines/layout-for-visual-studio.md)i inne wskazówki, których potrzebujesz, aby bezproblemowo zintegrować nowy interfejs użytkownika z programem Visual Studio.
