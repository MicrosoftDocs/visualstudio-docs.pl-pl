---
title: IDebugApplication::FIsAutoJitDebugEnabled | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FIsAutoJitDebugEnabled
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FIsAutoJitDebugEnabled
ms.assetid: 0551dd3b-e6eb-442a-8201-418f96fe62df
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f594c5ce48ebd31a265ed438db176c5707d9b079
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58152080"
---
# <a name="idebugapplicationfisautojitdebugenabled"></a>IDebugApplication::FIsAutoJitDebugEnabled
Określa, czy debuger just in time (JIT) został zarejestrowany do bez hostów auto-debug.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
BOOL FIsAutoJitDebugEnabled();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda się powiedzie, i debugera JIT jest zarejestrowana w celu bez hostów auto-debug, metoda zwraca `TRUE`. W przeciwnym razie zwraca `FALSE`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda określa, czy jest debugera JIT jest zarejestrowana w celu bez hostów auto-debug.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugApplication, interfejs](../../winscript/reference/idebugapplication-interface.md)