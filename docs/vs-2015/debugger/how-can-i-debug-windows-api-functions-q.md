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
ms.openlocfilehash: d7729782fe23c1404aa6862116e884baa97b17f5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60103605"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Jak można debugować funkcje API systemu Windows?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli chcesz debugować funkcja interfejsu API Windows, która zawiera symbole NT załadowane, wykonaj następujące czynności.  
  
### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Aby ustawić punkt przerwania w funkcji Windows API z symbole NT załadowane  
  
- Podaj nazwę funkcji wraz z nazwą biblioteki DLL, w której znajduje się funkcja. W 32-bitowego kodu formularz dekorowane nazwy funkcji. Aby ustawić punkt przerwania na **MessageBeep**, na przykład, należy wprowadzić następujące czynności.  
  
    ```  
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     Aby uzyskać nazwę z atrybutami, zobacz [wyświetlania nazw Ozdobionych](http://msdn.microsoft.com/f79e2717-a4db-4d12-a689-69830cce2be0).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
