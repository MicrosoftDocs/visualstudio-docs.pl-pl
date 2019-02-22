---
title: Co&#39;nowego w Visual Studio 2015 SDK | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10ceddf29a044ac8538c05cbf7cd300759a76de6
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56692050"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Co&#39;s nowego w programie Visual Studio 2015 SDK
Visual Studio SDK ma następujące nowe i zaktualizowane funkcje programu Visual Studio 2015, Visual Studio 2015, aktualizowane i programu Visual Studio 2017.

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
 W języku C# i Visual Basic istnieje wiele różnych szablonów elementów projektów, które umożliwiają tworzenie pakietów VSPackage, polecenia menu, okien narzędzi, Edytor klasyfikatorów, zakończeń edytora i rozszerzenia marginesu edytora. Standardowy projekt VSIX, można dodać wybranych lub wszystkich tych szablonów. Aby uzyskać więcej informacji, zobacz:

-   [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md)

-   [Tworzenie rozszerzenia za pomocą okna narzędzi](../extensibility/creating-an-extension-with-a-tool-window.md)

-   [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md)

-   [Tworzenie rozszerzenia za pomocą pakietu VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

     Kreator pakietu VSPackage nie tworzy już rozszerzenia w języku C# lub Visual Basic.

### <a name="c"></a>C++
 Dla języka C++ Kreator pakietu VSPackage obsługuje polecenia menu, okien narzędzi i edytorach niestandardowych. Wyszukaj go w **nowy projekt** okna dialogowego w **Visual C++ / rozszerzalności**.

## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Zestawy odwołań zestawu SDK za pomocą narzędzia NuGet
 Zwiększyć możliwości przenoszenia i udostępniania projektów rozszerzeń można użyć wersji NuGet zestawów odwołań zestawu SDK programu VS. Te zestawy są dostępne na [nuget.org](http://www.nuget.org) opublikowanych przez [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) i mogą być łatwo dodawane do projektu lub rozwiązania za pomocą programu Visual Studio **odwołuje się i zarządzanie nimi Pakiety NuGet** okna dialogowego. Możesz dodać poszczególne odwołania do zestawów rozszerzalność specyficzna dla lub dodać zestawu SDK programu VS odwołuje się do zestawów na raz przy użyciu zestawu SDK dla programu [pakiet Meta](http://www.nuget.org/packages/VSSDK_Reference_Assemblies). Aby dowiedzieć się więcej na temat programu NuGet, zobacz [dokumentacja programu NuGet](/NuGet) i [interfejs użytkownika Menedżera pakietów](/NuGet/Tools/Package-Manager-UI) tematów.

 Gdy używasz wersji NuGet zestawów odwołań zestawu SDK programu VS, inny użytkownik nie musi zainstalować zestaw SDK programu VS, aby otworzyć i skompilować projekt.  NuGet zestawy referencyjne i narzędzia do kompilacji zestawu SDK automatycznie zostanie zainstalowana na komputerze dla tego projektu.

 Szablony elementów zestawu SDK NuGet na użytek odniesień do nich i narzędzia kompilacji, dzięki czemu uzyskujesz zalety NuGet domyślnie.

> [!NOTE]
>  Można kontynuować używania zestawów referencyjnych zainstalowany zestaw SDK w PORÓWNANIU z projektami (znajdujący się w \<Visual Studio lokalizacja instalacji > \ VSSDK\VisualStudioIntegration\Common\Assemblies) i nie trzeba być istniejące projekty rozszerzalności uaktualniony do korzystania z pakietów NuGet.  Projekt **odwołuje się / Dodaj odwołanie** okna dialogowego w dalszym ciągu używać zestawów odwołań zainstalowany zestaw SDK programu VS.
>
>  Jeśli chcesz zmodyfikować istniejących projektów można użyć NuGet, zobacz [jak: Migrowanie pakietów VSPackage do programu Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) mającego sekcję na temat aktualizowania rozszerzalności projektów do pakietów NuGet.

## <a name="light-bulbs"></a>Żarówki
 Jedną z najbardziej atrakcyjnych nowych sposobów pisania kodu rozszerzenia jest zapewniana przez projekt Roslyn. Aby uzyskać więcej informacji, zobacz [Roslyn](https://github.com/dotnet/Roslyn).

 Ikony żarówek są nową funkcję, która jest dostarczana z VSSDK. Są one ikony stosowane przy w edytorze programu Visual Studio, które pozwalają wyświetlić zestaw akcji refaktoryzacji kodu lub poprawki dla problemów identyfikowane za pomocą analizatorów kodu wbudowanego. Aby uzyskać więcej informacji, zobacz [instruktażu: Wyświetlanie sugestie z żarówką](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).

## <a name="updated-user-experience-guidelines"></a>Wskazówki dotyczące interfejsu zaktualizowany użytkownik
 Projektowanie nowych rozszerzeń lub funkcje programu Visual Studio? Sprawdź zaktualizowane oraz rozszerzone [wskazówki dotyczące interfejsu użytkownika programu Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Znajdziesz [kolor tokenów](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [rozmiary czcionek](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [specyfikacje układu okna dialogowego](../extensibility/ux-guidelines/layout-for-visual-studio.md)i inne wskazówki, musisz bezproblemowo integrują się nowy interfejs użytkownika z programu Visual Studio.