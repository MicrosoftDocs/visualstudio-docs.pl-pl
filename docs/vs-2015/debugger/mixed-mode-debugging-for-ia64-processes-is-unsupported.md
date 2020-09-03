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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203289"
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Debugowanie w trybie mieszanym dla procesów IA64 nie jest obsługiwane.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio nie obsługuje debugowania w trybie mieszanym kodu zarządzanego i natywnego w procesach IA64. Oznacza to, że nie można wykonać kroków z kodu zarządzanego do kodu natywnego lub z kodu natywnego do kodu zarządzanego podczas debugowania.  
  
### <a name="workarounds"></a>Obejścia  
  
- Debuguj kod zarządzany i natywny w oddzielnych sesjach debugowania.  
  
     oraz  
  
     Debuguj kod mieszany jako proces 32-bitowy, zgodnie z opisem w poniższych procedurach.  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Aby zmienić platformę na 32-bitową (Visual Basic lub C#)  
  
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie w menu skrótów kliknij polecenie **Właściwości** .  
  
2. Na stronie właściwości kliknij kartę **Kompiluj** lub **Debuguj** .  
  
3. Kliknij pozycję **platforma** i wybierz pozycję x86 z listy platform.  
  
     Domyślnie kompilatory Visual Basic i C# domyślnie tworzą kod do uruchomienia na dowolnym procesorze CPU. Na komputerze 64-bitowym te pliki binarne są uruchamiane jako procesy 64-bitowe. Aby uruchomić program w procesie 32-bitowym, należy wybrać **Win32**, a nie **AnyCPU**.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>Aby zmienić platformę na 32-bitową (C/C++)  
  
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie w menu skrótów kliknij polecenie **Właściwości** .  
  
2. Na stronie właściwości kliknij pozycję **platforma** , a następnie wybierz pozycję Win32 z listy platform.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji 64-bitowych](../debugger/debug-64-bit-applications.md)
