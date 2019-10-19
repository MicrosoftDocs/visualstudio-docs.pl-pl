---
title: 'IDebugProperty:: GetExtendedInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetExtendedInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetExtendedInfo
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 130d11c8ed6bb21210d129bb9aace779db3bd54b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562388"
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
Pobiera rozszerzone informacje dla właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cInfos`  
 podczas Liczba obiektów informacji rozszerzonych.  
  
 `rgguidExtendedInfo`  
 podczas Tablica `GUID`s jest przenoszona, aby można było jednocześnie pobrać wiele elementów rozszerzonych informacji.  
  
 `pExtendedInfo`  
 określoną Zwraca tablicę `VARIANT`s, która może być używana do pobierania informacji o właściwościach rozszerzonych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca prawidłowy `HRESULT`, zazwyczaj `S_OK`.  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs pobiera rozszerzone informacje dla tego obiektu. Interfejs API istnieje tylko na potrzeby pobierania informacji, które nie dają się do pobrania przy użyciu `IDebugProperty::GetPropertyInfo`).  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugProperty, interfejs](../../winscript/reference/idebugproperty-interface.md)