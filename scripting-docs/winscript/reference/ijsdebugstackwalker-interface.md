---
title: IJsDebugStackWalker Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d06af2c509339d9499f66e1f267c54c69951e225
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58150897"
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