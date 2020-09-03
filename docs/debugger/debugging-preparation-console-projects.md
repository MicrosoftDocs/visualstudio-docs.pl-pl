---
title: Przygotowanie do debugowania projektów konsoli | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e612228bf5440936c336d286962820a02d6bd071
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916273"
---
# <a name="debugging-preparation-console-projects-c-c-visual-basic-f"></a>Przygotowanie debugowania: Projekty konsoli (C#, C++, Visual Basic, F #)

Przygotowanie do debugowania projektu konsoli jest podobne do przygotowania do debugowania projektu systemu Windows, z kilkoma dodatkowymi zagadnieniami, takimi jak argumenty wiersza polecenia i jak wstrzymać debugowanie aplikacji. Aby uzyskać więcej informacji, zobacz [Windows Forms aplikacji](../debugger/debugging-preparation-windows-forms-applications.md)i [Przygotowanie debugowania: aplikacje Windows Forms (.NET)](/previous-versions/visualstudio/visual-studio-2010/sez9z95a(v=vs.100)). Ze względu na podobieństwo wszystkich aplikacji konsolowych w tym temacie omówiono następujące typy projektów:

- Aplikacja konsolowa C#, Visual Basic i języka F #

- Aplikacja konsolowa C++ (.NET)

- Aplikacja konsolowa C++ (Win32)

  Aplikacja konsolowa używa okna **konsoli** , aby akceptować dane wejściowe i wyświetlać komunikaty wyjściowe. Aby zapisać w oknie **konsoli** , aplikacja musi używać obiektu **konsoli** zamiast obiektu debugowania. Aby zapisać w oknie **danych wyjściowych programu Visual Studio** , użyj obiektu Debug w zwykły sposób. Upewnij się, że wiesz, gdzie aplikacja jest zapisywany, lub Szukaj komunikatów w niewłaściwym miejscu. Aby uzyskać więcej informacji, zobacz [Klasa konsoli](/dotnet/api/system.console), [klasa debugowania](/dotnet/api/system.diagnostics.debug)i [okno dane wyjściowe](../ide/reference/output-window.md).

## <a name="set-command-line-arguments"></a>Ustawianie argumentów wiersza polecenia

Może być konieczne określenie argumentów wiersza polecenia dla aplikacji konsolowej. Aby uzyskać więcej informacji, zobacz [Ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [Ustawienia projektu dla konfiguracji debugowania Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)lub [Ustawienia projektu dla konfiguracji debugowania w języku C#](../debugger/project-settings-for-csharp-debug-configurations.md).

Podobnie jak wszystkie właściwości projektu, te argumenty są utrwalane między sesjami debugowania i między sesjami programu Visual Studio. W związku z tym, jeśli aplikacja konsolowa jest już debugowana, należy pamiętać, że w oknie dialogowym ** \<Project> strony właściwości** mogą istnieć argumenty z poprzednich sesji.

## <a name="start-the-application"></a>Uruchamianie aplikacji

 Po uruchomieniu niektórych aplikacji konsolowych są one uruchamiane do zakończenia, a następnie opuszcza. Takie zachowanie może nie dać wystarczającej ilości czasu na przerwanie wykonywania i debugowania. Aby móc debugować aplikację, użyj jednej z następujących procedur, aby uruchomić aplikację:

- Ustaw punkt przerwania w kodzie i uruchom aplikację.

- Uruchom aplikację przy użyciu klawisza **F10** (**Debuguj**  >  **krok**od) lub**Debug** **F11** (  >  **Wkrocz krok do**), a następnie przejdź przez kod przy użyciu innych opcji, takich jak **Uruchom do kliknięcia**.

- W edytorze kodu kliknij prawym przyciskiem myszy wiersz i wybierz polecenie **Uruchom do kursora**.

  Podczas debugowania aplikacji konsolowej można uruchomić aplikację z poziomu wiersza polecenia, a nie z programu Visual Studio. W takim przypadku można uruchomić aplikację z wiersza polecenia i dołączyć do niej debuger programu Visual Studio. Aby uzyskać więcej informacji, zobacz [dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

  Po uruchomieniu aplikacji konsolowej z programu Visual Studio okno **konsoli** czasami pojawia się za oknem programu Visual Studio. Jeśli spróbujesz uruchomić aplikację konsolową z programu Visual Studio i nic się nie dzieje, spróbuj przenieść okno programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
- [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)
- [Przygotowanie do debugowania projektów C++](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Typy projektów C#, F# i Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Ustawienia projektu dla konfiguracji debugowania w C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Zabezpieczenia debugera](../debugger/debugger-security.md)