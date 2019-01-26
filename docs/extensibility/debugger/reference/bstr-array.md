---
title: BSTR_ARRAY | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BSTR_ARRAY
helpviewer_keywords:
- BSTR_ARRAY structure
ms.assetid: 48da37f7-a237-48a9-9ff9-389c1a00862c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14f05949dd275a7f1566b8cec3a49903249e3de1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037203"
---
# <a name="bstrarray"></a>BSTR_ARRAY
Struktura, która opisuje tablicę ciągów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct tagBSTR_ARRAY {  
   DWORD dwCount;  
   BSTR* Members;  
} BSTR_ARRAY;  
```  
  
```csharp  
struct BSTR_ARRAY {  
   DWORD    dwCount;  
   string[] Members;  
}  
```  
  
## <a name="terms"></a>Warunki  
 dwCount  
 Liczba parametrów w `Members` tablicy.  
  
 Elementy członkowskie  
 Tablica ciągów.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest zwracana z [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) metody.  
  
 [Tylko w języku C++] Każdy ciąg pojedynczych musi zostać uwolniona za pomocą `SysFreeString`i `Members` tablicy musi być zwolniona przez `CoTaskMemFree`.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktur i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)