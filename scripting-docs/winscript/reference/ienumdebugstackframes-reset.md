---
title: 'IEnumDebugStackFrames:: Reset | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Reset
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Reset
ms.assetid: 57be2683-5346-4464-bdf5-6fd45b56253a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ddd97d60d40eaa15a5ed3e17cc87a0d9ffb197cf
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574861"
---
# <a name="ienumdebugstackframesreset"></a>IEnumDebugStackFrames::Reset
Resetuje sekwencję wyliczenia na początek.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Reset();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda resetuje sekwencję wyliczenia na początek.  
  
## <a name="see-also"></a>Zobacz także  
 [IEnumDebugStackFrames, interfejs](../../winscript/reference/ienumdebugstackframes-interface.md)