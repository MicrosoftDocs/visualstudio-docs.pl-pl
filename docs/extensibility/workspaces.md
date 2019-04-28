---
title: Obszary robocze w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 011781b434c4d005e473c5f97c60a9269dc5d034
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952766"
---
# <a name="workspaces"></a>Obszary robocze

Obszar roboczy to, jak Visual Studio reprezentuje żadnych kolekcji plików z [Otwórz Folder](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), i jest reprezentowana przez <xref:Microsoft.VisualStudio.Workspace.IWorkspace> typu. Przez siebie obszar roboczy nie rozpoznaje zawartości lub funkcji związanych z plikami w folderze. Przeciwnie zapewnia ogólne zestaw interfejsów API dla funkcji i rozszerzeń do tworzenia i wykorzystywania danych, które inne osoby mogą działać na. Producenci są złożone za pośrednictwem [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) przy użyciu różnych wyeksportować atrybutów.

## <a name="workspace-providers-and-services"></a>Obszar roboczy dostawców i usługi

Obszar roboczy dostawców umożliwiają danych i funkcji, aby zareagować na zawartość obszaru roboczego. Mogą być zawierają informacje kontekstowe pliku, symboli w plikach źródłowych lub tworzyć funkcje.

Użyj obu pojęcia [wzorzec fabryki](https://en.wikipedia.org/wiki/Factory_method_pattern) i są importowane za pomocą MEF przez obszar roboczy. Wszystkie atrybuty eksportu zaimplementować `IProviderMetadataBase` lub `IWorkspaceServiceFactoryMetadata`, ale konkretnych typów, które rozszerzenia należy używać typów eksportowanych.

Jedną różnicą między dostawcami i usług jest ich relacji z obszarem roboczym. Obszar roboczy może mieć wielu dostawców określonego typu, ale tylko jedna usługa określonego typu jest tworzony na obszar roboczy. Na przykład obszar roboczy zawiera wielu dostawców skanera pliku, ale obszar roboczy ma tylko jedną usługę indeksowania danego obszaru roboczego.

Inną główną różnicą jest użycie danych od dostawców i usługi. Obszar roboczy jest punktem wejściowym umożliwiającym pobieranie danych od dostawców kilka przyczyn. Po pierwsze dostawcy zazwyczaj mają pewne wąskie zestawu danych, utworzonego przez siebie. Dane mogą być symbole dla C# pliku źródłowego lub przy tworzeniu pliku konteksty dla _CMakeLists.txt_ pliku. Obszar roboczy będzie pasuje do żądania klientów dostawców, w których metadanych wyrównać z żądaniem. Po drugie, Zezwalaj na niektórych scenariuszy dla wielu dostawców na Współtworzenie na żądanie, podczas gdy inne scenariusze użycia dostawcy o najwyższym priorytecie.

Rozszerzenia mogą z kolei pobiera wystąpienia i bezpośrednią interakcję z obszaru roboczego usługi. Metody rozszerzenia na `IWorkspace` są dostępne dla usługi świadczone przez program Visual Studio, takie jak <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. Rozszerzenia mogą oferować usługi obszaru roboczego składników w ramach rozszerzenia lub używanie innych rozszerzeń. Należy używać konsumentów <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> lub metodę rozszerzenia, możesz udostępnić na `IWorkspace` typu.

>[!WARNING]
> Nie możesz tworzyć usługi, które powodują konflikt z programem Visual Studio. Może to prowadzić do nieoczekiwanych problemów.

## <a name="disposal-on-workspace-closure"></a>Sprzedaż na zamknięcia obszaru roboczego

W przypadku zamknięcia obszaru roboczego, rozszerzeń może być konieczne usunięcia, ale wywołanie asynchroniczne kodu. <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> Interfejs jest dostępny umożliwiają pisanie kodu, to proste.

## <a name="related-types"></a>Powiązanych typów

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> jest centralna jednostka dla otwarty obszar roboczy otwartym folderze.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> tworzy dostawcę danego obszaru roboczego tworzone.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> Tworzy usługę danego obszaru roboczego tworzone.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> powinny zostać wdrożone na dostawców i usługi, które wymagają do uruchomienia kodu asynchronicznego podczas usuwania.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> udostępnia metody pomocnicze do uzyskiwania dostępu do dobrze znane usługi lub dowolnych usług.

## <a name="workspace-settings"></a>Ustawienia obszaru roboczego

Obszary robocze mają <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> usługi prosty, lecz wydajny kontrolę nad obszarem roboczym. Aby uzyskać ogólne omówienie ustawienia, zobacz [Dostosowywanie kompilacji i debugowania zadań](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

Ustawienia dla większości `SettingsType` typy są _.json_ plików, takich jak _VSWorkspaceSettings.json_ i _tasks.vs.json_.

Możliwości ustawienia obszaru roboczego koncentruje się wokół "zakresów", które są po prostu ścieżki w obszarze roboczym. Gdy użytkownik wywołuje <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A>, wszystkie zakresy, które zawierają żądanej ścieżki i ustawienie typu są agregowane. Priorytet agregacji zakres jest następująca:

1. "Ustawienia lokalnego", co jest typowe w katalogu głównym obszaru roboczego `.vs` katalogu.
1. Żądana samej ścieżce.
1. Katalog nadrzędny żądanej ścieżki.
1. Wszystkie dalsze nadrzędnego katalogi, w tym katalogu głównym obszaru roboczego.
1. "Globalne ustawienia", które znajduje się w katalogu użytkownika.

Wynik jest wystąpieniem <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings>. Ten obiekt zawiera ustawienia dla danego typu i mogą być wyszukiwane Ustawianie nazw kluczy przechowywanych jako `string`. <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A> Metod i <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> metody rozszerzenia oczekują od wywołującego jest znany typ żądanej wartości ustawień. Ponieważ większość plików ustawień są utrwalane jako _.json_ plików, będzie używać wielu wywołań `string`, `bool`, `int`i tablice z tych typów. Wybierane są również obsługiwane. W takich przypadkach można użyć `IWorkspaceSettings` siebie jako argument typu. Na przykład:

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

Zakładając, że te ustawienia były użytkownika _VSWorkspaceSettings.json_, dane są dostępne jako:

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
>Ustawienia te interfejsy API są powiązane z interfejsami API dostępnymi w `Microsoft.VisualStudio.Settings` przestrzeni nazw. Ustawienia obszaru roboczego są niezależne od hosta i użyj plików ustawień specyficznych dla obszaru roboczego lub dostawców ustawień dynamicznych.

### <a name="providing-dynamic-settings"></a>Podanie ustawień dynamicznych

Rozszerzenia może zapewnić <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider>s. Tych dostawców w pamięci umożliwia rozszerzenia Dodaj ustawienia lub zastąpienia innych użytkowników.

Eksportowanie `IWorkspaceSettingsProvider` różni się od innych dostawców rozwiązań w obszarze roboczym. Fabryka nie jest `IWorkspaceProviderFactory` i nie ma żadnego typu atrybutów specjalnych. Zamiast niego należy zaimplementować <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> i użyj `[Export(typeof(IWorkspaceSettingsProviderFactory))]`.

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
>Podczas implementowania metod, które zwracają `IWorkspaceSettingsSource` (takich jak `IWorkspaceSettingsProvider.GetSingleSettings`), zwraca wystąpienie `IWorkspaceSettings` zamiast `IWorkspaceSettingsSource`. `IWorkspaceSettings` zawiera więcej informacji, które mogą być przydatne podczas agregacji niektórych ustawień.

### <a name="settings-related-apis"></a>Ustawienia związane z interfejsów API

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> odczytuje i agreguje ustawień dla obszaru roboczego.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> pobiera `IWorkspaceSettingsManager` dla obszaru roboczego.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> pobiera ustawienia dla danego zakresu agregowane w obrębie wszystkich nakładających się zakresów.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> zawiera ustawienia dla określonego zakresu.

## <a name="workspace-suggested-practices"></a>Obszar roboczy zalecane praktyki

- Zwraca obiekty z `IWorkspaceProviderFactory.CreateProvider` lub podobne interfejsy API, które należy pamiętać, ich `Workspace` kontekstu po utworzeniu. Interfejsy dostawcy są zapisywane, oczekiwano, że ten obiekt jest przechowywany przy tworzeniu.
- Zapisz pamięci podręcznych specyficznych dla obszaru roboczego lub ustawienia w ścieżce "Ustawienia lokalnego" obszaru roboczego. Utwórz ścieżkę dla pliku przy użyciu `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder` w programie Visual Studio 2017 w wersji 15.6 lub nowszej. W wersjach wcześniejszych niż w wersji 15.6 użyj następującego fragmentu kodu:

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

## <a name="solution-events-and-package-auto-load"></a>Rozwiązanie zdarzenia i automatyczne ładowanie pakiet

Załadowano pakietów można zaimplementować `IVsSolutionEvents7` i wywoływać `IVsSolution.AdviseSolutionEvents`. Obejmuje ona obsługi zdarzeń na otwierające i zamykające folderu w programie Visual Studio.

Kontekstu interfejsu użytkownika można automatycznie załadować pakietu. Wartość jest `4646B819-1AE0-4E79-97F4-8A8176FDD664`.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>Pakiet SourceExplorerPackage nie został poprawnie załadowany.

Rozszerzalność obszar roboczy jest silnie MEF oparty na i kompozycji błędy spowoduje, że pakiet, otwórz Folder, aby nie można załadować hostingu. Na przykład, jeśli rozszerzenie eksportuje typ z `ExportFileContextProviderAttribute`, ale tylko implementuje `IWorkspaceProviderFactory<IFileContextActionProvider>`, wystąpi błąd podczas próby otwarcia folderu w programie Visual Studio.

::: moniker range="vs-2017"

Szczegóły błędu znajdują się w _%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_id\ComponentModelCache\Microsoft.VisualStudio.Default.err_. Usuń wszelkie błędy typów implementowany przez Twoje rozszerzenie.

::: moniker-end

::: moniker range=">=vs-2019"

Szczegóły błędu znajdują się w _%LOCALAPPDATA%\Microsoft\VisualStudio\16.0_id\ComponentModelCache\Microsoft.VisualStudio.Default.err_. Usuń wszelkie błędy typów implementowany przez Twoje rozszerzenie.

::: moniker-end

## <a name="next-steps"></a>Następne kroki

* [Konteksty plików](workspace-file-contexts.md) -dostawców kontekstu pliku dostosowania analizy kodu dla obszarów roboczych Otwórz Folder.
* [Indeksowanie](workspace-indexing.md) -Workspace indeksowania zbiera i będzie nadal występował, informacje o obszarze roboczym.
