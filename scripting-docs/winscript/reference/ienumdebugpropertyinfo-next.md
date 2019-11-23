---
title: 'IEnumDebugPropertyInfo:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Next
ms.assetid: 052837ac-1599-49cc-9a5a-ba90f992eeff
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b99631c217ca56dce91512403dfb6623cd1e7641
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574194"
---
# <a name="ienumdebugpropertyinfonext"></a>IEnumDebugPropertyInfo::Next
Pobiera określoną liczbę struktur `DebugPropertyInfo` w sekwencji wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Next (  
   ULONGcelt,  
   DebugPropertyInfo*rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 podczas Liczba struktur `DebugPropertyInfo`do pobrania.  
  
 `rgelt`  
 określoną Pobrano tablicę struktur `DebugPropertyInfo`.  
  
 `pceltFetched`  
 określoną Zwraca liczbę struktur `DebugPropertyInfo` rzeczywiście pobranych.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Zwraca prawidłowy `HRESULT`, zazwyczaj `S_OK`.  
  
## <a name="see-also"></a>Zobacz także  
 [IEnumDebugPropertyInfo  interfejsu](../../winscript/reference/ienumdebugpropertyinfo-interface.md)  
 [DebugPropertyInfo, struktura](../../winscript/reference/debugpropertyinfo-structure.md)