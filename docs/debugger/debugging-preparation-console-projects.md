---
title: Przygotowanie do debugowania projektów konsoli | Microsoft Docs
description: Uzyskaj informacje na temat przygotowywania do debugowania projektów konsoli (C#, C++, Visual Basic, F#) w programie Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4d1610919667fdaf1a752ca56aef5358c0bd34f3
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387817"
---
# <a name="debugging-preparation-console-projects-c-c-visual-basic-f"></a>Przygotowanie debugowania: projekty konsoli (C#, C++, Visual Basic, F#)

Przygotowanie do debugowania projektu konsoli jest podobne do przygotowania do debugowania projektu systemu Windows, z pewnymi dodatkowymi zagadnieniami, takimi jak ustawianie argumentów wiersza polecenia i sposób wstrzymywania aplikacji do debugowania. Aby uzyskać więcej informacji, zobacz [Przygotowanie debugowania dla aplikacji formularzy systemu Windows](../debugger/debugging-preparation-windows-forms-applications.md). Ze względu na podobieństwo wszystkich aplikacji konsolowych ten temat obejmuje następujące typy projektów:

- Aplikacje konsolowe C#, Visual Basic i F#

- Aplikacja konsolowa C++ (.NET)

- Aplikacja konsolowa C++ (Win32)

  Aplikacja konsolowa używa okna **Konsola do** akceptowania danych wejściowych i wyświetlania komunikatów wyjściowych. Aby zapisać w **oknie** Konsoli, aplikacja musi używać obiektu **Console** zamiast obiektu Debug. Aby zapisać w **oknie Visual Studio Dane wyjściowe,** użyj obiektu Debuguj w zwykły sposób. Upewnij się, że wiesz, gdzie jest napisana aplikacja, lub że szukasz komunikatów w niewłaściwym miejscu. Aby uzyskać więcej informacji, zobacz Console Class ( [Klasa konsoli),](/dotnet/api/system.console) [Debug Class (Klasa debugowania)](/dotnet/api/system.diagnostics.debug) [i Okno Dane wyjściowe](../ide/reference/output-window.md).

## <a name="set-command-line-arguments"></a>Ustawianie argumentów wiersza polecenia

Może być konieczne określenie argumentów wiersza polecenia dla aplikacji konsolowej. Aby uzyskać więcej informacji, zobacz Project Settings for a C++ Debug Configuration [(Ustawienia](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)projektu dla konfiguracji debugowania w języku C++), Project Settings for a Visual Basic Debug Configuration (Ustawienia projektu dla konfiguracji debugowania w języku [C++),](../debugger/project-settings-for-a-cpp-debug-configuration.md)Project Settings for a Visual Basic Debug Configuration (Ustawienia projektu dla konfiguracji [debugowania w języku C#).](../debugger/project-settings-for-csharp-debug-configurations.md)

Podobnie jak wszystkie właściwości projektu, te argumenty są utrwalane między sesjami debugowania i między Visual Studio sesji. W związku z tym, jeśli aplikacja konsolowa jest aplikacją debugowana wcześniej, należy pamiętać, że w oknie dialogowym **\<Project> Strony właściwości** mogą wystąpić argumenty z poprzednich sesji.

## <a name="start-the-application"></a>Uruchamianie aplikacji

 Po uruchomieniu niektórych aplikacji konsolowych są one uruchamiane do ukończenia, a następnie zamykane. To zachowanie może nie dać wystarczająco dużo czasu, aby przerwać wykonywanie i debugowanie. Aby można było debugować aplikację, użyj jednej z następujących procedur, aby uruchomić aplikację:

- Ustaw punkt przerwania w kodzie i uruchom aplikację.

- Uruchom aplikację przy użyciu **klawiszy F10** **(Debuguj** krok  >  **over)** lub **F11** **(Debuguj** krok  >  **do),** a następnie nawiguj po kodzie przy użyciu innych opcji, takich jak **Uruchom,** aby kliknąć pozycję .

- W edytorze kodu kliknij prawym przyciskiem myszy wiersz i wybierz polecenie **Uruchom, aby kursor**.

  Podczas debugowania aplikacji konsolowej można uruchomić aplikację z wiersza polecenia, a nie z Visual Studio. W takim przypadku możesz uruchomić aplikację z wiersza polecenia i dołączyć do Visual Studio debugera. Aby uzyskać więcej informacji, zobacz [Attach to Running Processes (Dołączanie do uruchomionych procesów).](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

  Po uruchomieniu aplikacji konsolowej z Visual Studio  czasami za tym oknem Visual Studio konsoli. Jeśli spróbujesz uruchomić aplikację konsoli z programu Visual Studio nic się nie stanie, spróbuj przenieść okno Visual Studio aplikacji.

## <a name="see-also"></a>Zobacz też
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
- [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)
- [Przygotowywanie do debugowania projektów języka C++](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Typy projektów C#, F# i Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Ustawienia projektu dla konfiguracji debugowania w języku C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Zabezpieczenia debugera](../debugger/debugger-security.md)