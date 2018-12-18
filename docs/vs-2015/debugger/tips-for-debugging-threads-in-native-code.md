---
title: Porady dotyczące debugowania wątków w kodzie natywnym | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1852e2d0b3e773e5be0f3f60ad191056a4af0889
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775007"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Wskazówki dotyczące debugowanie wątków w kodzie natywnym
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Poniżej przedstawiono kilka wskazówek, których można użyć podczas debugowania wątków w kodzie natywnym:  
  
-   Zawartość bloku informacji o wątku można wyświetlić, wpisując `@TIB` w **Obejrzyj** okna lub **QuickWatch** okno dialogowe.  
  
-   Możesz wyświetlić kod ostatniego błędu dla bieżącego wątku, wprowadzając `@Err` w **Obejrzyj** okna lub **QuickWatch** okno dialogowe.  
  
-   Funkcje biblioteki wykonawczej C (CRT) mogą być przydatne podczas debugowania aplikacji wielowątkowych. Aby uzyskać więcej informacji, zobacz [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)



