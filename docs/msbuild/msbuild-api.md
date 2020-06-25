---
title: Interfejs API programu MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e14f60e84611041294379108852f697c023cbcd8
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350800"
---
# <a name="use-the-msbuild-api"></a>Korzystanie z interfejsu API programu MSBuild

MSBuild oferuje publiczną powierzchnię interfejsu API, dzięki czemu program może wykonywać kompilacje i sprawdzać projekty. Najnowsze wersje interfejsów API programu MSBuild można znaleźć w następujących pakietach NuGet:

| Nazwa pakietu | Opis |
| ------------ | ----------- |
| [Microsoft. Build](https://www.nuget.org/packages/Microsoft.Build) | Zawiera zestaw Microsoft. Build, który służy do tworzenia, edytowania i oceniania projektów programu MSBuild.|
| [Microsoft. Build. Framework](https://www.nuget.org/packages/Microsoft.Build.Framework)| Zawiera wspólny zestaw programu MSBuild Framework używany przez inne zestawy MSBuild. |
| [Microsoft. Build. Runtime](https://www.nuget.org/packages/Microsoft.Build.Runtime) | Dostarcza kompletną kopię pliku wykonywalnego programu MSBuild. Odwołuje się do tego pakietu tylko wtedy, gdy aplikacja wymaga załadowania projektów lub wykonania kompilacji w procesie bez konieczności instalowania programu MSBuild. Pomyślnie ocenianie projektów przy użyciu tego pakietu wymaga agregacji dodatkowych składników (na przykład kompilatorów) do katalogu aplikacji. |
| [Microsoft. Build. Tasks. Core](https://www.nuget.org/packages/Microsoft.Build.Tasks.Core) | Zawiera zestaw Microsoft. Build. Tasks, który implementuje często używane zadania programu MSBuild. |
| [Microsoft. Build. Utilities. Core](https://www.nuget.org/packages/Microsoft.Build.Utilities.Core) | Zawiera zestaw Microsoft. Build. Utilities, który służy do implementowania niestandardowych zadań programu MSBuild. |

Ponadto NuGet obsługuje również starszy zestaw, [Microsoft. Build. Engine](https://www.nuget.org/packages/Microsoft.Build.Engine), który jest przestarzały.

Istnieje kilka różnych wersji interfejsu API programu MSBuild, a w przypadku wersji 15 i 16 istnieją dwie odrębne formy zestawów w pakietach NuGet, jedna skompilowana z .NET Framework, a druga skompilowana przy użyciu platformy .NET Core, która jest podzbiorem powierzchni interfejsu API .NET Framework.  Wersja programu MSBuild programu .NET Core jest używana po wywołaniu `dotnet` polecenia i w przypadku korzystania z programu MSBuild w systemach Mac i Linux.

Dokumentację interfejsu API programu MSBuild można znaleźć za pomocą [przeglądarki interfejsu API platformy .NET](/dotnet/api)lub przeglądając przestrzenie nazw na poniższej liście.

| Przestrzeń nazw | Dotyczy: | Opis |
|-----------| -----------| ----------- |
| [Microsoft. Build. konstrukcja](/dotnet/api/Microsoft.Build.Construction) | Wszystko |  Zawiera typy, które są używane przez model obiektów MSBuild do konstruowania elementów głównych projektu z nieoszacowanymi wartościami. Każdy katalog główny projektu odpowiada plikowi projektu lub obiektowi docelowemu. |
| [Microsoft. Build. Definition](/dotnet/api/Microsoft.Build.Definition) | Wszystko | Zawiera `ProjectOptions` klasę, która obsługuje konstruowanie projektu. |
| [Microsoft. Build. Evaluation](/dotnet/api/Microsoft.Build.Evaluation) | Wszystko | Zawiera typy, które są używane przez model obiektów MSBuild do oceniania projektów. Każdy projekt jest skojarzony z co najmniej jednym elementem głównym projektu. |
| [Microsoft. Build. Evaluation. Context](/dotnet/api/Microsoft.Build.Evaluation.Context) | Wszystko | Zawiera `EvaluationContext` klasę, która jest używana do przechowywania stanu oceny dla wywołań. |
| [Microsoft. Build. Exceptions](/dotnet/api/Microsoft.Build.Exceptions) | Wszystko | Zawiera typy wyjątków, które mogą zostać zgłoszone podczas procesu kompilacji. |
| [Microsoft.Build.Execution](/dotnet/api/Microsoft.Build.Execution) | Wszystko | Zawiera typy, które są używane przez model obiektów MSBuild do kompilowania projektów. |
| [Microsoft. Build. Framework](/dotnet/api/Microsoft.Build.Framework) | Wszystko | Zawiera typy, które definiują sposób, w jaki zadania i rejestratory współdziałają z aparatem MSBuild.|
| [Microsoft. Build. Framework. Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler) | Wszystko | Zawiera typy obsługujące profilowanie wydajności. |
| [Microsoft. Build. Framework. XamlTypes](/dotnet/api/Microsoft.Build.Framework.XamlTypes) | Tylko .NET Framework | Zawiera klasy służące do reprezentowania typów XAML analizowanych z plików, reguł i innych źródeł. |
| [Microsoft. Build. obsługi symboli wieloznacznych](/dotnet/api/Microsoft.Build.Globbing) | Wszystko | Zawiera klasy, które obsługują przetwarzanie symboli wieloznacznych. |
| [Microsoft. Build. obsługi symboli wieloznacznych. Extensions](/dotnet/api/Microsoft.Build.Globbing.Extensions) | Wszystko | Zawiera typy, które obsługują rozszerzenia do przetwarzania symboli wieloznacznych. |
| [Microsoft. Build. Graph](/dotnet/api/Microsoft.Build.Graph) | Wszystko | Zawiera typy obsługujące `-graph` przełącznik MSBuild. |
| [Microsoft. Build. Logging](/dotnet/api/Microsoft.Build.Logging) | Wszystko | Zawiera typy służące do rejestrowania postępu kompilacji. |
| [Microsoft. Build. ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting) | Wszystko | Zawiera typy obsługujące komunikację zdalną w programie MSBuild. |
| [Microsoft. Build. Tasks](/dotnet/api/Microsoft.Build.Tasks) | Wszystko | Zawiera implementację wszystkich zadań wysyłanych za pomocą programu MSBuild. |
| [Microsoft. Build. Tasks. Deployment. program inicjujący](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper) | Tylko .NET Framework | Zawiera klasy używane wewnętrznie przez program MSBuild. |
| [Microsoft. Build. Tasks. Deployment. ManifestUtilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities) | Tylko .NET Framework | Zawiera klasy używane przez program MSBuild.|
| [Microsoft. Build. Tasks. hosting](/dotnet/api/Microsoft.Build.Tasks.Hosting) | Wszystko | Zawiera klasy używane wewnętrznie przez program MSBuild. |
| [Microsoft. Build. Tasks. XAML](/dotnet/api/Microsoft.Build.Tasks.Xaml) | Tylko .NET Framework | Zawiera klasy powiązane z zadaniami kompilacji XAML. |
| [Microsoft. Build. Utilities](/dotnet/api/Microsoft.Build.Utilities) | Wszystko | Zawiera klasy pomocnika, których można użyć do tworzenia własnych rejestratorów i zadań programu MSBuild.|

W poprzedniej tabeli, wszystkie w kolumnie dotyczy, to typy w przestrzeni nazw są dostępne zarówno w .NET Framework, jak i w wersji .NET Core interfejsu API programu MSBuild.
