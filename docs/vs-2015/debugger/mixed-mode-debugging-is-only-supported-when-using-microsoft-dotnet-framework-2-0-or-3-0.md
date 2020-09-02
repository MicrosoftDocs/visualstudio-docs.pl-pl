---
title: Debugowanie w trybie mieszanym jest obsługiwane tylko w przypadku korzystania z Microsoft .NET Framework 2,0 lub 3,0 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_to_old
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: f607af6f-57fe-472a-a32e-b6202067aa96
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fc45927ad6cc1189ed1d08328b4dd362821cdcb6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696469"
---
# <a name="mixed-mode-debugging-is-only-supported-when-using-microsoft-net-framework-20-or-30"></a>Debugowanie w trybie mieszanym jest obsługiwane tylko w przypadku korzystania z programu Microsoft .NET Framework 2.0 or 3.0
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wersje Microsoft .NET Framework starsze niż 2,0 nie zapewniają obsługi debugowania w trybie mieszanym dla procesów 64-bitowych. Oznacza to, że nie można wykonać kroków z kodu zarządzanego do kodu natywnego lub z kodu natywnego do kodu zarządzanego podczas debugowania.  
  
 Aby obejść ten problem, możesz:  
  
- Zaktualizuj projekt, tak aby korzystał z Microsoft .NET Framework 2,0 lub 3,0.  
  
- Debuguj kod zarządzany i natywny w oddzielnych sesjach debugowania.  
  
- Debuguj kod mieszany jako proces 32-bitowy, zgodnie z opisem w poniższych procedurach.  
  
### <a name="to-change-the-operating-system-to-32-bit-visual-basic-or-c"></a>Aby zmienić system operacyjny na 32-bitowy (Visual Basic lub C#)  
  
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie kliknij polecenie **Właściwości** w menu skrótów.  
  
2. Na stronie właściwości kliknij kartę **Kompiluj** lub **Debuguj** .  
  
3. Kliknij pozycję **platforma**, a następnie wybierz pozycję **x86** z listy platform.  
  
     Domyślnie kompilatory Visual Basic i C# tworzą kod do uruchomienia na dowolnym procesorze CPU. Na komputerze 64-bitowym te pliki binarne są uruchamiane jako procesy 64-bitowe. Aby uruchomić program w procesie 32-bitowym, należy wybrać **Win32**, a nie **AnyCPU**.  
  
### <a name="to-change-the-operating-system-to-32-bit-cc"></a>Aby zmienić system operacyjny na 32-bitowy (C/C++)  
  
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie kliknij polecenie **Właściwości** w menu skrótów.  
  
     Na stronie właściwości kliknij pozycję **platforma**, a następnie wybierz pozycję **Win32** z listy platform.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Zobacz [Konfigurowanie debugowania SQL](https://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji 64-bitowych](../debugger/debug-64-bit-applications.md)
