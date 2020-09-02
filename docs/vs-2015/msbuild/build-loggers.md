---
title: Rejestratory kompilacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2908c8217070196de1b2d3cd4f1c5f8d8f2868a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160432"
---
# <a name="build-loggers"></a>Rejestratory kompilacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rejestratory umożliwiają dostosowanie danych wyjściowych kompilacji i wyświetlanie komunikatów, błędów lub ostrzeżeń w odpowiedzi na określone zdarzenia kompilacji. Każdy Rejestrator jest implementowany jako Klasa platformy .NET, która implementuje <xref:Microsoft.Build.Framework.ILogger> interfejs, który jest zdefiniowany w zestawie Microsoft.Build.Framework.dll.  
  
 Istnieją dwie metody, których można użyć podczas implementowania rejestratora:  
  
- Zaimplementuj <xref:Microsoft.Build.Framework.ILogger> interfejs bezpośrednio.  
  
- Utwórz klasę z klasy pomocnika, <xref:Microsoft.Build.Utilities.Logger> która jest zdefiniowana w zestawie Microsoft.Build.Utilities.dll. <xref:Microsoft.Build.Utilities.Logger> implementuje <xref:Microsoft.Build.Framework.ILogger> i udostępnia domyślne implementacje niektórych <xref:Microsoft.Build.Framework.ILogger> elementów członkowskich.  
  
  W tym temacie opisano sposób pisania prostego rejestratora pochodzącego z programu <xref:Microsoft.Build.Utilities.Logger> i wyświetlania komunikatów z konsoli programu w odpowiedzi na niektóre zdarzenia kompilacji.  
  
## <a name="registering-for-events"></a>Rejestrowanie zdarzeń  
 Celem rejestratora jest zbieranie informacji o postępie kompilacji, które są zgłaszane przez aparat kompilacji, a następnie raportowanie tych informacji w przydatny sposób. Wszystkie rejestratory muszą przesłaniać <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> metodę, która wskazuje, że Rejestrator rejestruje zdarzenia. W tym przykładzie Rejestrator rejestruje dla <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> zdarzeń, i <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> .  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#2](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs#2)]  
  
## <a name="responding-to-events"></a>Reagowanie na zdarzenia  
 Teraz, gdy Rejestrator jest zarejestrowany dla określonych zdarzeń, musi obsłużyć te zdarzenia, gdy wystąpią. W przypadku <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> zdarzeń, <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> Rejestrator po prostu zapisuje krótką frazę i nazwę pliku projektu, który jest uwzględniony w zdarzeniu. Wszystkie komunikaty z rejestratora są zapisywane w oknie konsoli.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#3](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs#3)]  
  
## <a name="responding-to-logger-verbosity-values"></a>Reagowanie na wartości szczegółowości rejestratora  
 W niektórych przypadkach może być konieczne zarejestrowanie informacji ze zdarzenia tylko wtedy, gdy przełącznik MSBuild.exe **/verbosity.** zawiera określoną wartość. W tym przykładzie <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> program obsługi zdarzeń rejestruje komunikat tylko wtedy <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A> , gdy właściwość, która jest ustawiona przez przełącznik **/verbosity.** , jest równa <xref:Microsoft.Build.Framework.LoggerVerbosity> `Detailed` .  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#4](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs#4)]  
  
## <a name="specifying-a-logger"></a>Określanie rejestratora  
 Po skompilowaniu rejestratora do zestawu, należy powiedzieć [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , aby użyć tego rejestratora podczas kompilacji. W tym celu należy użyć przełącznika **/Logger** z MSBuild.exe. Aby uzyskać więcej informacji na temat przełączników dostępnych dla MSBuild.exe, zobacz [informacje dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md).  
  
 Poniższy wiersz polecenia kompiluje projekt `MyProject.csproj` i używa klasy rejestratora wdrożonej w `SimpleLogger.dll` . Przełącznik **/nologo** ukrywa transparent i wiadomość o prawach autorskich, a przełącznik **/noconsolelogger** powoduje wyłączenie domyślnego [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] rejestratora konsoli.  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll  
```  
  
 Następujący wiersz polecenia kompiluje projekt z tym samym rejestratorem, ale z `Verbosity` poziomem `Detailed` .  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll /verbosity:Detailed  
```  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład zawiera kompletny kod rejestratora.  
  
### <a name="code"></a>Kod  
 [!code-csharp[msbuild_SimpleConsoleLogger#1](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs#1)]  
  
### <a name="comments"></a>Komentarze  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład pokazuje, jak zaimplementować rejestrator, który zapisuje dziennik w pliku zamiast wyświetlania go w oknie konsoli.  
  
### <a name="code"></a>Kod  
 [!code-csharp[msbuild_BasicLogger#1](../snippets/csharp/VS_Snippets_Misc/msbuild_BasicLogger/CS/msbuild_BasicLogger.cs#1)]  
  
### <a name="comments"></a>Komentarze  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
