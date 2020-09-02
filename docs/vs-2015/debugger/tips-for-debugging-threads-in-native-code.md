---
title: Wskazówki dotyczące debugowania wątków w kodzie natywnym | Microsoft Docs
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
ms.openlocfilehash: 7c299d3585d9089f8525c2ec7f470601797cc3a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684871"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Wskazówki dotyczące debugowanie wątków w kodzie natywnym
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Poniżej przedstawiono kilka porad, których można użyć podczas debugowania wątków w kodzie natywnym:  
  
- Zawartość bloku informacji o wątkach można wyświetlić, wpisując `@TIB` w oknie dialogowym **Watch** lub **QuickWatch** .  
  
- Kod ostatniego błędu dla bieżącego wątku można wyświetlić, wprowadzając `@Err` w oknie dialogowym **czujka** lub **QuickWatch** .  
  
- Funkcje bibliotek uruchomieniowych języka C (CRT) mogą być przydatne do debugowania aplikacji wielowątkowych. Aby uzyskać więcej informacji, zobacz [_malloc_dbg](https://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb).  
  
## <a name="see-also"></a>Zobacz też  
 [Debuguj aplikacje wielowątkowe](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
