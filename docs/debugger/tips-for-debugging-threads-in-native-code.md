---
title: Porady dotyczące debugowania wątków w kodzie natywnym | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 8ee1f1f2f2029325e3d3b87ca44d05d800a62c07
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901878"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Wskazówki dotyczące debugowanie wątków w kodzie natywnym
Poniżej przedstawiono kilka wskazówek, których można użyć podczas debugowania wątków w kodzie natywnym:

- Zawartość bloku informacji o wątku można wyświetlić, wpisując `@TIB` w **Obejrzyj** okna lub **QuickWatch** okno dialogowe.

- Możesz wyświetlić kod ostatniego błędu dla bieżącego wątku, wprowadzając `@Err` w **Obejrzyj** okna lub **QuickWatch** okno dialogowe.

- Funkcje biblioteki wykonawczej C (CRT) mogą być przydatne podczas debugowania aplikacji wielowątkowych. Aby uzyskać więcej informacji, zobacz [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).

## <a name="see-also"></a>Zobacz też
- [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)