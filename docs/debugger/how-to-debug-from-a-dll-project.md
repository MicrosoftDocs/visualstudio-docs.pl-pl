---
title: 'Instrukcje: Debugowanie z projektu DLL | Dokumentacja firmy Microsoft'
ms.date: 10/10/2018
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6dd7ec8938b8b7f94ba649affe48f170172f887b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854077"
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio-c-c-visual-basic-f"></a>Instrukcje: Debugowanie z projektu DLL w programie Visual Studio (C#, C++, Visual Basic F#)

Jednym ze sposobów, aby debugować projekt DLL jest do określenia aplikacji wywołującej we właściwościach projektu biblioteki DLL. Możesz następnie rozpocząć debugowanie z projektu DLL. Dla tej metody do pracy aplikacja musi wywoływać tej samej biblioteki DLL w tej samej lokalizacji, który można skonfigurować. Jeśli aplikacja wykryje i ładuje inną wersję biblioteki DLL, ta wersja nie będzie zawierał punktów przerwania. Aby uzyskać inne metody debugowanie bibliotek DLL, zobacz [projektów DLL debugowania](../debugger/debugging-dll-projects.md).
  
Jeśli Twojej aplikacji zarządzanej wywołuje natywnej biblioteki DLL lub aplikacji natywnej wywołuje zarządzanej biblioteki DLL, można debugować zarówno biblioteki DLL i wywołania aplikacji. Aby uzyskać więcej informacji, zobacz [jak: Debugowanie w trybie mieszanym](../debugger/how-to-debug-in-mixed-mode.md).   

Natywne i zarządzane projekty biblioteki DLL mają różne ustawienia, aby określić aplikacje. 

## <a name="specify-a-calling-app-in-a-native-dll-project"></a>Określanie aplikacji wywołującej w natywnego projektu biblioteki DLL  
  
1. Wybierz projekt DLL języka C++ w **Eksploratora rozwiązań**. Wybierz **właściwości** ikonę, naciśnij klawisz **Alt**+**Enter**, lub kliknij prawym przyciskiem myszy i wybierz pozycję **właściwości**.
   
1. W  **\<Projekt > strony właściwości** okna dialogowego upewnij się, **konfiguracji** polu w górnej części okna jest ustawiana **debugowania**. 
   
1. Wybierz **właściwości konfiguracji** > **debugowania**.  
   
1. W **debuger do uruchomienia** , wybierz opcję **lokalny debuger Windows** lub **zdalny debuger Windows**.  
   
1. W **polecenia** lub **polecenia zdalnego** Dodaj pełną ścieżkę i nazwę pliku w aplikacji wywołującej, takich jak *.exe* pliku.
   
   ![Okno właściwości debugowania](../debugger/media/dbg-debugging-properties-dll.png "okno Właściwości debugowania")  
   
1. Dodaj argumenty programu niezbędne do **argumenty wiersza polecenia** pole.  
   
1. Kliknij przycisk **OK**.

## <a name="specify-a-calling-app-in-a-managed-dll-project"></a>Określanie aplikacji wywołującej w zarządzanego projektu biblioteki DLL  
  
1. Wybierz projekt C# lub Visual Basic DLL w **Eksploratora rozwiązań**. Wybierz **właściwości** ikonę, naciśnij klawisz **Alt**+**Enter**, lub kliknij prawym przyciskiem myszy i wybierz pozycję **właściwości**.
   
1. Upewnij się, że **konfiguracji** polu w górnej części okna jest ustawiana **debugowania**.
   
1. W obszarze **Akcja uruchamiania**:
   
   - Dla bibliotek DLL programu .NET Framework, wybierz **uruchomienia programu zewnętrznego**Dodaj pełną ścieżkę i nazwę aplikacji wywołującej.
     
   - Lub wybierz **uruchamiania przeglądarki z adresem URL** i wprowadź adres URL lokalnej aplikacji ASP.NET. 
   
   - Dla bibliotek DLL programu .NET Core **debugowania** różni się Strona właściwości. Wybierz **plik wykonywalny** z **Uruchom** listy rozwijanej, a następnie dodaj pełną ścieżkę i nazwę aplikacji wywołującej **plik wykonywalny** pola. 
   
1. Dodaj argumenty wiersza polecenia niezbędne w **argumenty wiersza polecenia** lub **argumenty aplikacji** pola.
   
   ![Okno właściwości języka C# debugowania](../debugger/media/dbg-debugging-properties-dll-csharp.png "C# debugowanie okna właściwości") 
   
1. Użyj **pliku** > **Zapisz wybrane elementy** lub **Ctrl**+**S** można zapisać zmian.

## <a name="debug-from-the-dll-project"></a>Debugowanie z projektu DLL  
 
1. Ustaw punkty przerwania w projekcie biblioteki DLL.

1. Kliknij prawym przyciskiem myszy projekt DLL, a następnie wybierz **Ustaw jako projekt startowy**. 

1. Upewnij się, że **konfiguracji rozwiązania** pole jest ustawione na **debugowania**. Naciśnij klawisz **F5**, kliknij zielony **Start** strzałkę lub wybierz **debugowania** > **Rozpocznij debugowanie**.

Jeśli debugowanie nie trafia punktów przerwania, upewnij się, że dane wyjściowe biblioteki DLL (domyślnie  *\<Projekt > \Debug* folder) to lokalizacja, która wywołuje aplikacji wywołującej.
  
## <a name="see-also"></a>Zobacz także  
 [Debugowanie projektów DLL](../debugger/debugging-dll-projects.md)   
 [Ustawienia projektu dla konfiguracji debugowania w języku C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Ustawienia projektu dla konfiguracji debugowania w języku Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Ustawienia projektu dla konfiguracji debugowania w języku C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)