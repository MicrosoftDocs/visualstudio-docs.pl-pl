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
ms.openlocfilehash: 1d4f23b885b2e72e53d288946df18e038d9d956d
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476778"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Jak można sprawdzić, czy wskaźniki uszkadzają adresy pamięci?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opis problemu  
 Myślę, że jeden ze wskaźników może uszkadzać pamięć pod adresem 0x00408000. Jak można dowiedzieć się, co się tam dzieje?  
  
## <a name="solution"></a>Rozwiązanie  
  
#### <a name="check-for-heap-corruption"></a>Sprawdź uszkodzenie sterty  
  
- Większość uszkodzeń pamięci jest rzeczywiście z powodu uszkodzenia sterty. Spróbuj użyć Global Flags Utility (gflags.exe) lub pageheap.exe. Zobacz [GFlags i Pageheap](/windows-hardware/drivers/debugger/gflags-and-pageheap) oraz [jak używać narzędzia Pageheap, aby wykrywać błędy pamięci w projekcie Microsoft Visual C++ ](https://support.microsoft.com/help/264471/how-to-use-the-pageheap-utility-to-detect-memory-errors-in-a-microsoft).
  
#### <a name="to-find-where-the-memory-address-is-modified"></a>Aby dowiedzieć się, gdzie jest zmodyfikowany adres pamięci  
  
1. Ustaw punkt przerwania pod adresem 0x00408000. Zobacz [Ustawianie punktu przerwania zmiany danych ( C++ tylko kod natywny)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus_only).  
  
2. Po trafieniu punktu przerwania Użyj okna **pamięci** , aby wyświetlić zawartość pamięci, zaczynając od 0x00408000. Aby uzyskać więcej informacji, zobacz [pamięć systemu Windows](../debugger/memory-windows.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie często zadawanych pytań dotyczących kodu natywnego](../debugger/debugging-native-code-faqs.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
