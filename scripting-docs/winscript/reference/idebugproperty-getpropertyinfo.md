---
title: IDebugProperty::GetPropertyInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetPropertyInfo
ms.assetid: b201c0c4-bff6-4285-880f-67be90584c5f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51cf7fae597d95b0d9098d6b2dc6950c2d06bfa0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979152"
---
# <a name="idebugpropertygetpropertyinfo"></a>IDebugProperty::GetPropertyInfo
Pobiera wartość `IDebugProperty` , który opisuje metodę lub właściwość indeksowana.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetPropertyInfo (  
   DBGPROP_INFO_FLAGSdwFields,  
   UINT nRadix,  
   DebugPropertyInfo* pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFields`  
 [in] Określa `DBGPROP_INFO_FLAGS` stałe, określające pola do wypełniania w `DebugPropertyInfo` struktury.  
  
 `nRadix`  
 [in] Podstawy ma być używany w formatowaniu wszelkie dane liczbowe.  
  
 `pPropertyInfo`  
 [out] Zwraca `DebugPropertyInfo` struktury, który opisuje właściwości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca prawidłową `HRESULT`, zazwyczaj `S_OK`.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [DebugPropertyInfo, struktura](../../winscript/reference/debugpropertyinfo-structure.md)