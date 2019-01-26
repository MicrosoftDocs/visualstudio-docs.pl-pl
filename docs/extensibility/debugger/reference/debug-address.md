---
title: DEBUG_ADDRESS | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 420f8d6e065fc68077a134f6d7bb677690dc2b57
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972524"
---
# <a name="debugaddress"></a>DEBUG_ADDRESS
Ta struktura reprezentuje adres.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS {  
   ULONG32             ulAppDomainID;  
   GUID                guidModule;  
   _mdToken            tokClass;  
   DEBUG_ADDRESS_UNION addr;  
} DEBUG_ADDRESS;  
```  
  
```csharp  
public struct DEBUG_ADDRESS {  
   public uint                ulAppDomainID;  
   public Guid                guidModule;  
   public int                 tokClass;  
   public DEBUG_ADDRESS_UNION addr;  
}  
```  
  
## <a name="terms"></a>Warunki  
 ulAppDomainID  
 Identyfikator procesu.  
  
 guidModule  
 Identyfikator GUID moduł, który zawiera ten adres.  
  
 tokClass  
 Token, który identyfikuje klasy lub typ tego adresu.  
  
> [!NOTE]
>  Ta wartość jest specyficzne dla dostawcy symboli i dlatego nie ma znaczenia ogólne innych niż jako identyfikator dla typu klasy.  
  
 addr  
 A [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) struktury, która zawiera sumę struktur, które opisują typy poszczególnych adresów. Wartość `addr`.`dwKind` pochodzi z [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) wyliczenia, w którym wyjaśniono, jak interpretować Unii.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest przekazywany do [getaddress —](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) metodę, aby wypełnić.  
  
 **Ostrzeżenie [tylko w języku C++]**  
  
 Jeśli `addr.dwKind` jest `ADDRESS_KIND_METADATA_LOCAL` i, jeśli `addr.addr.addrLocal.pLocal` nie jest wartością null, a następnie należy wywołać `Release` tokenu wskaźnika:  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktur i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)