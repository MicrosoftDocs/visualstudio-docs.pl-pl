---
title: Dowiedz się, czy moje wskaźniki uszkadzają adres pamięci | Microsoft Docs
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
ms.openlocfilehash: 516b04bb625ad2546c4c8f3d3e7d7d4ba9419094
ms.sourcegitcommit: 49ebf69986713e440fd138fb949f1c0f47223f23
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74705839"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Jak można sprawdzić, czy wskaźniki uszkadzają adresy pamięci?
## <a name="problem-description"></a>Opis problemu
 Myślę, że jeden ze wskaźników może spowodować uszkodzenie pamięci pod adresem 0x00408000. Jak mogę się dowiedzieć, co się dzieje?

## <a name="solution"></a>Rozwiązanie

#### <a name="check-for-heap-corruption"></a>Sprawdź uszkodzenie sterty

- Większość uszkodzeń pamięci jest w rzeczywistości spowodowana uszkodzeniem sterty. Spróbuj użyć narzędzia globalnych flags (gflags. exe) lub Pageheap. exe. Zobacz [https://docs.microsoft.com/windows-hardware/drivers/debugger/gflags-and-pageheap](/windows-hardware/drivers/debugger/gflags-and-pageheap).

#### <a name="to-find-where-the-memory-address-is-modified"></a>Aby znaleźć miejsce modyfikacji adresu pamięci

1. Ustaw punkt przerwania danych w 0x00408000. Zobacz [Ustawianie punktu przerwania zmiany danych ( C++ tylko kod natywny)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).

2. Po trafieniu punktu przerwania Użyj okna **pamięci** , aby wyświetlić zawartość pamięci, zaczynając od 0x00408000. Aby uzyskać więcej informacji, zobacz [pamięć systemu Windows](../debugger/memory-windows.md).

## <a name="see-also"></a>Zobacz także
- [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
