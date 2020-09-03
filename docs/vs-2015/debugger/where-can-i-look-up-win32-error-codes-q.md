---
title: Gdzie można sprawdzić kody błędów Win32? | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vc.errors
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d403315a2320589f69174109d55c8726ffd5f673
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149393"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Gdzie można sprawdzić kody błędów Win32?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

WINERROR. H w katalogu dołączania domyślnej instalacji systemu zawiera definicje kodu błędów dla funkcji Win32 API.  
  
 Kod błędu można wyszukać, wpisując kod w oknie **czujka** lub oknie dialogowym **QuickWatch** . Na przykład:  
  
```  
0x80000004,hr  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie często zadawanych pytań dotyczących kodu natywnego](../debugger/debugging-native-code-faqs.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
