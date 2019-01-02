---
title: IDebugEnumField::GetStringFromValue | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eb3fc6a0e8aab20659abe7a2d8601f478f948a9b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53877409"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Ta metoda uzyskuje nazwę danego jej wartość stałej wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetStringFromValue(  
   ULONGLONG value,  
   BSTR*     pbstrValue  
);  
```  
  
```csharp  
int GetStringFromValue(  
   ulong      value,  
   out string pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `value`  
 [in] Wartość, dla którego należy pobrać nazwę wyliczenia stałej.  
  
 `pbstrValue`  
 [out] Zwraca nazwę stała wyliczenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` Jeśli wartość nie ma skojarzonego nazwy lub zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli istnieje więcej niż jedną nazwę skojarzonej z taką samą wartość, zostanie zwrócony imię zdefiniowane w wyliczeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)