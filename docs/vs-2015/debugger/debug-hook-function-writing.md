---
title: Pisanie funkcji punktów zaczepienia debugowanie | Dokumentacja firmy Microsoft
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
- vc.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], CRT debug support
- debug hook functions
- hooks, debug
- hooks
- debugging [CRT], debug hook functions
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47cd3d42639785290f26d7acbbad15cd948b4f51
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735527"
---
# <a name="debug-hook-function-writing"></a>Pisanie debugowanie funkcji punktów zaczepienia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji opisano wiele niestandardowych debugowania punktów zaczepienia funkcje, których można napisać, które umożliwiają wstawianie kodu niektóre punkty wstępnie zdefiniowane wewnątrz debugera normalne przetwarzanie.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Funkcje punktu zaczepienia bloku klienta](../debugger/client-block-hook-functions.md)  
 Udostępniane są wskazówki i prototyp dla funkcji, które weryfikacji lub zgłosić zawartość danych przechowywanych w blokach _CLIENT_BLOCK zapisu.  
  
 [Funkcje punktu zaczepienia alokacji](../debugger/allocation-hook-functions.md)  
 Definiuje funkcję punktu zaczepienia alokacji i analizuje różnych zastosowań, punkty ograniczenia, zawiera prototyp.  
  
 [Punkty zaczepienia alokacji i alokacji pamięci CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)  
 Opisano ograniczenia dotyczące funkcji punktów zaczepienia alokacji jawnie zignorowanie `_CRT_BLOCK` blokuje, jeśli dokonają wszelkie wywołania funkcji biblioteki wykonawczej języka C, przydzielania pamięci wewnętrznej. Ten temat zawiera także listę konsekwencje Jeśli Twojego punktu zaczepienia alokacji nie ignoruje `_CRT_BLOCK` bloków (wraz z przykładami) i jak zmienić Alokacja domyślna funkcję, podłączania **CrtDefaultAllocHook**.  
  
 [Raportowanie funkcji punktów zaczepienia](../debugger/report-hook-functions.md)  
 W tym artykule omówiono `_CrtSetReportHook`, którego można użyć do filtrowania raportów skoncentrować się na określonych typów alokacji. Ten temat zawiera także prototypu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Techniki debugowania CRT](../debugger/crt-debugging-techniques.md)  
 Łącza do debugowania dla biblioteki wykonawczej C, w tym o korzystaniu z biblioteki debugowania CRT, makra raportowania, różnice między `malloc` i `_malloc_dbg`, pisanie debugowanie funkcji punktów zaczepienia i sterty debugowania CRT.



