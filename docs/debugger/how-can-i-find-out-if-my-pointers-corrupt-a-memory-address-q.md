---
title: Sprawdzić, czy wskaźniki uszkodzony adres pamięci | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5e61c1433ee05954a85537cd5e30bb9683642f3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894941"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Jak można sprawdzić, czy wskaźniki uszkadzają adresy pamięci?
## <a name="problem-description"></a>Opis problemu
 Myślę, że jeden ze wskaźników może uszkadzać pamięć pod adresem 0x00408000. Jak można dowiedzieć się, co się tam dzieje?

## <a name="solution"></a>Rozwiązanie

#### <a name="check-for-heap-corruption"></a>Sprawdź uszkodzenie sterty

- Większość uszkodzeń pamięci jest rzeczywiście z powodu uszkodzenia sterty. Spróbuj użyć Global Flags Utility (gflags.exe) lub pageheap.exe. Zobacz [ http://support.microsoft.com/default.aspx?scid=kb; en-us; 286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470).

#### <a name="to-find-where-the-memory-address-is-modified"></a>Aby dowiedzieć się, gdzie jest zmodyfikowany adres pamięci

1. Ustaw punkt przerwania pod adresem 0x00408000. Zobacz [Ustaw punkt przerwania zmiany danych (tylko w natywnym kodzie C++)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).

2. Po osiągnięciu punktu przerwania użyj **pamięci** okna, aby wyświetlić pamięci zawartości, począwszy od 0x00408000. Aby uzyskać więcej informacji, zobacz [Windows pamięci](../debugger/memory-windows.md).

## <a name="see-also"></a>Zobacz też
- [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)