---
title: What's New in Visual Studio 2015 SDK | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cb7f3e98f0860d05c879a81fb14f05142678baae
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055707"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Co&#39;nowego w Visual Studio 2015 SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK ma następujące nowe i zaktualizowane funkcje programu Visual Studio 2015, Visual Studio 2015, aktualizowane i programu Visual Studio 2017.

## <a name="visual-studio-2017"></a>Visual Studio 2017

Począwszy od programu Visual Studio 2017, skanowanie w poszukiwaniu szablonów elementów i projektów niestandardowych zostanie już wykonane. Zamiast tego rozszerzenia, należy podać plik manifestu szablonu, które opisują lokalizację instalacji tych szablonów. Za pomocą programu Visual Studio 2017 można zaktualizować rozszerzenia VSIX. W przypadku wdrożenia przy użyciu Instalatora MSI rozszerzenia, musisz ręcznie wygenerować plik manifestu szablonu. Aby uzyskać więcej informacji, zobacz [uaktualnianie niestandardowych szablonów projektów i elementów dla programu Visual Studio 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). Schematu manifestu szablonu jest udokumentowany w [Visual Studio Manifest odwołanie do schematu szablonu](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).

## <a name="vs-2015-sdk-update-1"></a>Program VS 2015 SDK z aktualizacją Update 1
 Aktualizacja Update 1 obejmuje narzędzia ułatwiające rozszerzenia dobrze współpracować z motywów kolorów i usługi obrazów programu Visual Studio.

 Te tematy znajdują się pod [narzędzia VSSDK](../extensibility/internals/vssdk-utilities.md) sekcji:

-   [Narzędzia do tworzenia motywów kolorów](../extensibility/internals/color-theming-tools.md) ułatwiają tworzenie i edytowanie niestandardowych kolorów dla programu Visual Studio.

-   [Narzędzia usługi obrazów](../extensibility/internals/image-service-tools.md) pozwalają pracować plików manifestu obrazu programu Visual Studio.

## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Nowy sposób dodawania zestawu SDK programu Visual Studio do programu Visual Studio
 Począwszy od programu Visual Studio 2015, nie trzeba pobrać program Visual Studio SDK osobno. Zamiast tego można zainstalować go jako część procesu normalnej instalacji lub użytkownik może zainstalować ją później. Po otwarciu lub utworzyć rozwiązania VSIX programu Visual Studio zapyta, aby zainstalować narzędzia rozszerzalności programu Visual Studio. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="new-ways-of-creating-extensions"></a>Nowe sposoby tworzenia rozszerzeń
 Począwszy od programu Visual Studio 2015 SDK mają różne sposoby tworzenia rozszerzenia, w zależności od tego, jaki język programowania jest używany.

### <a name="visual-c-and-visual-basic"></a>Visual C# i Visual Basic
 W języku C# i Visual Basic istnieje wiele różnych szablonów elementów projektów, które umożliwiają tworzenie pakietów VSPackage, polecenia menu, okien narzędzi, Edytor klasyfikatorów, zakończeń edytora i rozszerzenia marginesu edytora. Można dodać wybranych lub wszystkich z nich do standardowych projektów VSIX. Aby uzyskać więcej informacji, zobacz:

-   [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md)

-   [Tworzenie rozszerzenia za pomocą okna narzędzi](../extensibility/creating-an-extension-with-a-tool-window.md)

-   [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md)

-   [Tworzenie rozszerzenia za pomocą pakietu VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

     Kreator pakietu VSPackage nie tworzy już rozszerzenia w języku C# lub Visual Basic.

### <a name="c"></a>C++
 Dla języka C++ Kreator pakietu VSPackage obsługuje polecenia menu, okien narzędzi i edytorach niestandardowych. Wyszukaj go w **nowy projekt** okna dialogowego w **Visual C++ / rozszerzalności**.

## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Zestawów odwołań zestawu SDK programu VS, za pomocą narzędzia NuGet
 Zwiększyć możliwości przenoszenia i udostępniania projektów rozszerzeń można użyć wersji NuGet zestawów odwołań zestawu SDK programu VS.  Są one dostępne na [nuget.org](http://www.nuget.org) opublikowanych przez [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) i mogą być łatwo dodawane do projektu lub rozwiązania za pomocą programu Visual Studio **odwołuje się i zarządzanie nim NuGet Pakiety** okna dialogowego. Możesz dodać poszczególne odwołania do zestawów rozszerzalność specyficzna dla lub dodać zestawu SDK programu VS odwołuje się do zestawów na raz przy użyciu zestawu SDK dla programu [pakiet Meta](http://www.nuget.org/packages/VSSDK_Reference_Assemblies). Aby dowiedzieć się więcej na temat programu NuGet, zobacz [Przegląd NuGet](http://docs.nuget.org/) i [Zarządzanie NuGet pakietów przy użyciu okna dialogowego](http://docs.nuget.org/Consume/Package-Manager-Dialog).

 Gdy używasz wersji NuGet zestawów odwołań zestawu SDK programu VS, inny użytkownik nie musi zainstalować zestaw SDK programu VS, aby otworzyć i skompilować projekt.  NuGet zestawy referencyjne i narzędzia do kompilacji zestawu SDK automatycznie zostanie zainstalowana na komputerze dla tego projektu.

 Szablony elementów zestawu SDK NuGet na użytek odniesień do nich i narzędzia kompilacji, dzięki czemu uzyskujesz zalety NuGet domyślnie.

> [!NOTE]
>  Można kontynuować używania zestawów referencyjnych zainstalowany zestaw SDK w PORÓWNANIU z projektami (znajdujący się w \<Visual Studio lokalizacja instalacji > \ VSSDK\VisualStudioIntegration\Common\Assemblies) i nie trzeba być istniejące projekty rozszerzalności uaktualniony do korzystania z pakietów NuGet.  Projekt **odwołuje się / Dodaj odwołanie** okna dialogowego w dalszym ciągu używać zestawów odwołań zainstalowany zestaw SDK programu VS.
>
>  Jeśli chcesz zmodyfikować istniejących projektów można użyć NuGet, zobacz [porady: Migracja pakietów VSPackage Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) mającego sekcję na temat aktualizowania rozszerzalności projektów do pakietów NuGet.

## <a name="light-bulbs"></a>Żarówki
 Jedną z najbardziej atrakcyjnych nowych sposobów pisania kodu rozszerzenia jest zapewniana przez projekt Roslyn. Aby uzyskać więcej informacji, zobacz [Roslyn](https://github.com/dotnet/Roslyn).

 Ikony żarówek są nową funkcję, która jest dostarczana z VSSDK. Są one ikony stosowane przy w edytorze programu Visual Studio, które pozwalają wyświetlić zestaw akcji refaktoryzacji kodu lub poprawki dla problemów identyfikowane za pomocą analizatorów kodu wbudowanego. Aby uzyskać więcej informacji, zobacz [wskazówki: wyświetlanie sugestie z żarówką](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).

## <a name="updated-user-experience-guidelines"></a>Wskazówki dotyczące interfejsu zaktualizowany użytkownik
 Projektowanie nowych rozszerzeń lub funkcje programu Visual Studio? Sprawdź zaktualizowane oraz rozszerzone [dotyczące środowiska użytkownika w usłudze Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Znajdziesz [kolor tokenów](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [rozmiary czcionek](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [specyfikacje układu okna dialogowego](../extensibility/ux-guidelines/layout-for-visual-studio.md)i inne wskazówki, musisz bezproblemowo integrują się nowy interfejs użytkownika z programu Visual Studio.
