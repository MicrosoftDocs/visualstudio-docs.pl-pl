---
title: Debugowanie w trybie mieszanym jest obsługiwane tylko podczas korzystania z programu Microsoft .NET Framework 2.0 lub 3.0 | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696469"
---
# <a name="mixed-mode-debugging-is-only-supported-when-using-microsoft-net-framework-20-or-30"></a>Debugowanie w trybie mieszanym jest obsługiwane tylko w przypadku korzystania z programu Microsoft .NET Framework 2.0 or 3.0
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wersje programu Microsoft .NET Framework wcześniejszych niż 2.0 nie zapewniają obsługę debugowanie w trybie mieszanym dla procesów 64-bitowych. Oznacza to, że nie możesz wejść z kodu zarządzanego do kodu macierzystego lub kodu natywnego do zarządzanego kodu podczas debugowania.  
  
 Aby obejść ten problem, możesz wykonywać następujące czynności:  
  
- Zaktualizuj projekt, aby użyć programu Microsoft .NET Framework w wersji 2.0 lub 3.0.  
  
- Debugowanie kodu zarządzanego i natywnego w oddzielnych sesji debugowania.  
  
- Debugowanie kodu mieszanego jako proces 32-bitowych, zgodnie z opisem w poniższych procedurach.  
  
### <a name="to-change-the-operating-system-to-32-bit-visual-basic-or-c"></a>Aby zmienić system operacyjny na 32-bitowe (Visual Basic lub C#)  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **właściwości** w menu skrótów.  
  
2. Na stronach właściwości kliknij przycisk **skompilować** lub **debugowania** kartę.  
  
3. Kliknij przycisk **platformy**, a następnie wybierz pozycję **x86** na liście platform.  
  
     Domyślnie kompilatory języków Visual Basic i C# generuje kod wymagany do uruchomienia na dowolny procesor CPU. Na komputerze 64-bitowych te pliki binarne Uruchom jako procesów 64-bitowych. Aby uruchomić proces 32-bitowy, należy wybrać **Win32**, a nie **AnyCPU**.  
  
### <a name="to-change-the-operating-system-to-32-bit-cc"></a>Aby zmienić system operacyjny na 32-bitowych (C/C++)  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **właściwości** w menu skrótów.  
  
     Na stronach właściwości kliknij przycisk **platformy**, a następnie wybierz pozycję **Win32** na liście platform.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Zobacz [Konfigurowanie debugowania SQL](https://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji 64-bitowych](../debugger/debug-64-bit-applications.md)
