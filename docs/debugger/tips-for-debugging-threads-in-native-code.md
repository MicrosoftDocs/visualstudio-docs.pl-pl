---
title: Wskazówki dotyczące debugowania wątków w kodzie natywnym | Microsoft Docs
description: Zapoznaj się z listą porad dotyczących debugowania wątków w kodzie natywnym w przypadku debugowania aplikacji wielowątkowych w programie Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 9249e1527a7dd2ae720ab575b1d443c10b85376e
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150057"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Wskazówki dotyczące debugowanie wątków w kodzie natywnym
Poniżej przedstawiono kilka porad, których można użyć podczas debugowania wątków w kodzie natywnym:

- Zawartość bloku informacji o wątkach można wyświetlić, wpisując `@TIB` w oknie dialogowym **Watch** lub **QuickWatch** .

- Kod ostatniego błędu dla bieżącego wątku można wyświetlić, wprowadzając `@Err` w oknie dialogowym **czujka** lub **QuickWatch** .

- Funkcje bibliotek języka C Run-Time (CRT) mogą być przydatne do debugowania aplikacji wielowątkowych. Aby uzyskać więcej informacji, zobacz [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).

## <a name="see-also"></a>Zobacz także
- [Debuguj aplikacje wielowątkowe](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)