---
title: Debugowanie w trybie mieszanym dla procesów IA64 nie jest obsługiwane. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3cf7308b3302c682f32a2db9837f86cd0173260
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60101811"
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Debugowanie w trybie mieszanym dla procesów IA64 nie jest obsługiwane.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio nie obsługuje debugowanie kodu zarządzanego i natywnego w procesów IA64 w trybie mieszanym. Oznacza to, że nie możesz wejść z kodu zarządzanego do kodu macierzystego lub kodu natywnego do zarządzanego kodu podczas debugowania.  
  
### <a name="workarounds"></a>Rozwiązania  
  
- Debugowanie kodu zarządzanego i natywnego w oddzielnych sesji debugowania.  
  
     — lub —  
  
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
 [Debugowanie aplikacji 64-bitowych](../debugger/debug-64-bit-applications.md)
