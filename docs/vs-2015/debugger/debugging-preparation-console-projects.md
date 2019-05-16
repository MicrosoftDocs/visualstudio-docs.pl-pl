---
title: 'Przygotowanie debugowania: Projekty konsoli | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691218"
---
# <a name="debugging-preparation-console-projects"></a>Przygotowanie debugowania: Projekty startowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przygotowywanie do debugowania projektu konsoli jest podobny do przygotowania do debugowania projektu Windows, za pomocą kilka dodatkowych kwestii dotyczących. Aby uzyskać więcej informacji, zobacz [aplikacji z formularzem Windows](../debugger/debugging-preparation-windows-forms-applications.md), i [przygotowanie debugowania: Windows Forms aplikacji (.NET)](https://msdn.microsoft.com/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5). Z powodu podobieństwa wszystkich aplikacji konsoli w tym temacie omówiono następujące typy projektu:  
  
- Aplikacja Konsolowa C#  
  
- Aplikacja Konsolowa w języku Visual Basic  
  
- Aplikacja Konsolowa w języku C++ (platforma .NET)  
  
- Aplikacja Konsolowa w języku C++ (Win32)  
  
  Trzeba określić argumenty wiersza polecenia dla całej aplikacji konsolowej. Aby uzyskać więcej informacji, zobacz [ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [ustawienia projektu dla konfiguracji debugowania języka Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), lub [ustawienia projektu dla języka C# Debuguj konfiguracje ](../debugger/project-settings-for-csharp-debug-configurations.md).  
  
  Tak jak wszystkie właściwości projektu, te argumenty są zachowywane między sesjami debugowania oraz między sesjami programu Visual Studio. W związku z tym, jeśli aplikacja konsoli jest taki, który ma zostać wcześniej debugowane, pamiętaj, że może być argumenty z poprzedniej sesji w  **\<Projekt > strony właściwości** okno dialogowe.  
  
  Aplikacja konsoli używa **konsoli** okna, aby akceptować dane wejściowe i wyświetlić komunikaty wyjściowe. Aby zapisać **konsoli** oknie, aplikacja musi używać **konsoli** obiekt, a nie obiektu debugowania. Można zapisać do **Visual Studio dane wyjściowe** okna, użyj obiektu debugowania w zwykły sposób. Pamiętaj, że wiesz, gdzie pisania aplikacji, lub możesz poszukać komunikatów w niewłaściwym miejscu. Aby uzyskać więcej informacji, zobacz [klasy konsoli](https://msdn.microsoft.com/library/system.console.aspx), [klasy Debug](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx), i [okno danych wyjściowych](../ide/reference/output-window.md).  
  
## <a name="starting-the-application"></a>Uruchamianie aplikacji  
 Niektóre aplikacje konsoli uruchomić, zostało ukończone i zamknij. To zachowanie może nie dać wystarczająco dużo czasu na przerwanie wykonywania i debugowania. Aby można było debugować aplikację, użyj jednej z poniższych procedur do uruchamiania aplikacji:  
  
- Aplikacja uruchamia się wykonywanie i działa untils napotkania punktu przerwania.  
  
- Rozpoczyna się i natychmiast przerywa w pierwszym wierszu kodu źródłowego aplikacji.  
  
- W oknie kodu źródłowego, kliknij prawym przyciskiem myszy linię i wybierz **Uruchom do kursora**.  
  
   Aplikacja rozpoczyna się i uruchamia wybranego wiersza lub punkt przerwania, jeśli punkt przerwania zostaje trafiony przed wierszem.  
  
  Podczas debugowania aplikacji konsoli można uruchomić aplikacji z poziomu wiersza polecenia, a nie z programu Visual Studio. W takim przypadku można uruchomić aplikacji z poziomu wiersza polecenia i do niej dołączyć debuger programu Visual Studio. Aby uzyskać więcej informacji, zobacz [dołączenia do uruchamiania procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
  Po uruchomieniu aplikacji konsoli w programie Visual Studio, **konsoli** czasami za oknem programu Visual Studio zostanie wyświetlone okno. Jeśli użytkownik próbuje uruchomić aplikację konsoli w programie Visual Studio i nic nie wydaje się, że może mieć miejsce, spróbuj przenieść okna programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)   
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)   
 [Typy projektów Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#, F#i typów projektów języka Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)
