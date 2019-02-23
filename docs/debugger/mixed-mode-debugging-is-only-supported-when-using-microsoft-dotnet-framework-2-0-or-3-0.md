---
title: Debugowanie w trybie mieszanym jest obsługiwane tylko podczas korzystania z programu Microsoft .NET Framework 2.0 lub 3.0 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_to_old
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: f607af6f-57fe-472a-a32e-b6202067aa96
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9edda3762d17dcdf7ec23505646e4b166b0ea91a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56710971"
---
# <a name="mixed-mode-debugging-is-only-supported-when-using-microsoft-net-framework-20-or-30"></a>Debugowanie w trybie mieszanym jest obsługiwane tylko w przypadku korzystania z programu Microsoft .NET Framework 2.0 or 3.0
Wersje programu Microsoft .NET Framework wcześniejszych niż 2.0 nie zapewniają obsługę debugowanie w trybie mieszanym dla procesów 64-bitowych. Oznacza to, że nie możesz wejść z kodu zarządzanego do kodu macierzystego lub kodu natywnego do zarządzanego kodu podczas debugowania.

 Aby obejść ten problem, możesz wykonywać następujące czynności:

-   Zaktualizuj projekt, aby użyć programu Microsoft .NET Framework w wersji 2.0 lub 3.0.

-   Debugowanie kodu zarządzanego i natywnego w oddzielnych sesji debugowania.

-   Debugowanie kodu mieszanego jako proces 32-bitowych, zgodnie z opisem w poniższych procedurach.

### <a name="to-change-the-operating-system-to-32-bit-visual-basic-or-c"></a>Aby zmienić system operacyjny na 32-bitowe (Visual Basic lub C#)

1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **właściwości** w menu skrótów.

2.  Na stronach właściwości kliknij przycisk **skompilować** lub **debugowania** kartę.

3.  Kliknij przycisk **platformy**, a następnie wybierz pozycję **x86** na liście platform.

     Domyślnie kompilatory języków Visual Basic i C# generuje kod wymagany do uruchomienia na dowolny procesor CPU. Na komputerze 64-bitowych te pliki binarne Uruchom jako procesów 64-bitowych. Aby uruchomić proces 32-bitowy, należy wybrać **Win32**, a nie **AnyCPU**.

### <a name="to-change-the-operating-system-to-32-bit-cc"></a>Aby zmienić system operacyjny na 32-bitowych (C/C++)

1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **właściwości** w menu skrótów.

     Na stronach właściwości kliknij przycisk **platformy**, a następnie wybierz pozycję **Win32** na liście platform.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

-   Zobacz [Konfigurowanie debugowania SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100)).

## <a name="see-also"></a>Zobacz też
- [Debugowanie aplikacji 64-bitowych](../debugger/debug-64-bit-applications.md)