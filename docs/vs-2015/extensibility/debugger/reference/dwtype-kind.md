---
title: dwTYPE_KIND | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f37fb773a07291a883f5cb65e4cb4ac840a87a14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198781"
---
# <a name="dwtype_kind"></a>dwTYPE_KIND
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa sposób interpretowania typu obiektu [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
  
typedef DWORD dwTYPE_KIND;  
```  
  
```csharp  
public enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 TYPE_KIND_METADATA  
 Unia [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) powinna być interpretowana jako struktura [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) .  
  
 TYPE_KIND_PDB  
 `TYPE_INFO`Unia powinna być interpretowana jako struktura [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) .  
  
 TYPE_KIND_BUILT  
 `TYPE_INFO`Unia powinna być interpretowana jako struktura [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) .  
  
## <a name="remarks"></a>Uwagi  
 Wartości tego wyliczenia pojawiają się w `dwKind` polu struktury [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) i służą do określania sposobu interpretowania `type` elementu członkowskiego Unii. `TYPE_INFO`Struktura jest zwracana przez wywołanie metody. [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
