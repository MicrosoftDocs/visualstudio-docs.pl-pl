---
title: Porady dotyczące debugowania wątków w kodzie natywnym | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 2c4bed2506fef0c4f066e58e158b062c2a6b39aa
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60074180"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Wskazówki dotyczące debugowanie wątków w kodzie natywnym
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Poniżej przedstawiono kilka wskazówek, których można użyć podczas debugowania wątków w kodzie natywnym:  
  
- Zawartość bloku informacji o wątku można wyświetlić, wpisując `@TIB` w **Obejrzyj** okna lub **QuickWatch** okno dialogowe.  
  
- Możesz wyświetlić kod ostatniego błędu dla bieżącego wątku, wprowadzając `@Err` w **Obejrzyj** okna lub **QuickWatch** okno dialogowe.  
  
- Funkcje biblioteki wykonawczej C (CRT) mogą być przydatne podczas debugowania aplikacji wielowątkowych. Aby uzyskać więcej informacji, zobacz [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
