---
title: Obszar roboczy kompilacji w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 82660ee772280563b91830aaf1a18da0bc742b28
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55951231"
---
# <a name="workspace-build"></a>Obszar roboczy kompilacji

Obsługa narzędzia Build [Otwórz Folder](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) scenariuszy wymaga urządzenia extender, aby dostarczyć [indeksowane](workspace-indexing.md) i [kontekstu pliku](workspace-file-contexts.md) dane [obszaru roboczego](workspaces.md), jako dobrze jako akcji kompilacji do uruchomienia.

Poniżej przedstawiono zarys co będzie potrzebne Twoje rozszerzenie.

## <a name="build-file-context"></a>Tworzenie kontekstu pliku

- Fabryki dostawców
  - `ExportFileContextProviderAttribute` atrybutem `supportedContextTypeGuids` we wszystkich odpowiednich `string` stałe od `BuildContextTypes`
  - Implementuje `IWorkspaceProviderFactory<IFileContextProvider>`
  - Dostawca kontekstu pliku
    - Zwróć `FileContext` dla każdej kompilacji, działania i konfiguracja jest obsługiwana
      - `contextType` Z <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` implementuje <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> z `Configuration` właściwość jako konfiguracji kompilacji (na przykład `"Debug|x86"`, `"ret"`, lub `null` Jeśli nie ma to zastosowanie). Można również użyć wystąpienia <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext>. Wartość konfiguracji **musi** zgodna z konfiguracją z indeksowanej pliku wartości danych.

## <a name="indexed-build-file-data-value"></a>Wartość danych pliku indeksowanych kompilacji

- Fabryki dostawców
  - `ExportFileScannerAttribute` atrybutem `IReadOnlyCollection<FileDataValue>` jako obsługiwanego typu
  - Implementuje `IWorkspaceProviderFactory<IFileScanner>`
- Skaner plik na `ScanContentAsync<T>`
  - Zwraca dane podczas `FileScannerTypeConstants.FileDataValuesType` jest argumentem typu
  - Zwraca wartość danych pliku dla każdej konfiguracji skonstruowany przy użyciu:
    - `type` jako `BuildConfigurationContext.ContextTypeGuid`
    - `context` jako konfiguracji kompilacji (na przykład `"Debug|x86"`, `"ret"`, lub `null` Jeśli nie ma to zastosowanie). Ta wartość **musi** zgodna z konfiguracją z kontekstu pliku.

## <a name="build-file-context-action"></a>Akcja kontekstu pliku kompilacji

- Fabryki dostawców
  - `ExportFileContextActionProvider` atrybutem `supportedContextTypeGuids` we wszystkich odpowiednich `string` stałe od `BuildContextTypes`
  - Implementuje `IWorkspaceProviderFactory<IFileContextActionProvider>`
- Dostawca akcji na `IFileContextActionProvider.GetActionsAsync`
  - Zwróć `IFileContextAction` odpowiadający danej `FileContext.ContextType` wartość
- Akcja kontekstu pliku
  - Implementuje `IFileContextAction` i <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` Zwraca właściwość `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` jest `0x1000` dla kompilacji, `0x1010` do ponownej kompilacji, lub `0x1020` do czyszczenia

>[!NOTE]
>Ponieważ `FileDataValue` musi zostać pomyślnie zindeksowane, będzie istnieć pewne ilość czasu między otwierając obszar roboczy i punkt, w którym plik jest skanowany pod kątem kompilacji pełne funkcje. Opóźnienie będą widoczne na potrzeby otwierania folderu, ponieważ brak indeksu wcześniej w pamięci podręcznej.

## <a name="reporting-messages-from-a-build"></a>Raportowanie wiadomości z kompilacji

Kompilacja, może pojawić się informacje, ostrzeżenia i komunikaty o błędach dla użytkowników jeden z dwóch sposobów. Prosty sposób polega na użyciu <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> i podaj <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>, w następujący sposób:

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

`BuildMessage.Type` i `BuildMessage.LogMessage` kontrolują zachowanie, o których informacje są prezentowane użytkownikowi. Wszelkie `BuildMessage.TaskType` wartości innych niż `None` dadzą **lista błędów** wpis z podanych szczegółów. `LogMessage` zawsze będą dane wyjściowe w **kompilacji** okienku **dane wyjściowe** okna narzędzi.

Alternatywnie rozszerzenia może bezpośrednio współdziałać z **lista błędów** lub **kompilacji** okienka. W wersjach wcześniejszych niż Visual Studio 2017 w wersji 15.7 istnieje usterkę gdzie `pszProjectUniqueName` argument <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> jest ignorowana.

>[!WARNING]
>Obiektów wywołujących `IFileContextAction.ExecuteAsync` może zapewnić dowolnego bazowego niedotyczące `IProgress<IFileContextActionProgressUpdate>` argumentu. Nigdy nie wywołania `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` bezpośrednio. Obecnie nie istnieją żadne ogólne wytyczne dotyczące korzystania z tego argumentu, ale te wytyczne mogą ulec zmianie.

## <a name="build-related-apis"></a>Interfejsy API skojarzone z kompilacji

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> szczegółowe informacje o konfiguracji kompilacji.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> Pokazuje <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>s dla użytkowników.

## <a name="tasksvsjson-and-launchvsjson"></a>Tasks.VS.JSON i pliku launch.vs.json

Aby uzyskać informacji na temat tworzenia pliku tasks.vs.json lub pliku launch.vs.json, zobacz [Dostosowywanie kompilacji i debugowania zadań](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

## <a name="next-steps"></a>Następne kroki

* [Language Server Protocol](language-server-protocol.md) — Dowiedz się, jak zintegrować serwerach w wersji językowej programu Visual Studio.