---
title: Funkcje punktu zaczepienia bloku klienta | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b7b0ef177922f09239c8925ced1ca013e966c0e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72745720"
---
# <a name="client-block-hook-functions"></a>Funkcje punktu zaczepienia bloku klienta
Jeśli chcesz sprawdzić poprawność lub zgłosić zawartość danych przechowywanych w `_CLIENT_BLOCK` blokach, można napisać funkcję specjalnie do tego celu. Funkcja, którą pisze, musi mieć prototyp podobny do poniższego, zgodnie z definicją w CRTDBG. C

```cpp
void YourClientDump(void *, size_t)
```

 Innymi słowy, funkcja Hook powinna akceptować wskaźnik **void** na początku bloku alokacji wraz z wartością typu **size_t** wskazującą rozmiar alokacji i zwrócić `void` . Jego zawartość jest inna niż ta.

 Po zainstalowaniu funkcji Hook przy użyciu [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient), będzie ona wywoływana za każdym razem, gdy `_CLIENT_BLOCK` blok jest zrzucany. Następnie można użyć [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) , aby uzyskać informacje na temat typu lub podtypu bloków zrzutów.

 Wskaźnik do funkcji przekazanej przez użytkownika `_CrtSetDumpClient` jest typu **_CRT_DUMP_CLIENT**, zgodnie z definicją w CRTDBG. C

```cpp
typedef void (__cdecl *_CRT_DUMP_CLIENT)
   (void *, size_t);
```

## <a name="see-also"></a>Zobacz też

- [Pisanie debugowanie funkcji punktów zaczepienia](../debugger/debug-hook-function-writing.md)
- [Przykład crt_dbg2](https://msdn.microsoft.com/library/21e1346a-6a17-4f57-b275-c76813089167)
- [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)