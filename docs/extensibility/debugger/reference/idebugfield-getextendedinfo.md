---
title: IDebugField::GetExtendedInfo | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ef431fbc3bf14124ee0ea08a2439c0473e958a91
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945213"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Ta metoda pobiera rozszerzone informacje dotyczące pola.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetExtendedInfo(   
   REFGUID guidExtendedInfo,  
   BYTE**  prgBuffer,  
   DWORD*  pdwLen  
);  
```  
  
```csharp  
int GetExtendedInfo(  
   ref Guid guidExtendedInfo,   
   IntPtr[] prgBuffer,   
   ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `guidExtendedInfo`  
 [in] Wybiera informacje, które mają zostać zwrócone. Prawidłowe wartości to:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`guidConstantValue`|Wartość atrybutu jako sekwencja bajtów.|  
|`guidConstantType`|Typ jako typ podpisu.|  
  
 `prgBuffer`  
 [out] Zwraca informacje o rozszerzonych.  
  
 `pdwLen`  
 [out w] Zwraca rozmiar rozszerzone informacje w bajtach.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Obecnie metoda ta zwraca tylko typ lub wartość stałą. Obiekt wywołujący należy zwolnić buforu zwracane w `prgBuffer` przez wywołanie modelu COM `CoTaskMemFree` — funkcja (C++) lub <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C#).  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)