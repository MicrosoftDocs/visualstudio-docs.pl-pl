---
title: Funkcje punktu zaczepienia bloku klienta | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c5b1c754255ba0bc659c9b6968ad8ba0dea629ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702323"
---
# <a name="client-block-hook-functions"></a>Funkcje punktu zaczepienia bloku klienta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli chcesz sprawdzić poprawność lub zgłosić zawartość danych przechowywanych w `_CLIENT_BLOCK` blokach, można napisać funkcję specjalnie do tego celu. Funkcja, którą pisze, musi mieć prototyp podobny do poniższego, zgodnie z definicją w CRTDBG. C  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 Innymi słowy, funkcja Hook powinna akceptować wskaźnik **void** na początku bloku alokacji wraz z wartością typu **size_t** wskazującą rozmiar alokacji i zwrócić `void` . Jego zawartość jest inna niż ta.  
  
 Po zainstalowaniu funkcji Hook przy użyciu [_CrtSetDumpClient](https://msdn.microsoft.com/library/f3dd06d0-c331-4a12-b68d-25378d112033), będzie ona wywoływana za każdym razem, gdy `_CLIENT_BLOCK` blok jest zrzucany. Następnie można użyć [_CrtReportBlockType](https://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b) , aby uzyskać informacje na temat typu lub podtypu bloków zrzutów.  
  
 Wskaźnik do funkcji przekazanej przez użytkownika `_CrtSetDumpClient` jest typu **_CRT_DUMP_CLIENT**, zgodnie z definicją w CRTDBG. C  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zapisywanie funkcji punktu zaczepienia debugowania](../debugger/debug-hook-function-writing.md)   
 [Przykład crt_dbg2](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](https://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b)
