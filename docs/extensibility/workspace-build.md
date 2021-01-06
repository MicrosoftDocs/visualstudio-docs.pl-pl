---
title: Kompilacja obszaru roboczego w programie Visual Studio | Microsoft Docs
description: Dowiedz się więcej na temat rozszerzenia dostarczającego dane kontekstu indeksowanego i pliku dla obszaru roboczego w celu obsługi scenariusza otwartego folderu.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: e44c2398b873bbca95c971ae1b44ac3de831b2ae
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877107"
---
# <a name="workspace-build"></a>Kompilacja obszaru roboczego

Obsługa kompilacji w scenariuszach [otwartych folderów](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) wymaga rozszerzenia, aby dostarczyć dane kontekstu [indeksowanego](workspace-indexing.md) i [pliku](workspace-file-contexts.md) dla [obszaru roboczego](workspaces.md), a także akcję kompilacji do uruchomienia.

Poniżej znajduje się zarys tego, co będzie potrzebne w Twoim rozszerzeniu.

## <a name="build-file-context"></a>Kontekst pliku kompilacji

- Fabryka dostawców
  - `ExportFileContextProviderAttribute` atrybut ze `supportedContextTypeGuids` wszystkimi stosownymi `string` stałymi z `BuildContextTypes`
  - Wprowadza `IWorkspaceProviderFactory<IFileContextProvider>`
  - Dostawca kontekstu pliku
    - Zwróć `FileContext` dla każdej operacji kompilacji i obsługiwanej konfiguracji
      - `contextType` wniosek <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` implementuje <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> z `Configuration` właściwością jako konfigurację kompilacji (na przykład `"Debug|x86"` `"ret"` , lub `null` Jeśli nie ma zastosowania). Alternatywnie możesz użyć wystąpienia <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext> . Wartość konfiguracji **musi** być zgodna z konfiguracją z indeksowanej wartości danych pliku.

## <a name="indexed-build-file-data-value"></a>Wartość danych indeksowanego pliku kompilacji

- Fabryka dostawców
  - `ExportFileScannerAttribute` atrybut z `IReadOnlyCollection<FileDataValue>` typem obsługiwanym
  - Wprowadza `IWorkspaceProviderFactory<IFileScanner>`
- Skaner plików na `ScanContentAsync<T>`
  - Zwraca dane `FileScannerTypeConstants.FileDataValuesType` , gdy jest argumentem typu
  - Zwraca wartość danych pliku dla każdej konfiguracji zbudowanej przy użyciu:
    - `type` definicj `BuildConfigurationContext.ContextTypeGuid`
    - `context` jako Konfiguracja kompilacji (na przykład, `"Debug|x86"` `"ret"` lub `null` Jeśli nie ma zastosowania). Ta wartość **musi** być zgodna z konfiguracją z kontekstu pliku.

## <a name="build-file-context-action"></a>Akcja kontekstu pliku kompilacji

- Fabryka dostawców
  - `ExportFileContextActionProvider` atrybut ze `supportedContextTypeGuids` wszystkimi stosownymi `string` stałymi z `BuildContextTypes`
  - Wprowadza `IWorkspaceProviderFactory<IFileContextActionProvider>`
- Dostawca akcji na `IFileContextActionProvider.GetActionsAsync`
  - Zwróć element `IFileContextAction` pasujący do podanej `FileContext.ContextType` wartości.
- Akcja kontekstu pliku
  - Implementuje `IFileContextAction` i <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` Zwraca wartość właściwości `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` jest `0x1000` dla kompilacji, `0x1010` na potrzeby odbudowywania lub `0x1020` czyszczenia

>[!NOTE]
>Ze względu na to, że należy `FileDataValue` indeksować, będzie pewnym czasie między otwarciem obszaru roboczego a punktem, w którym plik jest skanowany pod kątem pełnej funkcjonalności kompilacji. Opóźnienie będzie widoczne podczas pierwszego otwarcia folderu, ponieważ nie ma wcześniej zbuforowanego indeksu.

## <a name="reporting-messages-from-a-build"></a>Raportowanie komunikatów z kompilacji

Kompilacja umożliwia użytkownikom wyświetlanie informacji, ostrzeżeń i komunikatów o błędach. Prostym sposobem jest użycie <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> i podanie a, na <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage> przykład:

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Build;

private static void OutputBuildMessage(IWorkspace workspace)
{
    IBuildMessageService buildMessageService = workspace.GetBuildMessageService();

    if (buildMessageService != null)
    {
      // Example error build message. See the documentation for BuildMessage for more information.
      var message = new BuildMessage()
      {
          Type = BuildMessage.TaskType.Error,
          Code = "MY1001",
          TaskText = "This is a sample error",
          ProjectFile = "buildfile.bld",
          File = "sourcefile.src"
          LogMessage = $"This is sample text that will only go to the Build output window pane.\n"

          // And any other properties to set
      };

      buildMessageService.ReportBuildMessages(new BuildMessage[] { message });
    }
}
```

`BuildMessage.Type` i `BuildMessage.LogMessage` kontrolować zachowanie, gdzie informacje są prezentowane użytkownikowi. Każda `BuildMessage.TaskType` wartość inna niż `None` spowoduje utworzenie wpisu **Lista błędów** z danymi szczegółowymi. `LogMessage` będzie zawsze wyprowadzane w okienku **kompilacja** okna narzędzia **danych wyjściowych** .

Alternatywnie rozszerzenia mogą bezpośrednio korzystać z okienka **Lista błędów** lub **kompilacji** . Usterka istnieje w wersjach wcześniejszych niż wersja 15,7 programu Visual Studio 2017, gdzie `pszProjectUniqueName` argument <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> jest ignorowany.

>[!WARNING]
>Obiekty wywołujące `IFileContextAction.ExecuteAsync` mogą udostępniać dowolne podstawowe implementacje dla tego `IProgress<IFileContextActionProgressUpdate>` argumentu. Nigdy nie wywołuj `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` bezpośrednio. Obecnie nie ma żadnych ogólnych wytycznych dotyczących używania tego argumentu, ale te wskazówki mogą ulec zmianie.

## <a name="build-related-apis"></a>Twórz powiązane interfejsy API

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> zawiera szczegóły konfiguracji kompilacji.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> Wyświetla listę <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage> s dla użytkowników.

## <a name="tasksvsjson-and-launchvsjson"></a>tasks.vs.jswłączone i launch.vs.jsna

Aby uzyskać informacje na temat tworzenia tasks.vs.jslub launch.vs.jsna pliku, zobacz [Dostosowywanie kompilacji i debugowania zadań](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

## <a name="next-steps"></a>Następne kroki

* [Protokół serwera języka](language-server-protocol.md) — informacje na temat integrowania serwerów języków w programie Visual Studio.