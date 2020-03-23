---
title: Buduj rejestratory | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a00bbb8ce239275ff140dbedf2157e4cdc41d44c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634529"
---
# <a name="build-loggers"></a>Tworzenie rejestratorów

Rejestratory umożliwiają dostosowanie danych wyjściowych kompilacji i wyświetlania komunikatów, błędów lub ostrzeżeń w odpowiedzi na określone zdarzenia kompilacji. Każdy rejestrator jest implementowany jako klasa .NET, która implementuje <xref:Microsoft.Build.Framework.ILogger> interfejs, który jest zdefiniowany w zestawie *Microsoft.Build.Framework.dll.*

Istnieją dwa podejścia, których można użyć podczas implementowania rejestratora:

- Implementuj <xref:Microsoft.Build.Framework.ILogger> interfejs bezpośrednio.
- Wywodź swoją klasę z <xref:Microsoft.Build.Utilities.Logger>klasy pomocnika, która jest zdefiniowana w zestawie *Microsoft.Build.Utilities.dll.* <xref:Microsoft.Build.Utilities.Logger>implementuje <xref:Microsoft.Build.Framework.ILogger> i zapewnia domyślne <xref:Microsoft.Build.Framework.ILogger> implementacje niektórych członków.

  W tym temacie wyjaśniono, jak napisać prosty <xref:Microsoft.Build.Utilities.Logger>rejestrator, który pochodzi od programu i wyświetla komunikaty na konsoli w odpowiedzi na określone zdarzenia kompilacji.

## <a name="register-for-events"></a>Zarejestruj się na wydarzenia

Celem rejestratora jest zebranie informacji o postępie kompilacji, ponieważ jest on zgłaszany przez aparat kompilacji, a następnie zgłaszanie tych informacji w użyteczny sposób. Wszystkie rejestratory należy zastąpić <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> metodę, która jest, gdy rejestrator rejestruje dla zdarzeń. W tym przykładzie rejestrator rejestruje <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>dla <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> i zdarzeń.

[!code-csharp[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]

## <a name="respond-to-events"></a>Reagowanie na zdarzenia

Teraz, gdy rejestrator jest zarejestrowany dla określonych zdarzeń, musi obsługiwać te zdarzenia, gdy wystąpią. W <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>przypadku <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> , i zdarzeń rejestrator po prostu zapisuje krótką frazę i nazwę pliku projektu zaangażowanego w zdarzenie. Wszystkie komunikaty z rejestratora są zapisywane w oknie konsoli.

[!code-csharp[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]

## <a name="respond-to-logger-verbosity-values"></a>Odpowiadanie na wartości szczegółowości rejestratora

W niektórych przypadkach można rejestrować tylko informacje ze zdarzenia, jeśli przełącznik MSBuild.exe **-verbosity** zawiera określoną wartość. W tym przykładzie <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> program obsługi zdarzeń rejestruje <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A> komunikat tylko wtedy, gdy właściwość ustawiona przez <xref:Microsoft.Build.Framework.LoggerVerbosity> `Detailed`przełącznik **-verbosity** jest równa .

[!code-csharp[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]

## <a name="specify-a-logger"></a>Określanie rejestratora

Gdy rejestrator jest kompilowany do zestawu, należy powiedzieć MSBuild do użycia tego rejestratora podczas kompilacji. Odbywa się to za pomocą przełącznika **-logger** z *MSBuild.exe*. Aby uzyskać więcej informacji na temat przełączników dostępnych dla *pliku MSBuild.exe*, zobacz [Odwołanie do wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

Następujący wiersz polecenia tworzy projekt *MyProject.csproj* i używa klasy rejestratora zaimplementowanego w *pliku SimpleLogger.dll*. Przełącznik **-nologo** ukrywa baner i komunikat o prawach autorskich, a przełącznik **-noconsolelogger** wyłącza domyślny rejestrator konsoli MSBuild.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll
```

Poniższy wiersz polecenia tworzy projekt z tym samym `Verbosity` rejestratorem, ale z poziomem `Detailed`.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll -verbosity:Detailed
```

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład zawiera pełny kod rejestratora.

### <a name="code"></a>Code

[!code-csharp[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

W poniższym przykładzie pokazano, jak zaimplementować rejestratora, który zapisuje dziennik do pliku, a nie wyświetla go w oknie konsoli.

### <a name="code"></a>Code

[!code-csharp[msbuild_BasicLogger#1](../msbuild/codesnippet/CSharp/build-loggers_5.cs)]

## <a name="see-also"></a>Zobacz też

- [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Koncepcje MSBuild](../msbuild/msbuild-concepts.md)
