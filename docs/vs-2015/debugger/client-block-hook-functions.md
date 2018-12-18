---
title: Funkcje punktu zaczepienia bloku klienta | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 2b16dc9eaff974e98e411d4f49d8aed6f9f656e8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773941"
---
# <a name="client-block-hook-functions"></a>Funkcje punktu zaczepienia bloku klienta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli chcesz sprawdzić lub zgłosić zawartość danych przechowywanych w `_CLIENT_BLOCK` blokuje, można napisać funkcję specjalnie do tego celu. Napisana funkcja musi mieć podobny do poniższego, prototyp, zgodnie z definicją w CRTDBG. GODZ.:  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 Innymi słowy, funkcja podłączania powinna obsługiwać **void** wskaźnika na początku bloku alokacji, wraz z **size_t** wpisz wartość wskazującą, rozmiar alokacji i zwracać `void`. Innych niż jego zawartość, zależą od Ciebie.  
  
 Po zainstalowaniu, używając funkcji punktów zaczepienia [_CrtSetDumpClient](http://msdn.microsoft.com/library/f3dd06d0-c331-4a12-b68d-25378d112033), będzie ona wywoływana zawsze `_CLIENT_BLOCK` jest zrzucany bloku. Następnie można użyć [_CrtReportBlockType](http://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b) można pobrać informacji na temat typu lub podtypu zrzut bloków.  
  
 Wskaźnik do funkcji, możesz przekazać do `_CrtSetDumpClient` typu **_crt_dump_client —**, zgodnie z definicją w CRTDBG. GODZ.:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie pisanie funkcji punktów zaczepienia](../debugger/debug-hook-function-writing.md)   
 [Przykładowe crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](http://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b)



