---
title: IEnumDebugExtendedPropertyInfo::GetCount | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.GetCount
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::GetCount
ms.assetid: 2c862f62-b57c-4cd4-ac4e-7d372fbda9a4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e56f1def9d797cc67d0a71813a4dd4b35589d7e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58156284"
---
# <a name="ienumdebugextendedpropertyinfogetcount"></a>IEnumDebugExtendedPropertyInfo::GetCount
Pobiera liczbę `ExtendedDebugPropertyInfo` struktury modułu wyliczającego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetCount (  
   ULONG* pcelt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcelt`  
 [out] Zwraca liczbę `ExtendedDebugPropertyInfo` struktury modułu wyliczającego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca prawidłową `HRESULT`, zazwyczaj `S_OK`.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumDebugExtendedPropertyInfo Interface](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo, struktura](../../winscript/reference/extendeddebugpropertyinfo-structure.md)