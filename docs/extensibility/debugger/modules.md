---
title: Moduły | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cdcaa4afb2191c80a8b5bed1bedf68f4c217f029
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55008312"
---
# <a name="modules"></a>Moduły
Pod względem architektury debugera *modułu*:  
  
-   Jest kontenerem fizycznych kodu, takie jak plik wykonywalny lub bibliotekę DLL.  
  
-   Można ponownie załadować jej symboli i opisania siebie. Moduł opisy są wyświetlane w oknie moduły środowiska IDE.  
  
-   Jest reprezentowany przez [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) interfejsu, utworzonych przez aparat debugowania w celu opisania modułu.  
  
## <a name="see-also"></a>Zobacz także  
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)