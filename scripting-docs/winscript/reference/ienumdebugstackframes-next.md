---
title: 'IEnumDebugStackFrames:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Next
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Next
ms.assetid: ade3f5b0-8ff3-48a0-9433-270789e6d53e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17261f8ba9b2957d33ed7019c16f2e1423b6b42e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575546"
---
# <a name="ienumdebugstackframesnext"></a>IEnumDebugStackFrames::Next
Pobiera określoną liczbę segmentów w sekwencji wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Next(  
   ULONG                       celt,  
   DebugStackFrameDescriptor*  prgdsfd,  
   ULONG*                      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 podczas Liczba segmentów do pobrania.  
  
 `prgdsfd`  
 określoną Zwraca tablicę `DebugStackFrameDescriptor` interfejsów, które reprezentują segmenty, które są pobierane.  
  
 `pceltFetched`  
 określoną Rzeczywista liczba segmentów pobranych przez moduł wyliczający.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda pobiera określoną liczbę segmentów w sekwencji wyliczenia.  
  
## <a name="see-also"></a>Zobacz także  
 [IEnumDebugStackFrames   interfejsu](../../winscript/reference/ienumdebugstackframes-interface.md)  
 [DebugStackFrameDescriptor, struktura](../../winscript/reference/debugstackframedescriptor-structure.md)