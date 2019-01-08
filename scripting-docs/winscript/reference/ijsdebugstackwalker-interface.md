---
title: IJsDebugStackWalker, interfejs | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d79950c6d5595a0a8a95623a7510c5523f16e41b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087903"
---
# <a name="ijsdebugstackwalker-interface"></a>IJsDebugStackWalker — Interfejs
Przedstawia walker stosu dla określonego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IJsDebugStackWalker::GetNext, metoda](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Pobiera następną klatkę.|  
  
## <a name="remarks"></a>Uwagi  
 Walkery stosu można tworzyć tylko w przypadku, gdy element docelowy jest zatrzymany i są nieprawidłowe, gdy proces docelowy jest kontynuowane ponownie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsów skryptów systemu Windows](../../winscript/reference/windows-script-interfaces-reference.md)