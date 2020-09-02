---
title: Debugowanie w trybie mieszanym dla procesów x64 jest obsługiwane tylko w przypadku korzystania z programu Microsoft.NET Framework 4 lub nowszego | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e974269cccb65db66ee59735f7acc5de494e2106
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697832"
---
# <a name="mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoftnet-framework-4-or-greater"></a>Debugowanie w trybie mieszanym dla procesów x64 jest obsługiwane tylko w przypadku korzystania z programu Microsoft .NET Framework 4 lub nowszej wersji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wersje .NET Framework w wersji wcześniejszej niż 4 nie zapewniają obsługi debugowania w trybie mieszanym dla procesów x64. Oznacza to, że nie można wykonać kroków z kodu zarządzanego do kodu natywnego lub z kodu natywnego do kodu zarządzanego podczas debugowania.  
  
### <a name="workarounds"></a>Obejścia  
  
- Zaktualizuj projekt, tak aby używał Microsoft .NET Framework 4 lub nowszego.  
  
     oraz  
  
     Debuguj kod zarządzany i natywny w oddzielnych sesjach debugowania.  
  
     oraz  
  
     Debuguj kod mieszany jako proces 32-bitowy, zgodnie z opisem w poniższych procedurach.  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Aby zmienić platformę na 32-bitową (Visual Basic lub C#)  
  
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie kliknij polecenie **Właściwości**.  
  
2. Na stronie właściwości kliknij kartę **kompilacja** lub **Debuguj** .  
  
3. Kliknij pozycję **platforma** i wybierz pozycję x86 z listy platform.  
  
     Domyślnie kompilatory Visual Basic i C# domyślnie tworzą kod do uruchomienia na dowolnym procesorze CPU. Na komputerze 64-bitowym te pliki binarne są uruchamiane jako procesy 64-bitowe. Aby uruchomić program w procesie 32-bitowym, należy wybrać **Win32**, a nie **AnyCPU**.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>Aby zmienić platformę na 32-bitową (C/C++)  
  
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie kliknij polecenie **Właściwości**.  
  
2. Na stronie właściwości kliknij pozycję **platforma** , a następnie wybierz pozycję Win32 z listy platform.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Zobacz [Konfigurowanie debugowania SQL](https://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji 64-bitowych](../debugger/debug-64-bit-applications.md)
