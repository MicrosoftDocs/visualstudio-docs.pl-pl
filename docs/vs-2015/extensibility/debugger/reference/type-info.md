---
title: TYPE_INFO | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 628d6e5ae2e13ea117cb3fd50aca3ba2150ac59f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755457"
---
# <a name="typeinfo"></a>TYPE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta struktura określa różne rodzaje informacji na temat typu pola.  
  
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
 Wartość z zakresu od [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) wyliczenie, które określa, jak interpretować Unii.  
  
 type.typeMeta  
 [Tylko w języku C++] Zawiera [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) struktury, jeśli `dwKind` jest `TYPE_KIND_METADATA`.  
  
 type.typePdb  
 [Tylko w języku C++] Zawiera [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) struktury, jeśli `dwKind` jest `TYPE_KIND_PDB`.  
  
 type.typeBuilt  
 [Tylko w języku C++] Zawiera [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) struktury, jeśli `dwKind` jest `TYPE_KIND_BUILT`.  
  
 type.unused  
 Dopełnienie nieużywane.  
  
 — typ  
 Nazwa Unii.  
  
 unionmember  
 [C# tylko] To typ odpowiednią strukturą ustalane na podstawie Marshal `dwKind`.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest przekazywany do [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) metody, gdzie jest wypełnione. Sposób interpretowania zawartość struktury opiera się na `dwKind` pola.  
  
> [!NOTE]
>  [Tylko w języku C++] Jeśli `dwKind` jest równa `TYPE_KIND_BUILT`, jest zwolnić bazowego [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiektu, kiedy niszczenie `TYPE_INFO` struktury. Jest to realizowane przez wywołanie `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.  
  
 [C# tylko] W poniższej tabeli przedstawiono, jak interpretować `unionmember` składowej dla każdego rodzaju typu. W przykładzie pokazano, jak to zrobić dla jednego rodzaju.  
  
|`dwKind`|`unionmember` interpretowane jako|  
|--------------|----------------------------------|  
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak interpretować `unionmember` członkiem `TYPE_INFO` struktury w języku C#. W tym przykładzie interpretowanie tylko jeden typ (`TYPE_KIND_METADATA`), ale inne są interpretowane w taki sam sposób.  
  
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
 Nagłówek: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktur i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)

