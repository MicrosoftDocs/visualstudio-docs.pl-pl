---
title: Jak można debugować funkcje API systemu Windows? | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.api
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8c5fd73eb64c79ac9476c0036b9f2d709294d178
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704594"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Jak można debugować funkcje API systemu Windows?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli chcesz debugować funkcję interfejsu API systemu Windows z załadowanymi symbolami NT, należy wykonać następujące czynności.  
  
### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Aby ustawić punkt przerwania w funkcji interfejsu API systemu Windows z załadowanymi symbolami NT  
  
- Wprowadź nazwę funkcji wraz z nazwą biblioteki DLL, w której znajduje się funkcja. W kodzie 32-bitowym, użyj dekoracyjnej formy nazwy funkcji. Aby ustawić punkt przerwania na **MessageBeep**, na przykład należy wprowadzić następujące polecenie.  
  
    ```  
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     Aby uzyskać nazwę dekoracyjną, zobacz [Wyświetlanie dekoracyjnych nazw](https://msdn.microsoft.com/f79e2717-a4db-4d12-a689-69830cce2be0).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie często zadawanych pytań dotyczących kodu natywnego](../debugger/debugging-native-code-faqs.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
