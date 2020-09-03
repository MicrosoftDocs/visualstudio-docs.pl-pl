---
title: 'Przygotowanie debugowania: Projekty konsoli | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ac87f6c5ef5fcf9fc7ca5532fe7436dedb8ba97
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691218"
---
# <a name="debugging-preparation-console-projects"></a>Przygotowanie debugowania: projekty konsoli
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przygotowanie do debugowania projektu konsoli jest podobne do przygotowania do debugowania projektu systemu Windows z kilkoma dodatkowymi zagadnieniami. Aby uzyskać więcej informacji, zobacz [Windows Forms aplikacji](../debugger/debugging-preparation-windows-forms-applications.md)i [Przygotowanie debugowania: aplikacje Windows Forms (.NET)](https://msdn.microsoft.com/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5). Ze względu na podobieństwo wszystkich aplikacji konsolowych w tym temacie omówiono następujące typy projektów:  
  
- Aplikacja konsolowa C#  
  
- Aplikacja konsolowa Visual Basic  
  
- Aplikacja konsolowa C++ (.NET)  
  
- Aplikacja konsolowa C++ (Win32)  
  
  Może być konieczne określenie argumentów wiersza polecenia dla aplikacji konsolowej. Aby uzyskać więcej informacji, zobacz [Ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [Ustawienia projektu dla konfiguracji debugowania Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)lub [Ustawienia projektu dla konfiguracji debugowania w języku C#](../debugger/project-settings-for-csharp-debug-configurations.md).  
  
  Podobnie jak wszystkie właściwości projektu, te argumenty są utrwalane między sesjami debugowania i między sesjami programu Visual Studio. W związku z tym, jeśli aplikacja konsolowa jest już debugowana, należy pamiętać, że w oknie dialogowym ** \<Project> strony właściwości** mogą istnieć argumenty z poprzednich sesji.  
  
  Aplikacja konsolowa używa okna **konsoli** , aby akceptować dane wejściowe i wyświetlać komunikaty wyjściowe. Aby zapisać w oknie **konsoli** , aplikacja musi używać obiektu **konsoli** zamiast obiektu debugowania. Aby zapisać w oknie **danych wyjściowych programu Visual Studio** , użyj obiektu Debug w zwykły sposób. Upewnij się, że wiesz, gdzie aplikacja jest zapisywany, lub Szukaj komunikatów w niewłaściwym miejscu. Aby uzyskać więcej informacji, zobacz [Klasa konsoli](https://msdn.microsoft.com/library/system.console.aspx), [klasa debugowania](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx)i [okno dane wyjściowe](../ide/reference/output-window.md).  
  
## <a name="starting-the-application"></a>Uruchamianie aplikacji  
 Po uruchomieniu niektórych aplikacji konsolowych są one uruchamiane do zakończenia, a następnie opuszcza. Takie zachowanie może nie dać wystarczającej ilości czasu na przerwanie wykonywania i debugowania. Aby móc debugować aplikację, użyj jednej z następujących procedur, aby uruchomić aplikację:  
  
- Aplikacja uruchamia wykonywanie i uruchamia się do momentu osiągnięcia punktu przerwania.  
  
- Aplikacja zaczyna i od razu dzieli się w pierwszym wierszu kodu źródłowego.  
  
- W oknie kod źródłowy kliknij prawym przyciskiem myszy wiersz i wybierz polecenie **Uruchom do kursora**.  
  
   Aplikacja jest uruchamiana i uruchamiana w wybranym wierszu lub w punkcie przerwania, jeśli punkt przerwania zostanie osiągnięty przed wierszem.  
  
  Podczas debugowania aplikacji konsolowej można uruchomić aplikację z poziomu wiersza polecenia, a nie z programu Visual Studio. W takim przypadku można uruchomić aplikację z wiersza polecenia i dołączyć do niej debuger programu Visual Studio. Aby uzyskać więcej informacji, zobacz [dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
  Po uruchomieniu aplikacji konsolowej z programu Visual Studio okno **konsoli** czasami pojawia się za oknem programu Visual Studio. Jeśli spróbujesz uruchomić aplikację konsolową z programu Visual Studio i nic się nie dzieje, spróbuj przenieść okno programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)   
 [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)   
 [Visual C++ typy projektów](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Typy projektów C#, F # i Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)
