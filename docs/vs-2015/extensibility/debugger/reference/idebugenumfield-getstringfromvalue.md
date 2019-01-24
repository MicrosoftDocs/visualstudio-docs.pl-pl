---
title: IDebugEnumField::GetStringFromValue | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ecdd60c363e30afbe4c61e8e18660a17a06a5ce8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54791778"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta metoda uzyskuje nazwę danego jej wartość stałej wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
