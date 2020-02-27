---
title: Rejestratory kompilacji | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634529"
---
# <a name="build-loggers"></a>Rejestratory kompilacji

Rejestratory umożliwiają dostosowanie danych wyjściowych kompilacji i wyświetlanie komunikatów, błędów lub ostrzeżeń w odpowiedzi na określone zdarzenia kompilacji. Każdy Rejestrator jest implementowany jako Klasa .NET implementująca interfejs <xref:Microsoft.Build.Framework.ILogger>, który jest zdefiniowany w zestawie *Microsoft. Build. Framework. dll* .

Istnieją dwie metody, których można użyć podczas implementowania rejestratora:

- Zaimplementuj interfejs <xref:Microsoft.Build.Framework.ILogger> bezpośrednio.
- Utwórz klasę z klasy pomocnika, <xref:Microsoft.Build.Utilities.Logger>, która jest zdefiniowana w zestawie *Microsoft. Build. Utilities. dll* . <xref:Microsoft.Build.Utilities.Logger> implementuje <xref:Microsoft.Build.Framework.ILogger> i udostępnia domyślne implementacje niektórych <xref:Microsoft.Build.Framework.ILogger>ych elementów członkowskich.

  W tym temacie opisano sposób pisania prostego rejestratora pochodzącego z <xref:Microsoft.Build.Utilities.Logger>i wyświetlania komunikatów w konsoli programu w odpowiedzi na niektóre zdarzenia kompilacji.

## <a name="register-for-events"></a>Rejestrowanie zdarzeń

Celem rejestratora jest zbieranie informacji o postępie kompilacji, które są zgłaszane przez aparat kompilacji, a następnie raportowanie tych informacji w przydatny sposób. Wszystkie rejestratory muszą przesłaniać metodę <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>, która wskazuje, że Rejestrator rejestruje zdarzenia. W tym przykładzie Rejestrator rejestruje dla zdarzeń <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>i <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.

[!code-csharp[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]

## <a name="respond-to-events"></a>Reagowanie na zdarzenia

Teraz, gdy Rejestrator jest zarejestrowany dla określonych zdarzeń, musi obsłużyć te zdarzenia, gdy wystąpią. W przypadku <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>i zdarzeń <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>, rejestrator po prostu zapisuje krótką frazę i nazwę pliku projektu, który jest uwzględniony w zdarzeniu. Wszystkie komunikaty z rejestratora są zapisywane w oknie konsoli.

[!code-csharp[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]

## <a name="respond-to-logger-verbosity-values"></a>Odpowiedz na wartości szczegółowości rejestratora

W niektórych przypadkach można rejestrować tylko informacje ze zdarzenia, jeśli przełącznik MSBuild. exe **-verbose** ma określoną wartość. W tym przykładzie program obsługi zdarzeń <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> rejestruje komunikat tylko wtedy, gdy właściwość <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A>, która jest ustawiona przez przełącznik o **pełnej szczegółowości** , jest równa <xref:Microsoft.Build.Framework.LoggerVerbosity>`Detailed`.

[!code-csharp[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]

## <a name="specify-a-logger"></a>Określ Rejestrator

Po skompilowaniu rejestratora do zestawu, należy powiedzieć, aby program MSBuild używał tego rejestratora podczas kompilacji. W tym celu należy użyć przełącznika **-rejestratora** w programie *MSBuild. exe*. Aby uzyskać więcej informacji na temat przełączników dostępnych dla programu *MSBuild. exe*, zobacz [informacje dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

Poniższy wiersz polecenia kompiluje projekt *WebProject. csproj* i używa klasy rejestratora zaimplementowanej w *SimpleLogger. dll*. Przełącznik **-nologo** powoduje ukrycie transparentu i komunikatu o prawach autorskich, a przełącznik **-noconsolelogger** powoduje wyłączenie domyślnego rejestratora konsoli programu MSBuild.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll
```

Następujący wiersz polecenia kompiluje projekt z tym samym rejestratorem, ale z poziomem `Verbosity` `Detailed`.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll -verbosity:Detailed
```

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład zawiera kompletny kod rejestratora.

### <a name="code"></a>Kod

[!code-csharp[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład pokazuje, jak zaimplementować rejestrator, który zapisuje dziennik w pliku zamiast wyświetlania go w oknie konsoli.

### <a name="code"></a>Kod

[!code-csharp[msbuild_BasicLogger#1](../msbuild/codesnippet/CSharp/build-loggers_5.cs)]

## <a name="see-also"></a>Zobacz też

- [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
