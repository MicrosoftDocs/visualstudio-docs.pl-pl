---
title: 'Błąd: debugowanie w trybie mieszanym dla procesów x64 jest obsługiwane tylko w przypadku korzystania z Microsoft .NET Framework 4 lub nowszego | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e4b0216c-7006-4832-883f-08e982ba8d3f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 190a6e890ce31ce2aa66ff474bb9e4b1976a6c46
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67824008"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Błąd: debugowanie w trybie mieszanym dla procesów x64 jest obsługiwane tylko w przypadku korzystania z programu Microsoft .NET Framework 4 lub nowszej wersji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby debugować mieszany kod natywny i zarządzany w procesie 64-bitowym, musisz mieć [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] wersję 4. Debugowanie w trybie mieszanym 64-bitowych procesów z [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] wersjami wcześniejszymi niż 4 nie jest obsługiwane.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Wykonaj jedną z następujących czynności:  
  
  - Uaktualnij [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] do wersji 4.  

  - Utwórz 32-bitową wersję aplikacji na potrzeby debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie narzędzi zdalnych na urządzeniu](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
