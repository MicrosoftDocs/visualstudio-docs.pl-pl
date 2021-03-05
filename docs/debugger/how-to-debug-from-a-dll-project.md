---
title: Debugowanie z projektu DLL | Microsoft Docs
description: Debugowanie projektu DLL można rozpocząć od samego projektu, określając aplikację wywołującą we właściwościach projektu. Zobacz ten artykuł, aby uzyskać szczegółowe informacje.
ms.custom: SEO-VS-2020
ms.date: 10/10/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1f6063c5a0343951bb098c6937ce13dac7100d4a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160438"
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio-c-c-visual-basic-f"></a>Instrukcje: debugowanie z projektu DLL w programie Visual Studio (C#, C++, Visual Basic, F #)

Jednym ze sposobów debugowania projektu DLL jest określenie aplikacji wywołującej we właściwościach projektu DLL. Następnie można rozpocząć debugowanie z projektu DLL. Aby ta metoda działała, aplikacja musi wywołać tę samą bibliotekę DLL w tej samej lokalizacji co konfiguracja, którą konfigurujesz. Jeśli aplikacja znajdzie i załaduje inną wersję biblioteki DLL, ta wersja nie będzie zawierać punktów przerwania. Aby poznać inne metody debugowania DLL, zobacz [Debugowanie projektów DLL](../debugger/debugging-dll-projects.md).

Jeśli zarządzana aplikacja wywołuje natywną bibliotekę DLL lub Natywna aplikacja wywołuje zarządzaną bibliotekę DLL, można debugować zarówno bibliotekę DLL, jak i aplikację wywołującą. Aby uzyskać więcej informacji, zobacz [jak: debugowanie w trybie mieszanym](../debugger/how-to-debug-in-mixed-mode.md).

Natywne i zarządzane projekty DLL mają różne ustawienia, aby określić aplikacje wywołujące.

## <a name="specify-a-calling-app-in-a-native-dll-project"></a>Określ aplikację wywołującą w macierzystym projekcie DLL

1. Wybierz projekt biblioteki DLL C++ w **Eksplorator rozwiązań**. Wybierz ikonę **Właściwości** , naciśnij klawisz **Alt** + **Enter** lub kliknij prawym przyciskiem myszy i wybierz polecenie **Właściwości**.

1. W oknie dialogowym **\<Project> strony właściwości** upewnij się, że pole **konfiguracji** w górnej części okna ma wartość **Debuguj**.

1. Wybierz pozycję Debugowanie **Właściwości konfiguracji**  >  .

1. Na liście **debuger do uruchomienia** wybierz pozycję **lokalny debuger systemu Windows** lub **zdalny debuger systemu Windows**.

1. W oknie **polecenia** lub **zdalne** Dodaj w pełni kwalifikowaną ścieżkę i nazwę pliku aplikacji wywołującej, na przykład plik *. exe* .

   ![Debuguj okno Właściwości](../debugger/media/dbg-debugging-properties-dll.png "Debuguj okno Właściwości")

1. Dodaj wszelkie niezbędne argumenty programu do pola **argumenty polecenia** .

1. Wybierz przycisk **OK**.

## <a name="specify-a-calling-app-in-a-managed-dll-project"></a>Określanie aplikacji wywołującej w zarządzanym projekcie DLL

1. Wybierz projekt C# lub Visual Basic DLL w **Eksplorator rozwiązań**. Wybierz ikonę **Właściwości** , naciśnij klawisz **Alt** + **Enter** lub kliknij prawym przyciskiem myszy i wybierz polecenie **Właściwości**.

1. Upewnij się, że pole **konfiguracji** w górnej części okna ma wartość **Debuguj**.

1. W obszarze **Akcja początkowa**:

   - W przypadku bibliotek DLL .NET Framework wybierz pozycję **Uruchom program zewnętrzny**, a następnie Dodaj w pełni kwalifikowaną ścieżkę i nazwę aplikacji wywołującej.

   - Lub wybierz pozycję **Uruchom przeglądarkę z adresem URL** i wprowadź adres URL lokalnej aplikacji ASP.NET.

   - W przypadku bibliotek dll platformy .NET Core Strona właściwości **debugowania** jest inna. Wybierz z listy rozwijanej **Uruchom** **plik wykonywalny** , a następnie Dodaj w pełni kwalifikowaną ścieżkę i nazwę aplikacji wywołującej w polu **wykonywalnym** .

1. Dodaj wszelkie wymagane argumenty wiersza polecenia w **argumentach wiersza polecenia** lub w polu **argumenty aplikacji** .

   ![Okno Właściwości debugowania C#](../debugger/media/dbg-debugging-properties-dll-csharp.png "Okno Właściwości debugowania C#")

1. Użyj   >  **pozycji Zapisz wybrane elementy** lub **Ctrl** + **S** , aby zapisać zmiany.

## <a name="debug-from-the-dll-project"></a>Debugowanie z projektu DLL

1. Ustaw punkty przerwania w projekcie DLL.

1. Kliknij prawym przyciskiem myszy projekt DLL i wybierz polecenie **Ustaw jako projekt startowy**.

1. Upewnij się, że w polu **Konfiguracja rozwiązań** jest ustawiona wartość **Debuguj**. Naciśnij klawisz **F5**, kliknij zieloną strzałkę **startową** lub wybierz **Debuguj**  >  **Rozpocznij debugowanie**.

Jeśli debugowanie nie trafi w punkty przerwania, upewnij się, że dane wyjściowe biblioteki DLL (domyślnie folder *\<project> \debug.* ) są lokalizacją, którą wywołuje aplikacja wywołująca.

## <a name="see-also"></a>Zobacz też
- [Debugowanie projektów DLL](../debugger/debugging-dll-projects.md)
- [Ustawienia projektu dla konfiguracji debugowania w języku C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Ustawienia projektu dla konfiguracji debugowania w języku Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Ustawienia projektu dla konfiguracji debugowania w języku C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
