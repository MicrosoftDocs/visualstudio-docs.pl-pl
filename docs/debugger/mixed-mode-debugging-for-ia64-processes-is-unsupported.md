---
title: Debugowanie w trybie mieszanym dla procesów IA64 nie jest obsługiwane. | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f0130ba9e893d5a4036df9ee1bc2ab22c8e18008
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929878"
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Debugowanie w trybie mieszanym dla procesów IA64 nie jest obsługiwane.
Program Visual Studio nie obsługuje debugowanie kodu zarządzanego i natywnego w procesów IA64 w trybie mieszanym. Oznacza to, że nie możesz wejść z kodu zarządzanego do kodu macierzystego lub kodu natywnego do zarządzanego kodu podczas debugowania.

### <a name="workarounds"></a>Rozwiązania

- Debugowanie kodu zarządzanego i natywnego w oddzielnych sesji debugowania.

     —lub—

     Debugowanie kodu mieszanego jako proces 32-bitowych, zgodnie z opisem w poniższych procedurach.

### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Aby zmienić platformy 32-bitowe (Visual Basic lub C#)

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem, a następnie kliknij przycisk **właściwości** w menu skrótów.

2. Na stronach właściwości kliknij przycisk **skompilować** lub **debugowania** kartę.

3. Kliknij przycisk **platformy** i wybierać x86 listę platform.

     Domyślnie domyślne Kompilatory języka Visual Basic i C# generuje kod wymagany do uruchomienia na dowolny procesor CPU. Na komputerze 64-bitowych te pliki binarne Uruchom jako procesów 64-bitowych. Aby uruchomić proces 32-bitowy, należy wybrać **Win32**, a nie **AnyCPU**.

### <a name="to-change-the-platform-to-32-bit-cc"></a>Aby zmienić platformy 32-bitowych (C/C++)

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem, a następnie kliknij przycisk **właściwości** w menu skrótów.

2. Na stronach właściwości kliknij przycisk **platformy** i wybierz listę platform, systemu Win32

## <a name="see-also"></a>Zobacz też
- [Debugowanie aplikacji 64-bitowych](../debugger/debug-64-bit-applications.md)