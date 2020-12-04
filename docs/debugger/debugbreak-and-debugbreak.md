---
title: DebugBreak i __debugbreak | Microsoft Docs
description: Dowiedz się, jak używać funkcji DebugBreak i wewnętrznego __debugbreak, aby spowodować przerwanie działania programu, tak jakby był ustawiony punkt przerwania.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 376dd75062dc5a78582a23a12e9e025db60b9f3a
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2020
ms.locfileid: "96559774"
---
# <a name="debugbreak-and-__debugbreak"></a>DebugBreak i __debugbreak
Można wywołać [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) funkcję Win32 lub [__debugbreak](/cpp/intrinsics/debugbreak) wewnętrznie w dowolnym momencie w kodzie. `DebugBreak` i `__debugbreak` mają ten sam efekt, co ustawienie punktu przerwania w tej lokalizacji.

 Ponieważ `DebugBreak` jest wywołaniem funkcji systemowej, należy zainstalować symbole debugowania systemu, aby upewnić się, że po przerwaniu są wyświetlane poprawne informacje stosu wywołań. W przeciwnym razie informacje stosu wywołań wyświetlane przez debuger mogą być wyłączone przez jedną klatkę. Jeśli używasz `__debugbreak` , symbole nie są wymagane.

## <a name="see-also"></a>Zobacz także
- [Funkcje wewnętrzne kompilatora](/cpp/intrinsics/compiler-intrinsics)
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
- [Określanie plików symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
