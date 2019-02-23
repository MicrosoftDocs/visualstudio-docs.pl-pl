---
title: DebugBreak i __debugbreak | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DebugBreak
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6c4b9d780caf7589eecdc709cbede577dd7a6fd
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686161"
---
# <a name="debugbreak-and-debugbreak"></a>DebugBreak i __debugbreak
Można wywołać funkcję DebugBreak Win32 lub [__debugbreak](/cpp/intrinsics/debugbreak) wewnętrzne w dowolnym momencie w kodzie. `DebugBreak` i `__debugbreak` mają ten sam efekt jak ustawienie punktu przerwania w tej lokalizacji.

 Ponieważ `DebugBreak` jest wywołaniem funkcji systemowej, debugowania systemu symbole musi być zainstalowany, aby upewnić się, informacje stosu wywołań poprawne jest wyświetlany po ostatniej chwili. W przeciwnym razie informacje stosu wywołań, które są wyświetlane przez debuger może być wyłączone przez jedną klatkę. Jeśli używasz `__debugbreak`, symbole nie są wymagane.

## <a name="see-also"></a>Zobacz też
- [Funkcje wewnętrzne kompilatora](/cpp/intrinsics/compiler-intrinsics)
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
- [Określanie plików symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)