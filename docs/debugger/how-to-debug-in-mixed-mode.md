---
title: Debugowanie w trybie mieszanym | Microsoft Docs
ms.date: 11/05/2018
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53a40c4dc615b5e1b6a3caef3a99be5ab0b56327
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350111"
---
# <a name="how-to-debug-in-mixed-mode-c-c-visual-basic"></a>Instrukcje: debugowanie w trybie mieszanym (C#, C++, Visual Basic)

W poniższych procedurach opisano sposób włączania debugowania dla kodu zarządzanego i natywnego, znanego również jako debugowanie w trybie mieszanym. Istnieją dwa scenariusze debugowania w trybie mieszanym:

- Aplikacja wywołująca bibliotekę DLL jest zapisywana w kodzie natywnym, a Biblioteka DLL jest zarządzana.

- Aplikacja wywołująca bibliotekę DLL jest zapisywana w kodzie zarządzanym, a Biblioteka DLL znajduje się w kodzie natywnym. Aby zapoznać się z samouczkiem, który przeprowadzi Cię przez ten scenariusz bardziej szczegółowo, zobacz [Debugowanie kodu zarządzanego i natywnego](../debugger/how-to-debug-managed-and-native-code.md).

Można włączyć zarówno debugery zarządzane, jak i natywne na stronach **Właściwości** projektu aplikacji wywołującej. Ustawienia różnią się między aplikacjami natywnymi i zarządzanymi.

Jeśli nie masz dostępu do projektu aplikacji wywołującej, możesz debugować bibliotekę DLL z projektu DLL. Nie jest potrzebny tryb mieszany do debugowania tylko projektu DLL. Aby uzyskać więcej informacji, zobacz [jak: debugowanie z projektu DLL](../debugger/how-to-debug-from-a-dll-project.md).

> [!NOTE]
> Widoczne okna dialogowe i polecenia mogą różnić się od tych w tym artykule, w zależności od ustawień lub wersji programu Visual Studio. Aby zmienić ustawienia, wybierz kolejno opcje **Narzędzia**  >  **Importuj i Eksportuj ustawienia**. Aby uzyskać więcej informacji, zobacz [Resetowanie ustawień](../ide/environment-settings.md#reset-settings).

## <a name="enable-mixed-mode-debugging-for-a-native-calling-app"></a>Włącz debugowanie w trybie mieszanym dla natywnej aplikacji wywołującej

1. Wybierz projekt C++ w **Eksplorator rozwiązań** i kliknij ikonę **Właściwości** , naciśnij klawisz **Alt** + **Enter**lub kliknij prawym przyciskiem myszy i wybierz polecenie **Właściwości**.

1. W oknie dialogowym ** \<Project> strony właściwości** rozwiń węzeł **Właściwości konfiguracji**, a następnie wybierz pozycję **debugowanie**.

1. Ustaw **Typ debugera** na **mieszany** lub **Auto**Auto.

1. Wybierz przycisk **OK**.

   ![Włącz debugowanie w trybie mieszanym](../debugger/media/dbg-mixed-mode-from-native.png "Włącz debugowanie w trybie mieszanym")

## <a name="enable-mixed-mode-debugging-for-a-managed-calling-app"></a>Włącz debugowanie w trybie mieszanym dla zarządzanej aplikacji wywołującej

1. Wybierz projekt C# lub Visual Basic w **Eksplorator rozwiązań** i wybierz ikonę **Właściwości** , naciśnij klawisz **Alt** + **Enter**lub kliknij prawym przyciskiem myszy i wybierz polecenie **Właściwości**.

1. Wybierz kartę **debugowanie** , a następnie wybierz pozycję **Włącz debugowanie kodu natywnego**.

1. Zamknij stronę właściwości, aby zapisać zmiany.

   ![Włącz debugowanie kodu natywnego](../debugger/media/dbg-mixed-mode-from-csharp.png "Włącz debugowanie kodu natywnego")

> [!NOTE]
> W większości wersji programu Visual Studio, począwszy od programu Visual Studio 2017, należy użyć *launchSettings.jsw* pliku zamiast właściwości projektu, aby włączyć debugowanie w trybie mieszanym dla kodu natywnego w aplikacji .NET Core. Aby uzyskać szczegółowe informacje, zobacz [Debugowanie kodu zarządzanego i natywnego](../debugger/how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Zobacz też

- [Instrukcje: debugowanie z projektu DLL](../debugger/how-to-debug-from-a-dll-project.md)