---
title: DebugBreak i __debugbreak | Microsoft Docs
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
ms.openlocfilehash: ea2a40943233e7dfffd3340f2e27da1d43a76a0a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691175"
---
# <a name="debugbreak-and-__debugbreak"></a>DebugBreak i __debugbreak
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można wywołać DebugBreak funkcję Win32 lub [__debugbreak](https://msdn.microsoft.com/library/1d1e1c0c-891a-4613-ae4b-d790094ba830) wewnętrznie w dowolnym momencie w kodzie. `DebugBreak` i `__debugbreak` mają ten sam efekt, co ustawienie punktu przerwania w tej lokalizacji.  
  
 Ponieważ `DebugBreak` jest wywołaniem funkcji systemowej, należy zainstalować symbole debugowania systemu, aby upewnić się, że po przerwaniu są wyświetlane poprawne informacje stosu wywołań. W przeciwnym razie informacje stosu wywołań wyświetlane przez debuger mogą być wyłączone przez jedną klatkę. Jeśli używasz `__debugbreak` , symbole nie są wymagane.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](https://msdn.microsoft.com/library/48bb9929-7d78-4fd8-a092-ae3c9f971858)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)   
 [Określanie plików symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
