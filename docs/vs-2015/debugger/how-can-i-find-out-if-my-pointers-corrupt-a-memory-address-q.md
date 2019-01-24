---
title: Jak można sprawdzić, czy wskaźniki uszkadzają adresy pamięci? | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8da16e806b8c4bb9bb29251184a5a45c566e9f25
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54805411"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Jak można sprawdzić, czy wskaźniki uszkadzają adresy pamięci?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opis problemu  
 Myślę, że jeden ze wskaźników może uszkadzać pamięć pod adresem 0x00408000. Jak można dowiedzieć się, co się tam dzieje?  
  
## <a name="solution"></a>Rozwiązanie  
  
#### <a name="check-for-heap-corruption"></a>Sprawdź uszkodzenie sterty  
  
-   Większość uszkodzeń pamięci jest rzeczywiście z powodu uszkodzenia sterty. Spróbuj użyć Global Flags Utility (gflags.exe) lub pageheap.exe. Zobacz [ http://support.microsoft.com/default.aspx?scid=kb; en-us; 286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470).  
  
#### <a name="to-find-where-the-memory-address-is-modified"></a>Aby dowiedzieć się, gdzie jest zmodyfikowany adres pamięci  
  
1.  Ustaw punkt przerwania pod adresem 0x00408000. Zobacz [Ustaw punkt przerwania zmiany danych (tylko w natywnym kodzie C++)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus_only).  
  
2.  Po osiągnięciu punktu przerwania użyj **pamięci** okna, aby wyświetlić pamięci zawartości, począwszy od 0x00408000. Aby uzyskać więcej informacji, zobacz [Windows pamięci](../debugger/memory-windows.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
