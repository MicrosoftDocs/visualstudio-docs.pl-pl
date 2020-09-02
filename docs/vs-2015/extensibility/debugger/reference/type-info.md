---
title: TYPE_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 12102c297c34649c753cf1c811994f9e750b9605
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64837094"
---
# <a name="type_info"></a>TYPE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta struktura określa różne rodzaje informacji o typie pola.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
struct _tagTYPE_INFO_UNION {  
   dwTYPE_KIND dwKind;  
   union {  
      METADATA_TYPE typeMeta;  
      PDB_TYPE      typePdb;  
      BUILT_TYPE    typeBuilt;  
      DWORD         unused;  
   } type;  
} TYPE_INFO;  
```  
  
```csharp  
public struct TYPE_INFO {  
   public uint   dwKind;  
   public IntPtr unionmember;  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 dwKind  
 Wartość z wyliczenia [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) , która określa sposób interpretacji związku.  
  
 Type. typeMeta  
 [Tylko C++] Zawiera strukturę [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) , jeśli `dwKind` jest `TYPE_KIND_METADATA` .  
  
 Type. typePdb  
 [Tylko C++] Zawiera strukturę [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) , jeśli `dwKind` jest `TYPE_KIND_PDB` .  
  
 Type. typeBuilt  
 [Tylko C++] Zawiera strukturę [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) , jeśli `dwKind` jest `TYPE_KIND_BUILT` .  
  
 Typ. nieużywany  
 Nieużywane uzupełnienie.  
  
 typ  
 Nazwa Unii.  
  
 unionmember  
 [Tylko w C#] Kierowanie tego elementu do odpowiedniego typu struktury na podstawie `dwKind` .  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest przenoszona do [metody, w której](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) jest wypełniana. Sposób interpretacji zawartości struktury jest określana na podstawie `dwKind` pola.  
  
> [!NOTE]
> [Tylko C++] Jeśli jest `dwKind` równe `TYPE_KIND_BUILT` , to konieczne jest zwolnienie bazowego obiektu [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) podczas niszczenia `TYPE_INFO` struktury. W tym celu należy wywołać metodę `typeInfo.type.typeBuilt.pUnderlyingField->Release()` .  
  
 [Tylko w C#] W poniższej tabeli pokazano, jak interpretować `unionmember` element członkowski dla każdego typu. W przykładzie pokazano, jak to zrobić w przypadku jednego rodzaju typu.  
  
|`dwKind`|`unionmember` interpretowane jako|  
|--------------|----------------------------------|  
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## <a name="example"></a>Przykład  
 Ten przykład pokazuje, jak interpretować `unionmember` element członkowski `TYPE_INFO` struktury w języku C#. Ten przykład pokazuje interpretowanie tylko jednego typu ( `TYPE_KIND_METADATA` ), ale inne są interpretowane w taki sam sposób.  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(TYPE_INFO ti)  
        {  
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)  
            {  
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,  
                                               typeof(METADATA_TYPE));  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
