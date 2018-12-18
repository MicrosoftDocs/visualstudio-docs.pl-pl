---
title: 'Porady: debugowanie w trybie mieszanym | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/05/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1439dce6930b71e29141031e93175e0a6aaa519c
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389477"
---
# <a name="how-to-debug-in-mixed-mode-c-c-visual-basic"></a>Porady: debugowanie w trybie mieszanym (C#, C++, Visual Basic)

W poniższych procedurach opisano sposób włączania debugowania dla kodu zarządzanego i natywnego razem, znany także jako trybu mieszanego debugowania. Istnieją dwa scenariusze debugowania w trybie mieszanym:

- Aplikacji, która wywołuje bibliotekę DLL są zapisywane w kodzie natywnym, a Biblioteka DLL jest zarządzana.

- Aplikacja, która wywołuje bibliotekę DLL są zapisywane w kodzie zarządzanym i Wspomniany plik znajduje się w kodzie natywnym. Aby uzyskać samouczek, który przeprowadzi Cię przez ten scenariusz bardziej szczegółowo, zobacz [debugowanie kodu zarządzanego i natywnego](../debugger/how-to-debug-managed-and-native-code.md).

Możesz włączyć debugery zarządzane i natywne w projekcie aplikacji wywołującej **właściwość** stron. Ustawienia różnią się natywnych i zarządzanych aplikacji.

Jeśli nie masz dostępu do projektu wywołującej aplikacji można debugować bibliotekę DLL z projektu DLL. Tryb mieszany, aby debugować tylko projekt DLL nie jest konieczne. Aby uzyskać więcej informacji, zobacz [porady: debugowanie z projektu DLL](../debugger/how-to-debug-from-a-dll-project.md).

> [!NOTE]
> Dostępne polecenia i okien dialogowych mogą różnić się od przedstawionych w tym artykule, w zależności od wersji lub ustawienia programu Visual Studio. Aby zmienić swoje ustawienia, wybierz opcję **narzędzia** > **Import i eksport ustawień**. Aby uzyskać więcej informacji, zobacz [zresetować ustawienia](../ide/environment-settings.md#reset-settings).

## <a name="enable-mixed-mode-debugging-for-a-native-calling-app"></a>Włącz debugowanie w trybie mieszanym dla natywnych aplikacji wywołującej

1. Wybierz projekt C++ w **Eksploratora rozwiązań** i kliknij przycisk **właściwości** ikonę, naciśnij klawisz **Alt**+**Enter**, lub Kliknij prawym przyciskiem myszy i wybierz polecenie **właściwości**.

1. W  **\<Projekt > strony właściwości** okna dialogowego rozwiń **właściwości konfiguracji**, a następnie wybierz pozycję **debugowanie**.

1. Ustaw **typ debugera** do **mieszane** lub **automatycznie**.

1. Wybierz **OK**.

   ![Włącz debugowanie w trybie mieszanym](../debugger/media/dbg-mixed-mode-from-native.png "włączyć debugowanie w trybie mieszanym")

## <a name="enable-mixed-mode-debugging-for-a-managed-calling-app"></a>Włącz debugowanie w trybie mieszanym dla zarządzanych aplikacji wywołującej

1. Wybierz projekt C# lub Visual Basic w **Eksploratora rozwiązań** i wybierz **właściwości** ikonę, naciśnij klawisz **Alt**+**Enter**, lub kliknij prawym przyciskiem myszy i wybierz pozycję **właściwości**.

1. Wybierz **debugowania** , a następnie wybierz pozycję **Włącz debugowanie kodu natywnego**.

1. Zamknij stronę właściwości, aby zapisać zmiany.

   ![Włącz debugowanie kodu natywnego](../debugger/media/dbg-mixed-mode-from-csharp.png "Włącz debugowanie kodu natywnego")

> [!NOTE]
> W większości wersji programu Visual Studio 2017, musisz użyć *launchSettings.json* pliku zamiast właściwości projektu, aby włączyć debugowanie w trybie mieszanym dla kodu natywnego w aplikacji platformy .NET Core. Aby uzyskać więcej informacji, zobacz [debugowanie kodu zarządzanego i natywnego](../debugger/how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Zobacz także

- [Instrukcje: debugowanie z projektu DLL](../debugger/how-to-debug-from-a-dll-project.md)