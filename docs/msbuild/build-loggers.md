---
title: Rejestratory kompilacji | Microsoft Docs
description: Rejestratory programu MSBuild umożliwiają zarządzanie danymi wyjściowymi kompilacji i wyświetlanie komunikatów, błędów lub ostrzeżeń w odpowiedzi na określone zdarzenia kompilacji i ich dostosowywanie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 75c06082a34f5dd3248024f1707cb188107863c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964891"
---
# <a name="build-loggers"></a>Rejestratory kompilacji

Rejestratory umożliwiają dostosowanie danych wyjściowych kompilacji i wyświetlanie komunikatów, błędów lub ostrzeżeń w odpowiedzi na określone zdarzenia kompilacji. Każdy Rejestrator jest implementowany jako Klasa platformy .NET, która implementuje <xref:Microsoft.Build.Framework.ILogger> interfejs, który jest zdefiniowany w zestawie *Microsoft.Build.Framework.dll* .

Istnieją dwie metody, których można użyć podczas implementowania rejestratora:

- Zaimplementuj <xref:Microsoft.Build.Framework.ILogger> interfejs bezpośrednio.
- Utwórz klasę z klasy pomocnika, <xref:Microsoft.Build.Utilities.Logger> która jest zdefiniowana w zestawie *Microsoft.Build.Utilities.dll* . <xref:Microsoft.Build.Utilities.Logger> implementuje <xref:Microsoft.Build.Framework.ILogger> i udostępnia domyślne implementacje niektórych <xref:Microsoft.Build.Framework.ILogger> elementów członkowskich.

  W tym temacie opisano sposób pisania prostego rejestratora pochodzącego z programu <xref:Microsoft.Build.Utilities.Logger> i wyświetlania komunikatów z konsoli programu w odpowiedzi na niektóre zdarzenia kompilacji.

## <a name="register-for-events"></a>Rejestrowanie zdarzeń

Celem rejestratora jest zbieranie informacji o postępie kompilacji, które są zgłaszane przez aparat kompilacji, a następnie raportowanie tych informacji w przydatny sposób. Wszystkie rejestratory muszą przesłaniać <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> metodę, która wskazuje, że Rejestrator rejestruje zdarzenia. W tym przykładzie Rejestrator rejestruje dla <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> zdarzeń, i <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> .

[!code-csharp[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]

## <a name="respond-to-events"></a>Reagowanie na zdarzenia

Teraz, gdy Rejestrator jest zarejestrowany dla określonych zdarzeń, musi obsłużyć te zdarzenia, gdy wystąpią. W przypadku <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> zdarzeń, <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> Rejestrator po prostu zapisuje krótką frazę i nazwę pliku projektu, który jest uwzględniony w zdarzeniu. Wszystkie komunikaty z rejestratora są zapisywane w oknie konsoli.

[!code-csharp[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]

## <a name="respond-to-logger-verbosity-values"></a>Odpowiedz na wartości szczegółowości rejestratora

W niektórych przypadkach można rejestrować tylko informacje ze zdarzenia, jeśli przełącznik MSBuild.exe **-verbose** ma określoną wartość. W tym przykładzie <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> program obsługi zdarzeń rejestruje komunikat tylko wtedy, gdy <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A> Właściwość, która jest ustawiona przez przełącznik **-verbose** , jest równa <xref:Microsoft.Build.Framework.LoggerVerbosity> `Detailed` .

[!code-csharp[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]

## <a name="specify-a-logger"></a>Określ Rejestrator

Po skompilowaniu rejestratora do zestawu, należy powiedzieć, aby program MSBuild używał tego rejestratora podczas kompilacji. W tym celu należy użyć przełącznika **-rejestratora** z *MSBuild.exe*. Aby uzyskać więcej informacji na temat przełączników dostępnych dla *MSBuild.exe*, zobacz [informacje dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

Poniższy wiersz polecenia kompiluje projekt *WebProject. csproj* i używa klasy rejestratora zaimplementowanej w *SimpleLogger.dll*. Przełącznik **-nologo** powoduje ukrycie transparentu i komunikatu o prawach autorskich, a przełącznik **-noconsolelogger** powoduje wyłączenie domyślnego rejestratora konsoli programu MSBuild.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll
```

Następujący wiersz polecenia kompiluje projekt z tym samym rejestratorem, ale z `Verbosity` poziomem `Detailed` .

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll -verbosity:Detailed
```

## <a name="example-1"></a>Przykład 1

### <a name="description"></a>Opis

Poniższy przykład zawiera kompletny kod rejestratora.

### <a name="code"></a>Kod

[!code-csharp[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]

## <a name="example-2"></a>Przykład 2

### <a name="description"></a>Opis

Poniższy przykład pokazuje, jak zaimplementować rejestrator, który zapisuje dziennik w pliku zamiast wyświetlania go w oknie konsoli.

### <a name="code"></a>Kod

[!code-csharp[msbuild_BasicLogger#1](../msbuild/codesnippet/CSharp/build-loggers_5.cs)]

## <a name="see-also"></a>Zobacz też

- [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
