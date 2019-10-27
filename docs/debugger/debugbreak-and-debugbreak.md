---
title: DebugBreak i __debugbreak | Microsoft Docs
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
ms.openlocfilehash: ce99cd360d75472df6326cfaf6a3f4ddb198b6d2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738355"
---
# <a name="debugbreak-and-__debugbreak"></a>DebugBreak i __debugbreak
Można wywołać funkcję Win32 DebugBreak lub wewnętrzną [__debugbreak](/cpp/intrinsics/debugbreak) w dowolnym momencie w kodzie. `DebugBreak` i `__debugbreak` mają ten sam efekt, co ustawienie punktu przerwania w tej lokalizacji.

 Ponieważ `DebugBreak` jest wywołaniem funkcji systemowej, należy zainstalować symbole debugowania systemu, aby upewnić się, że po przerwaniu są wyświetlane poprawne informacje stosu wywołań. W przeciwnym razie informacje stosu wywołań wyświetlane przez debuger mogą być wyłączone przez jedną klatkę. Jeśli używasz `__debugbreak`, symbole nie są wymagane.

## <a name="see-also"></a>Zobacz także
- [Funkcje wewnętrzne kompilatora](/cpp/intrinsics/compiler-intrinsics)
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
- [Określanie plików symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)