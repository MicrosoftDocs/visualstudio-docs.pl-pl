---
title: Dowiedz się, czy wskaźniki uszkodzony adres pamięci | Microsoft Docs
description: Aby ustalić, czy wskaźnik uszkodzonej pamięci, można poszukać uszkodzenia sterty i ustawić punkt przerwania danych, aby dowiedzieć się, jak wartość jest modyfikowana.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 836cc0363da0e20c45d83e1b2c13081e480fa919
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386972"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Jak można sprawdzić, czy wskaźniki uszkadzają adresy pamięci?
## <a name="problem-description"></a>Opis problemu
 Myślę, że jeden z moich wskaźników może uszkodzić pamięć pod adresem 0x00408000. Jak sprawdzić, co się tam dzieje?

## <a name="solution"></a>Rozwiązanie

#### <a name="check-for-heap-corruption"></a>Sprawdzanie uszkodzeń sterty

- Większość uszkodzeń pamięci jest w rzeczywistości spowodowana uszkodzeniem sterty. Spróbuj użyć narzędzia Global Flags (gflags.exe) lub pageheap.exe. Zobacz [/windows-hardware/drivers/debugger/gflags-and-pageheap](/windows-hardware/drivers/debugger/gflags-and-pageheap).

#### <a name="to-find-where-the-memory-address-is-modified"></a>Aby dowiedzieć się, gdzie adres pamięci jest modyfikowany

1. Ustaw punkt przerwania danych w 0x00408000. Zobacz [Ustawianie punktu przerwania zmiany danych (tylko natywny język C++).](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus)

2. Po trafieniu punktu przerwania użyj okna **Pamięć,** aby wyświetlić zawartość pamięci, zaczynając od 0x00408000. Aby uzyskać więcej informacji, zobacz [Okna pamięci](../debugger/memory-windows.md).

## <a name="see-also"></a>Zobacz też
- [Debugowanie kodu natywnego : często zadawane pytania](../debugger/debugging-native-code-faqs.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
