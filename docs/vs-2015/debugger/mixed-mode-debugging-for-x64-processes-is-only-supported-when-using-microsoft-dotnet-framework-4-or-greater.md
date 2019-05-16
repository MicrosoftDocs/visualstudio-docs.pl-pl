---
title: Mieszany tryb debugowania x64 procesów jest obsługiwana tylko w przypadku korzystania z programu Microsoft.NET Framework 4 lub nowszej | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697832"
---
# <a name="mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoftnet-framework-4-or-greater"></a>Debugowanie w trybie mieszanym dla procesów x64 jest obsługiwane tylko w przypadku korzystania z programu Microsoft .NET Framework 4 lub nowszej wersji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

.NET Framework w wersji starszej niż 4 nie dostarcza obsługi dla x64 debugowanie trybu mieszanego procesów. Oznacza to, że nie możesz wejść z kodu zarządzanego do kodu macierzystego lub kodu natywnego do zarządzanego kodu podczas debugowania.  
  
### <a name="workarounds"></a>Rozwiązania  
  
- Zaktualizuj projekt, aby użyć programu Microsoft .NET Framework 4 lub nowszej.  
  
     — lub —  
  
     Debugowanie kodu zarządzanego i natywnego w oddzielnych sesji debugowania.  
  
     — lub —  
  
     Debugowanie kodu mieszanego jako proces 32-bitowych, zgodnie z opisem w poniższych procedurach.  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Aby zmienić platformy 32-bitowe (Visual Basic lub C#)  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **właściwości**.  
  
2. Na stronach właściwości kliknij przycisk **skompilować** lub **debugowania** kartę.  
  
3. Kliknij przycisk **platformy** i wybierać x86 listę platform.  
  
     Domyślnie domyślne Kompilatory języka Visual Basic i C# generuje kod wymagany do uruchomienia na dowolny procesor CPU. Na komputerze 64-bitowych te pliki binarne Uruchom jako procesów 64-bitowych. Aby uruchomić proces 32-bitowy, należy wybrać **Win32**, a nie **AnyCPU**.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>Aby zmienić platformy 32-bitowych (C/C++)  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **właściwości**.  
  
2. Na stronach właściwości kliknij przycisk **platformy** i wybierz listę platform systemu Win32.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Zobacz [Konfigurowanie debugowania SQL](https://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji 64-bitowych](../debugger/debug-64-bit-applications.md)
