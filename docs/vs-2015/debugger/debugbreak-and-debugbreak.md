---
title: DebugBreak i __debugbreak | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- DebugBreak
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c7d26d78cf5e1995c25560e70e46ee4f6fde3a25
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54798588"
---
# <a name="debugbreak-and-debugbreak"></a>DebugBreak i __debugbreak
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można wywołać funkcję DebugBreak Win32 lub [__debugbreak](http://msdn.microsoft.com/library/1d1e1c0c-891a-4613-ae4b-d790094ba830) wewnętrzne w dowolnym momencie w kodzie. `DebugBreak` i `__debugbreak` mają ten sam efekt jak ustawienie punktu przerwania w tej lokalizacji.  
  
 Ponieważ `DebugBreak` jest wywołaniem funkcji systemowej, debugowania systemu symbole musi być zainstalowany, aby upewnić się, informacje stosu wywołań poprawne jest wyświetlany po ostatniej chwili. W przeciwnym razie informacje stosu wywołań, które są wyświetlane przez debuger może być wyłączone przez jedną klatkę. Jeśli używasz `__debugbreak`, symbole nie są wymagane.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](http://msdn.microsoft.com/library/48bb9929-7d78-4fd8-a092-ae3c9f971858)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)   
 [Określanie plików symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
