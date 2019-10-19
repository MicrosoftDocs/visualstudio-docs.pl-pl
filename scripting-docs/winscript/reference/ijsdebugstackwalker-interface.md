---
title: Interfejs IJsDebugStackWalker | Microsoft Docs
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
ms.openlocfilehash: 3b06b8c1f9282c42599c798030440c30450ef6dd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574019"
---
# <a name="ijsdebugstackwalker-interface"></a>IJsDebugStackWalker — Interfejs
Reprezentuje Analizator stosu dla określonego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IJsDebugStackWalker::GetNext, metoda](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Pobiera następną ramkę.|  
  
## <a name="remarks"></a>Uwagi  
 Przeszukiwania stosu można tworzyć tylko w czasie, gdy element docelowy jest zatrzymany, i są nieprawidłowe, gdy proces docelowy jest kontynuowany ponownie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** Jscript9diag. h  
  
## <a name="see-also"></a>Zobacz także  
 [Dokumentacja interfejsów skryptów systemu Windows](../../winscript/reference/windows-script-interfaces-reference.md)