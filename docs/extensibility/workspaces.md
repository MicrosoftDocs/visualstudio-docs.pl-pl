---
title: Obszary robocze w programie Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 011781b434c4d005e473c5f97c60a9269dc5d034
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952766"
---
# <a name="workspaces"></a>Obszary robocze

Obszar roboczy to sposób, w jaki program Visual Studio reprezentuje dowolną kolekcję plików w [otwartym folderze](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)i jest reprezentowana przez <xref:Microsoft.VisualStudio.Workspace.IWorkspace> Typ. W tym obszarze roboczym nie jest zrozumiała zawartość ani funkcje związane z plikami znajdującymi się w folderze. Jest to jednak ogólny zestaw interfejsów API dla funkcji i rozszerzeń umożliwiających tworzenie i używanie danych, na które mogą pracować inne osoby. Producenci składają się z [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) przy użyciu różnych atrybutów eksportu.

## <a name="workspace-providers-and-services"></a>Dostawcy i usługi obszaru roboczego

Dostawcy i usługi obszaru roboczego umożliwiają dostęp do danych i funkcji w celu reagowania na zawartość obszaru roboczego. Mogą one zawierać kontekstowe informacje o pliku, symbole w plikach źródłowych lub funkcje kompilacji.

Obie koncepcje wykorzystują [wzorzec fabryki](https://en.wikipedia.org/wiki/Factory_method_pattern) i są importowane za pomocą MEF przez obszar roboczy. Wszystkie atrybuty eksportu implementują `IProviderMetadataBase` lub `IWorkspaceServiceFactoryMetadata` , ale istnieją konkretne typy, których rozszerzenia powinny używać dla eksportowanych typów.

Jedną z różnic między dostawcami i usługami jest ich relacja z obszarem roboczym. Obszar roboczy może mieć wielu dostawców określonego typu, ale dla każdego obszaru roboczego tworzony jest tylko jedna usługa określonego typu. Na przykład obszar roboczy ma wielu dostawców skanerów plików, ale obszar roboczy ma tylko jedną usługę indeksowania dla każdego obszaru roboczego.

Inną istotną różnicą jest zużycie danych od dostawców i usług. Obszar roboczy jest punktem wejścia, który umożliwia pobieranie danych od dostawców z kilku powodów. Najpierw dostawcy zazwyczaj mają pewien wąski zestaw utworzonych przez siebie danych. Dane mogą być symbolami dla pliku źródłowego C# lub kontekstów pliku kompilacji dla pliku _CMakeLists.txt_ . Obszar roboczy będzie odpowiadał żądaniu odbiorcy, którego metadane są wyrównane do żądania. W drugim przypadku niektóre scenariusze umożliwiają wielu dostawcom Współtworzenie żądania, podczas gdy inne scenariusze używają dostawcy z najwyższym priorytetem.

Z kolei rozszerzenia mogą uzyskiwać wystąpienia i korzystać bezpośrednio z usług obszaru roboczego. Metody rozszerzenia dla programu `IWorkspace` są dostępne dla usług oferowanych przez program Visual Studio, takich jak <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> . Twoje rozszerzenie może oferować usługę obszaru roboczego dla składników w rozszerzeniu lub dla innych rozszerzeń do użycia. Odbiorcy powinni używać <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> lub metody rozszerzenia dostarczanej na `IWorkspace` Typ.

>[!WARNING]
> Nie twórz usług, które powodują konflikt z programem Visual Studio. Może to prowadzić do nieoczekiwanych problemów.

## <a name="disposal-on-workspace-closure"></a>Usuwanie w zamknięciu obszaru roboczego

Po zamknięciu obszaru roboczego, klasy rozszerzeń mogą wymagać usunięcia, ale wywołania kodu asynchronicznego. <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable>Interfejs jest dostępny, aby ułatwić pisanie tego kodu.

## <a name="related-types"></a>Powiązane typy

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> jest centralną jednostką dla otwartego obszaru roboczego, takiego jak otwarty folder.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> tworzy dostawcę dla wystąpienia obszaru roboczego.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> tworzy usługę dla wystąpienia obszaru roboczego.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> należy zaimplementować dla dostawców i usług, które muszą uruchamiać kod asynchroniczny podczas usuwania.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> zapewnia metody pomocnika do uzyskiwania dostępu do dobrze znanych usług lub dowolnych usług.

## <a name="workspace-settings"></a>Ustawienia obszaru roboczego

Obszary robocze mają <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> prostą, ale dodatkową kontrolę nad obszarem roboczym. Aby zapoznać się z podstawowymi omówieniem ustawień, zobacz [Dostosowywanie kompilacji i debugowania zadań](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

Ustawienia dla większości `SettingsType` typów to pliki _JSON_ , takie jak _VSWorkspaceSettings.js_ i _tasks.vs.jswłączone_.

Możliwości centrów ustawień obszaru roboczego wokół "zakresów", które są po prostu ścieżkami w obszarze roboczym. Gdy odbiorca wywołuje <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> wszystkie zakresy, które zawierają żądaną ścieżkę i typ ustawienia są agregowane. Priorytet agregacji zakresu jest następujący:

1. "Ustawienia lokalne", czyli zazwyczaj katalog główny obszaru roboczego `.vs` .
1. Żądana ścieżka.
1. Katalog nadrzędny żądanej ścieżki.
1. Wszystkie dalsze katalogi nadrzędne do i łącznie z korzeniem obszaru roboczego.
1. "Ustawienia globalne", które znajduje się w katalogu użytkownika.

Wynik jest wystąpieniem <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> . Ten obiekt zawiera ustawienia dla określonego typu i można wykonać zapytania w celu ustawienia nazw kluczy przechowywanych jako `string` . <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A>Metody i <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> metody rozszerzające oczekują, że obiekt wywołujący wie o typie żądanej wartości ustawienia. Ponieważ większość plików ustawień jest utrwalonych jako pliki _JSON_ , wiele wywołań będzie używać `string` `bool` `int` tablic tych typów,,, i. Typy obiektów są również obsługiwane. W takich przypadkach można użyć `IWorkspaceSettings` siebie jako argumentu typu. Na przykład:

```json
{
  "intValue": 1,
  "stringValue": "s",
  "boolValue": true,
  "stringArray": [
    "s1",
    "s2"
  ],
  "nestedIWorkspaceSettings": {
    "nestedString": "ns"
  }
}
```

Przy założeniu, że te ustawienia znajdowały się w _VSWorkspaceSettings.js_użytkownika, dostęp do danych można uzyskać w następujący sposób:

```csharp
using System.Collections.Generic;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static void ReadSettings(IWorkspace workspace)
{
    IWorkspaceSettingsManager settingsManager = workspace.GetSettingsManager();
    IWorkspaceSettings settings = settingsManager.GetAggregatedSettings(SettingsTypes.Generic);

    // result == WorkspaceSettingsResult.Success
    WorkspaceSettingsResult result = settings.GetProperty("intValue", out int intValue);
    result = settings.GetProperty("stringValue", out string stringValue);
    result = settings.GetProperty("boolValue", out bool boolValue);
    result = settings.GetProperty("stringArray", out string[] stringArray);
    result = settings.GetProperty("nestedIWorkspaceSettings", out IWorkspaceSettings nestedIWorkspaceSettings);
    result = nestedIWorkspaceSettings.GetProperty("nestedString", out string nestedString);

    // Extension method alternative using default values.
    int intValueOrDefault = settings.Property("intValue", /* default */ 42);

    // Missing key. result == WorkspaceSettingsResult.Undefined
    result = settings.GetProperty("missing", out string missing);

    // Wrong type for a key. result == WorkspaceSettingsResult.Error
    result = settings.GetProperty("intValue", out IWorkspaceSettings notSettings);

    // Special ability to union "stringArray" across all scopes.
    IEnumerable<string> allStringArray = settings.UnionPropertyArray<string>("stringArray");
}
```

>[!NOTE]
>Te ustawienia API są niepowiązane z interfejsami API dostępnymi w `Microsoft.VisualStudio.Settings` przestrzeni nazw. Ustawienia obszaru roboczego to niezależny od hosta i używają plików ustawień właściwych dla obszaru roboczego lub dostawców ustawień dynamicznych.

### <a name="providing-dynamic-settings"></a>Udostępnianie ustawień dynamicznych

Rozszerzenia mogą dostarczyć <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider> s. Ci dostawcy w pamięci umożliwiają rozszerzeniom Dodawanie ustawień lub zastępowanie innych.

Eksportowanie `IWorkspaceSettingsProvider` jest inne niż w przypadku innych dostawców obszarów roboczych. Fabryka nie jest `IWorkspaceProviderFactory` i nie ma specjalnego typu atrybutu. Zamiast tego należy zaimplementować <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> i użyć `[Export(typeof(IWorkspaceSettingsProviderFactory))]` .

```csharp
// Common workspace provider factory pattern
[ExportFeatureProvider(some, args, to, export)]
internal class MyProviderFactory : IWorkspaceProviderFactory<IFeatureProvider>
{
     IFeatureProvider CreateProvider(IWorkspace workspace) => new Provider(workspace);
}

// IWorkspaceSettingsProvider pattern
[Export(typeof(IWorkspaceSettingsProviderFactory))]
internal class MySettingsProviderFactory : IWorkspaceSettingsProviderFactory
{
    // 100 is typically the value used by built-in settings providers. Lower value is higher priority.
    int Priority => 100;

    IWorkspaceSettingsProvider CreateSettingsProvider(IWorkspace workspace) => new MySettingsProvider(workspace);
}
```

>[!TIP]
>Podczas implementowania metod, które zwracają `IWorkspaceSettingsSource` ( `IWorkspaceSettingsProvider.GetSingleSettings` na przykład), zwracają wystąpienie zamiast `IWorkspaceSettings` `IWorkspaceSettingsSource` . `IWorkspaceSettings` zawiera więcej informacji, które mogą być przydatne podczas agregacji ustawień.

### <a name="settings-related-apis"></a>Interfejsy API powiązane z ustawieniami

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> odczytuje i agreguje ustawienia dla obszaru roboczego.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> Pobiera `IWorkspaceSettingsManager` dla obszaru roboczego.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> Pobiera ustawienia dla danego zakresu zagregowane we wszystkich nakładających się zakresach.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> zawiera ustawienia dla określonego zakresu.

## <a name="workspace-suggested-practices"></a>Sugerowane rozwiązania w obszarze roboczym

- Zwróć obiekty z `IWorkspaceProviderFactory.CreateProvider` lub podobnych interfejsów API, które zapamiętają ich `Workspace` kontekst po utworzeniu. Interfejsy dostawców są zapisywane, oczekiwano, że ten obiekt jest przechowywany podczas tworzenia.
- Zapisz pamięć podręczną specyficzną dla obszaru roboczego lub ustawienia w ścieżce "Ustawienia lokalne" obszaru roboczego. Utwórz ścieżkę do pliku przy użyciu programu `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder` Visual Studio 2017 w wersji 15,6 lub nowszej. W przypadku wersji wcześniejszych niż wersja 15,6 Użyj następującego fragmentu kodu:

```csharp
using System.IO;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static string MakeRootedUnderWorkingFolder(IWorkspace workspace, string relativePath)
{
    string workingFolder = workspace.GetSettingsManager().GetAggregatedSettings(SettingsTypes.WorkspaceControlSettings).Property<string>("WorkingFolder");
    return Path.Combine(workingFolder, relativePath);
}
```

## <a name="solution-events-and-package-auto-load"></a>Automatyczne ładowanie zdarzeń rozwiązania i pakietów

Ładowane pakiety mogą implementować `IVsSolutionEvents7` i wywoływać `IVsSolution.AdviseSolutionEvents` . Obejmuje to zdarzenie dotyczące otwierania i zamykania folderu w programie Visual Studio.

Kontekst interfejsu użytkownika może służyć do automatyczne ładowania pakietu. Wartość to `4646B819-1AE0-4E79-97F4-8A8176FDD664`.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>Pakiet SourceExplorerPackage nie został załadowany prawidłowo

Rozszerzalność obszaru roboczego jest silnie oparta na MEFach, a błędy kompozycji spowodują, że nie można załadować folderu obsługującego otwarty folder. Na przykład, jeśli rozszerzenie eksportuje typ z `ExportFileContextProviderAttribute` , ale tylko typ implementuje, wystąpi `IWorkspaceProviderFactory<IFileContextActionProvider>` błąd podczas próby otwarcia folderu w programie Visual Studio.

::: moniker range="vs-2017"

Szczegóły błędu można znaleźć w _%localappdata%\microsoft\visualstudio\15.0_id \componentmodelcache\microsoft.VisualStudio.default.err_. Usuń błędy dla typów implementowanych przez rozszerzenie.

::: moniker-end

::: moniker range=">=vs-2019"

Szczegóły błędu można znaleźć w _%localappdata%\microsoft\visualstudio\16.0_id \componentmodelcache\microsoft.VisualStudio.default.err_. Usuń błędy dla typów implementowanych przez rozszerzenie.

::: moniker-end

## <a name="next-steps"></a>Następne kroki

* [Konteksty pliku](workspace-file-contexts.md) — dostawcy kontekstu plików wprowadzają analizę kodu dla obszarów roboczych otwartych folderów.
* [Indeksowanie](workspace-indexing.md) — indeksowanie obszaru roboczego zbiera i utrzymuje informacje o obszarze roboczym.
