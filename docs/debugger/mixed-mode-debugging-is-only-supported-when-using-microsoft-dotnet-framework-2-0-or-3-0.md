---
title: Debugowanie w trybie mieszanym jest obsługiwane tylko w przypadku korzystania z Microsoft .NET Framework 2,0 lub 3,0 | Microsoft Docs
description: Wersje Microsoft .NET Framework starsze niż 2,0 nie zapewniają obsługi debugowania w trybie mieszanym dla procesów 64-bitowych. Zapoznaj się z tym artykułem.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 497eed63b695557fe19f7fd2cf5bb4900d632355
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913187"
---
# <a name="mixed-mode-debugging-is-only-supported-when-using-microsoft-net-framework-20-or-30"></a>Debugowanie w trybie mieszanym jest obsługiwane tylko w przypadku korzystania z programu Microsoft .NET Framework 2.0 or 3.0
Wersje Microsoft .NET Framework starsze niż 2,0 nie zapewniają obsługi debugowania w trybie mieszanym dla procesów 64-bitowych. Oznacza to, że nie można wykonać kroków z kodu zarządzanego do kodu natywnego lub z kodu natywnego do kodu zarządzanego podczas debugowania.

 Aby obejść ten problem, możesz:

- Zaktualizuj projekt, tak aby korzystał z Microsoft .NET Framework 2,0 lub 3,0.

- Debuguj kod zarządzany i natywny w oddzielnych sesjach debugowania.

- Debuguj kod mieszany jako proces 32-bitowy, zgodnie z opisem w poniższych procedurach.

### <a name="to-change-the-operating-system-to-32-bit-visual-basic-or-c"></a>Aby zmienić system operacyjny na 32-bitowy (Visual Basic lub C#)

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt, a następnie kliknij polecenie **Właściwości** w menu skrótów.

2. Na stronie właściwości kliknij kartę **Kompiluj** lub **Debuguj** .

3. Kliknij pozycję **platforma**, a następnie wybierz pozycję **x86** z listy platform.

     Domyślnie kompilatory Visual Basic i C# tworzą kod do uruchomienia na dowolnym procesorze CPU. Na komputerze 64-bitowym te pliki binarne są uruchamiane jako procesy 64-bitowe. Aby uruchomić program w procesie 32-bitowym, należy wybrać **Win32**, a nie **AnyCPU**.

### <a name="to-change-the-operating-system-to-32-bit-cc"></a>Aby zmienić system operacyjny na 32-bitowy (C/C++)

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt, a następnie kliknij polecenie **Właściwości** w menu skrótów.

     Na stronie właściwości kliknij pozycję **platforma**, a następnie wybierz pozycję **Win32** z listy platform.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Zobacz [Konfigurowanie debugowania SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100)).

## <a name="see-also"></a>Zobacz też
- [Debuguj 64-bitowe aplikacje](../debugger/debug-64-bit-applications.md)