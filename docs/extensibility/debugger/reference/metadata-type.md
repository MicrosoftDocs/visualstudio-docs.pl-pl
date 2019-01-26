---
title: METADATA_TYPE | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c276c34b902358ab355f1a67ffa1d97f4f0f8ce
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55034720"
---
# <a name="metadatatype"></a>METADATA_TYPE
Ta struktura określa informacje o typie pola pobierana z metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _tagTYPE_METADATA {  
   ULONG32  ulAppDomainID;  
   GUID     guidModule;  
   _mdToken tokClass;  
} METADATA_TYPE;  
```  
  
```csharp  
public struct METADATA_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public int  tokClass;  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 ulAppDomainID  
 Identyfikator aplikacji, z którego pochodzą symbolu. Służy do jednoznacznego identyfikowania wystąpienia aplikacji.  
  
 guidModule  
 Identyfikator GUID moduł, który zawiera tego pola.  
  
 tokClass  
 Identyfikator tokenu metadanych tego typu.  
  
 [C++] `_mdToken` jest `typedef` dla 32-bitowych `int`.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest wyświetlany jako część Unii w [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) struktury, kiedy `dwKind` pole `TYPE_INFO` struktury jest ustawiona na `TYPE_KIND_METADATA` (wartość z zakresu od [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) Wyliczenie).  
  
 `tokClass` Wartość tokenu metadanych, który unikatowo identyfikuje typ. Aby uzyskać więcej informacji na temat sposobu interpretacji górny bity identyfikator tokenu metadanych, zobacz `CorTokenType` wyliczenia w pliku sekcję corhdr.h w [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] zestawu SDK.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktur i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)