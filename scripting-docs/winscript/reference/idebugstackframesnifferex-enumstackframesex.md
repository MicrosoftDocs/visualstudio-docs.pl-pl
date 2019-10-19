---
title: 'IDebugStackFrameSnifferEx:: EnumStackFramesEx | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrameSnifferEx.EnumStackFramesEx
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrameSnifferEx::EnumStackFramesEx
ms.assetid: b656b581-aff0-4984-8d8a-a1c7a8e6558a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a4062e7c0a9b3a82578daffa2ab7ef7e9ba614d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576707"
---
# <a name="idebugstackframesnifferexenumstackframesex"></a>IDebugStackFrameSnifferEx::EnumStackFramesEx
Zwraca moduł wyliczający ramek stosu dla bieżącego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwSpMin`  
 podczas Dolny limit adresów dla wyliczania ramek stosu.  
  
 `ppedsf`  
 określoną Moduł wyliczający ramek stosu dla bieżącego wątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Moduł wyliczający ramki stosu zwraca ramki zaczynające się na górze stosu z ostatnio wypchnięcią ramką. Moduł wyliczający zawiera tylko ramki stosu z adresami o wartości większej lub równej `dwSpMin`.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugStackFrameSnifferEx, interfejs](../../winscript/reference/idebugstackframesnifferex-interface.md)