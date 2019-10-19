---
title: 'IDebugApplication:: FCanJitDebug | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FCanJitDebug
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FCanJitDebug
ms.assetid: d7ddac65-4864-411f-bf66-34a46c03f239
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d68240ffd86935e9936642c09d5131f70b46e9ab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576875"
---
# <a name="idebugapplicationfcanjitdebug"></a>IDebugApplication::FCanJitDebug
Określa, czy debuger just in Time (JIT) jest zarejestrowany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
BOOL FCanJitDebug();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się pomyślnie i zostanie zarejestrowany debuger JIT, metoda zwróci `TRUE`. W przeciwnym razie zwraca `FALSE`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda określa, czy debuger JIT jest zarejestrowany.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugApplication, interfejs](../../winscript/reference/idebugapplication-interface.md)