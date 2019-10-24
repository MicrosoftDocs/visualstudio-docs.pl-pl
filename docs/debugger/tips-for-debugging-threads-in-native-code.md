---
title: Wskazówki dotyczące debugowania wątków w kodzie natywnym | Microsoft Docs
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
ms.openlocfilehash: 7dde94e28f378f0630a78f32ae5e58533729ce0f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728993"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Wskazówki dotyczące debugowanie wątków w kodzie natywnym
Poniżej przedstawiono kilka porad, których można użyć podczas debugowania wątków w kodzie natywnym:

- Zawartość bloku informacji o wątkach można wyświetlić, wpisując `@TIB` w oknie **czujki** lub w oknie dialogowym **QuickWatch** .

- Kod ostatniego błędu dla bieżącego wątku można wyświetlić, wprowadzając `@Err` w oknie **czujki** lub oknie dialogowym **QuickWatch** .

- Funkcje bibliotek uruchomieniowych języka C (CRT) mogą być przydatne do debugowania aplikacji wielowątkowych. Aby uzyskać więcej informacji, zobacz [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).

## <a name="see-also"></a>Zobacz także
- [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)