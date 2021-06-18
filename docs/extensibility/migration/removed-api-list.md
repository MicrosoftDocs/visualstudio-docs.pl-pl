---
title: Interfejsy API usunięte w wersji Visual Studio 2022 (wersja zapoznawcza)
description: Dowiedz się więcej o interfejsach API zestawu SDK programu VS usuniętych w wersji Visual Studio 2022 (wersja zapoznawcza), aby autorzy rozszerzeń zaktualizowali swoje rozszerzenia do pracy z programem Visual Studio 2022 (wersja zapoznawcza).
ms.date: 06/08/2021
ms.topic: reference
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: bed8d0a261f70acb5e842ebeaf0059faae3fc478
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308786"
---
# <a name="visual-studio-2022-sdk-removed-apis"></a>Visual Studio API usunięte z zestawu SDK 2022

[!INCLUDE [preview-note](../includes/preview-note.md)]

Poniższe interfejsy API zostały usunięte z zestawu SDK usługi Visual Studio i nie można ich już używać. Aby uzyskać szczegółowe informacje na temat aktualizowania kodu, zobacz poszczególne sekcje.

* [`IVsImageService`](#ivsimageservice)
* [`IBlockContextProvider`](#iblockcontextprovider)
* [`IToolTipProvider`](#itooltipprovider)
* [`IVsTextScanner` I `IVsFullTextScanner`](#ivstextscanner-and-ivsfulltextscanner)
* [Asynchroniczne ładowanie rozwiązań i uproszczone ładowanie rozwiązań](#asynchronous-solution-load-and-lightweight-solution-load)
* [`IVsDummy`](#ivsdummy)
* [`Microsoft.VisualStudio.Shell.Task`](#microsoftvisualstudioshelltask)
* [Bezpieczne otwieranie z źródła](#open-from-source-safe)
* [Nowe funkcje WPF projektant XAML dla .NET Framework](#new-wpf-xaml-designer-for-net-framework)

## <a name="ivsimageservice"></a>IVsImageService

Jest `IVsImageService` usuwany w Visual Studio 2022 r. Wszyscy użytkownicy powinni zamiast tego `IVsImageService` przejść do `IVsImageService2` .

### <a name="recommended-updates"></a>Zalecane aktualizacje

Jeśli używasz metody `IVsImageService` , zamień wywołania do jej metod na wywołania metod równoważnych na `IVsImageService2` :

| **IVsImageService, metoda** | **Równoważna metoda IVsImageService2** |
|----------------------------|----------------------------------------|
| Dodaj                        | AddCustomImage                         |
| Get                        | Getimage                               |
| GetIconForFile             | GetImageMonikerForFile                 |
| GetIconForFileEx           | GetImageMonikerForFile                 |

`IVsImageService`Metody Add i Get przydają się do obrazów niestandardowych według nazwy (ciągu), a nie monikera.  Preferowane jest przełączenie kodu tak, aby używać tylko monikerów do odwoływać się do obrazów niestandardowych, ale jeśli okaże się to niepraktyczne, istnieje kilka metod, które umożliwią skojarzenie nazwy z `IVsImageService2` monikerami:

* `TryAssociateNameWithMoniker`
* `GetImageMonikerForName`

Za pomocą tych dwóch metod można nadal odwoływać się do obrazów według nazwy.

## <a name="iblockcontextprovider"></a>IBlockContextProvider

Powiązane `IBlockContextProvider` typy i są usuwane w Visual Studio 2022 r. Wszyscy użytkownicy powinni zamiast tego `IBlockContextProvider` przejść do `IStructureContextSourceProvider` .

### <a name="recommended-updates"></a>Zalecane aktualizacje

Zamiast tego `IBlockContextProvider` użytkownicy powinni używać `IStructureContextSourceProvider` [(dokumentacja](/dotnet/api/microsoft.visualstudio.text.adornments.istructurecontextsourceprovider)).

## <a name="itooltipprovider"></a>IToolTipProvider

Powiązane `IToolTipProvider` typy i są usuwane w Visual Studio 2022 r. Wszyscy użytkownicy powinni zamiast tego `IToolTipProvider` przejść do `IToolTipService` .

### <a name="recommended-updates"></a>Zalecane aktualizacje

Zamiast tego `IToolTipProvider` użytkownicy powinni używać `IToolTipService` [(dokumentacja](/dotnet/api/microsoft.visualstudio.text.adornments.itooltipservice)).

## <a name="ivstextscanner-and-ivsfulltextscanner"></a>IVsTextScanner i IVsFullTextScanner

I `IVsTextScanner` `IVsFullTextScanner` są usuwane w Visual Studio 2022 r. Zamiast tego wszyscy użytkownicy systemu `IVsTextScanner` lub powinni przejść do `IVsFullTextScanner` `IVsTextLines` .

### <a name="recommended-updates"></a>Zalecane aktualizacje

Zamiast nich `IVsTextScanner` użytkownicy lub powinni używać `IVsFullTextScanner` `IVsTextLines` [(dokumentacja](/dotnet/apimicrosoft.visualstudio.textmanager.interop.ivstextlines.getlinetext)).

## <a name="asynchronous-solution-load-and-lightweight-solution-load"></a>Asynchroniczne ładowanie rozwiązań i uproszczone ładowanie rozwiązań

Funkcje asynchronicznego ładowania rozwiązań (ASL) i uproszczonego ładowania rozwiązań (LSL) zostaną usunięte w Visual Studio 2022 r., w związku z tym następujące metody są usuwane:

### <a name="interfaces"></a>Interfejsy

* `IVsSolution4` - Metody: `IsBackgroundSolutionLoadEnabled` , `EnsureProjectsAreLoaded` , `EnsureProjectIsLoaded` , `EnsureSolutionIsLoaded`
* `IVsSolutionLoadEvents` - Metody: `OnBeforeBackgroundSolutionLoadBegins` , `OnQueryBackgroundLoadProjectBatch` , `OnBeforeLoadProjectBatch` , `OnAfterLoadProjectBatch`
* `IVsSolutionLoadManagerSupport` — Cały interfejs
* `IVsSolutionLoadManager` — Cały interfejs
* `IVsSccManager3`  — Cały interfejs
* `IVsAsynchronousProjectCreate` — Cały interfejs
* `IVsAsynchronousProjectCreateUI` — Cały interfejs

### <a name="enums-properties-and-ui-contexts"></a>Wylicze, właściwości i konteksty interfejsu użytkownika

* `VSHPROPID_ProjectUnloadStatus` - Wyli). `UNLOADSTATUS_LoadPendingIfNeeded`
* `VSHPROPID_DemandLoadDependencies`
* `VSHPROPID_IsProjectProvisioned`
* `VSPROPID_IsInBackgroundIdleLoadProjectBatch`
* `VSPROPID_IsInSyncDemandLoadProjectBatch`
* `VSPROPID_ActiveSolutionLoadManager`
* `UICONTEXT_BackgroundProjectLoad`

### <a name="recommended-updates"></a>Zalecane aktualizacje

Brak.

## <a name="ivsdummy"></a>IVsDummy

Jest `IVsDummy` usuwany w Visual Studio 2022 r. i nie zostanie zastąpiony. 

### <a name="recommended-updates"></a>Zalecane aktualizacje

Brak. Nie powinno to jednak mieć żadnego wpływu, ponieważ interfejs API nic nie robił.

## <a name="microsoftvisualstudioshelltask"></a>Microsoft.VisualStudio.Shell.Task

Nazwa `Microsoft.VisualStudio.Shell.Task` klasy została zmieniona na , aby nie `Microsoft.VisualStudio.Shell.TaskListItem` kolidowała z bardzo popularną `System.Threading.Tasks.Task` klasą.

## <a name="open-from-source-safe"></a>Bezpieczne otwieranie z źródła

Obsługa otwierania rozwiązania z bezpiecznego źródła jest usuwana, w związku z tym usuwane są następujące metody, zdarzenia i stałe.

## <a name="interfaces"></a>Interfejsy

* `IVsSCCProvider3` — Cały interfejs

### <a name="recommended-updates"></a>Zalecane aktualizacje

Brak.

## <a name="new-wpf-xaml-designer-for-net-framework"></a>Nowe funkcje WPF projektant XAML dla .NET Framework

Bieżąca wersja platformy WPF projektant XAML dla platformy .NET Framework jest przestarzała i zostanie zastąpiona nowym WPF projektant XAML dla platformy .NET Framework na podstawie tej samej architektury, która jest używana dla platformy WPF projektant XAML dla platformy .NET (.NET Core). Oznacza to również, że model rozszerzalności .NET Framework WPF oparty na .design.dll i Microsoft.Windows.Design.Extensibility nie jest już obsługiwany. Nowa wersja platformy WPF projektant XAML dla platformy .NET Framework będzie zapewniać ten sam model rozszerzalności co model WPF projektant XAML dla platformy .NET (.NET Core). Jeśli utworzono już rozszerzenie .designtools.dll dla platformy .NET (.NET Core), to samo rozszerzenie będzie działać dla nowego rozszerzenia WPF projektant XAML dla .NET Framework. Skorzystaj z poniższego linku migracji, aby uzyskać więcej informacji na temat migracji do nowego modelu rozszerzalności dla platform WPF (.NET Framework i .NET Core) oraz platform UWP w przyszłości. 

### <a name="recommended-updates"></a>Zalecane aktualizacje

Zobacz [Migracja rozszerzalności projektanta XAML.](https://github.com/microsoft/xaml-designer-extensibility/blob/main/documents/xaml-designer-extensibility-migration.md)
