---
title: METADATA_ADDRESS_FIELD | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- METADATA_ADDRESS_FIELD
helpviewer_keywords:
- METADATA_ADDRESS_FIELD structure
ms.assetid: 15ab45fe-6b3b-4e09-880b-31b34f523607
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7d3a85126d58839da2bd04de32ea4d9dd09c405
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070893"
---
# <a name="metadataaddressfield"></a>METADATA_ADDRESS_FIELD
Ta struktura reprezentuje adresu pola klasy lub struktury.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_FIELD {  
   _mdToken tokField;  
} METADATA_ADDRESS_FIELD  
```  
  
```csharp  
public struct METADATA_ADDRESS_FIELD {  
   public int tokField;  
}  
```  
  
## <a name="terms"></a>Warunki  
 tokField  
 Identyfikator tokenu pola.  
  
 [C++] `_mdToken` jest `typedef` dla 32-bitowych `int`.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest częścią Unii w [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) struktury, kiedy `dwKind` pole `DEBUG_ADDRESS_UNION` struktury jest ustawiona na `ADDRESS_KIND_FIELD` (wartość z zakresu od [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) Wyliczenie).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktur i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)