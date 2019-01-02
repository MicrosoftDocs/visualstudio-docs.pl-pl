---
title: Rejestratory kompilacji | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1df3eea826f2b439d2dfb9d6607c1afded80421
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914004"
---
# <a name="build-loggers"></a>Rejestratory kompilacji
Rejestratory umożliwiają umożliwiające dostosowanie dane wyjściowe kompilacji i wyświetlanie wiadomości, błędy lub ostrzeżenia w odpowiedzi na zdarzenia w konkretnej kompilacji. Każdy rejestrator jest implementowany jako klasa .NET, która implementuje <xref:Microsoft.Build.Framework.ILogger> interfejs, który jest zdefiniowany w *Microsoft.Build.Framework.dll* zestawu.  
  
 Istnieją dwie metody, których można użyć podczas implementowania Rejestrator:  
  
- Implementowanie <xref:Microsoft.Build.Framework.ILogger> interfejs bezpośrednio.  
  
- Pochodną klasy z klasy Pomocnika <xref:Microsoft.Build.Utilities.Logger>, który jest zdefiniowany w *Microsoft.Build.Utilities.dll* zestawu. <xref:Microsoft.Build.Utilities.Logger> implementuje <xref:Microsoft.Build.Framework.ILogger> i zawiera domyślne implementacje niektórych <xref:Microsoft.Build.Framework.ILogger> elementów członkowskich.  
  
  W tym temacie wyjaśniono, jak napisać prosty rejestratora, która pochodzi od klasy <xref:Microsoft.Build.Utilities.Logger>, i wyświetla komunikaty na konsoli w odpowiedzi na niektóre zdarzenia kompilacji.  
  
## <a name="register-for-events"></a>Rejestrowanie zdarzeń  
 Rejestrator ma na celu zbierania informacji o postępie kompilacji, zgłoszonej przez aparat kompilacji, a następnie zgłaszanie tych informacji w wygodny sposób. Należy zastąpić wszystkie rejestratory <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> metoda, która jest, gdy rejestruje rejestratora dla zdarzeń. W tym przykładzie rejestruje rejestratora <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>, i <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> zdarzenia.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]  
  
## <a name="respond-to-events"></a>Odpowiadanie na zdarzenia  
 Teraz, gdy rejestratora jest zarejestrowany dla określonych zdarzeń, musi obsługiwać te wydarzenia w momencie ich wystąpienia. Aby uzyskać <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>, i <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> zdarzenia, rejestratora zapisuje po prostu krótkich fraz i nazwę pliku projektu zaangażowanych w zdarzeniu. Wszystkie komunikaty z Rejestratora są zapisywane w oknie konsoli.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]  
  
## <a name="respond-to-logger-verbosity-values"></a>Reagowanie na wartości poziom szczegółowości rejestratora  
 W niektórych przypadkach możesz tylko rejestrować informacje ze zdarzenia, jeśli MSBuild.exe **— poziom szczegółowości** przełącznik zawiera określoną wartość. W tym przykładzie <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> programu obsługi zdarzeń tylko rejestruje wiadomość, jeśli <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A> właściwość, która została ustawiona przez **— poziom szczegółowości** przełącznika, jest równa <xref:Microsoft.Build.Framework.LoggerVerbosity> `Detailed`.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]  
  
## <a name="specify-a-logger"></a>Określ Rejestrator  
 Gdy rejestratora jest kompilowany do zestawu, należy przekazać [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do użycia tego rejestratora podczas kompilacji. Odbywa się przy użyciu **-rejestratora** przełącznik z *MSBuild.exe*. Aby uzyskać więcej informacji na temat parametrów, które są dostępne dla *MSBuild.exe*, zobacz [wiersza polecenia](../msbuild/msbuild-command-line-reference.md).  
  
 Następujące polecenie w wierszu tworzy projekt *MyProject.csproj* i wykorzystuje klasy rejestratora zaimplementowane w *SimpleLogger.dll*. **- Nologo** przełącznika ukrywa transparent i komunikat o prawach autorskich oraz **- noconsolelogger** przełącznika wyłącza domyślne [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] rejestratora konsoli.  
  
```cmd  
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll  
```  
  
 Następujące polecenie w wierszu tworzy projekt za pomocą tego samego rejestratora, ale z `Verbosity` poziom `Detailed`.  
  
```cmd  
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll -verbosity:Detailed  
```  

## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład zawiera kompletny kod dla rejestratora.  
  
### <a name="code"></a>Kod  
 [!code-csharp[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład pokazuje, jak zaimplementować rejestrator, który zapisuje dziennik do pliku, a nie jej wyświetlania w oknie konsoli.  
  
### <a name="code"></a>Kod  
 [!code-csharp[msbuild_BasicLogger#1](../msbuild/codesnippet/CSharp/build-loggers_5.cs)]  
  
## <a name="see-also"></a>Zobacz także  
 [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)