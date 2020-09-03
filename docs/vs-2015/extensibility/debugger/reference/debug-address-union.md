---
title: DEBUG_ADDRESS_UNION | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b500bcb49e9072c3d31ea5ac3f77bda606c23b78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179179"
---
# <a name="debug_address_union"></a>DEBUG_ADDRESS_UNION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Opisuje różne rodzaje adresów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS_UNION {  
   ADDRESS_KIND dwKind;  
   union {  
      NATIVE_ADDRESS                  addrNative;  
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;  
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;  
      METADATA_ADDRESS_METHOD         addrMethod;  
      METADATA_ADDRESS_FIELD          addrField;  
      METADATA_ADDRESS_LOCAL          addrLocal;  
      METADATA_ADDRESS_PARAM          addrParam;  
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;  
      METADATA_ADDRESS_RETVAL         addrRetVal;  
      DWORD                           unused;  
   } addr;  
} DEBUG_ADDRESS_UNION;  
```  
  
```csharp  
public struct DEBUG_ADDRESS_UNION {  
   public ADDRESS_KIND dwKind;  
   public IntPtr       unionmember;  
}  
```  
  
## <a name="terms"></a>Terminologia  
 dwKind  
 Wartość z wyliczenia [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) , określająca sposób interpretacji związku.  
  
 addr. addrNative  
 [Tylko C++] Zawiera strukturę [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) , jeśli `dwKind` = ADDRESS_KIND_NATIVE.  
  
 addr. addrThisRel  
 [Tylko C++] Zawiera strukturę[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) , jeśli `dwKind` = ADDRESS_KIND_UNMANAGED_THIS_RELATIVE.  
  
 addr. addUPhysical  
 [Tylko C++] Zawiera strukturę[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) , jeśli `dwKind` = ADDRESS_KIND_UNMANAGED_PHYSICAL.  
  
 addr. addrMethod  
 [Tylko C++] Zawiera strukturę[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) , jeśli `dwKind` = ADDRESS_KIND_METHOD.  
  
 addr. addrField  
 [Tylko C++] Zawiera strukturę[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) , jeśli `dwKind` = ADDRESS_KIND_FIELD.  
  
 addr. addrLocal  
 [Tylko C++] Zawiera strukturę[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) , jeśli `dwKind` = ADDRESS_KIND_LOCAL.  
  
 addr. addrParam  
 [Tylko C++] Zawiera strukturę[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) , jeśli `dwKind` = ADDRESS_KIND_PARAM.  
  
 addr. addrArrayElem  
 [Tylko C++] Zawiera strukturę[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) , jeśli `dwKind` = ADDRESS_KIND_ARRAYELEM.  
  
 addr. addrRetVal  
 [Tylko C++] Zawiera strukturę[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) , jeśli `dwKind` = ADDRESS_KIND_RETVAL.  
  
 ADR. nieużywane  
 Uzupełnienie [tylko C++].  
  
 adresowe  
 [Tylko C++] Nazwa Unii.  
  
 unionmember  
 [Tylko w C#] Ta wartość musi być organizowana do odpowiedniego typu struktury na podstawie `dwKind` . Zobacz uwagi dotyczące skojarzenia między `dwKind` i interpretacji związku.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest częścią struktury [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) i reprezentuje jedną z różnych rodzajów adresów ( `DEBUG_ADDRESS` Struktura jest wypełniana przez wywołanie metody [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) ).  
  
 [Tylko w C#] W poniższej tabeli pokazano, jak interpretować `unionmember` składową dla każdego rodzaju adresu. W przykładzie pokazano, jak to zrobić w przypadku jednego rodzaju adresu.  
  
|`dwKind`|`unionmember` interpretowane jako|  
|--------------|----------------------------------|  
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|  
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|  
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|  
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|  
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|  
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|  
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|  
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|  
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|  
  
## <a name="example"></a>Przykład  
 Ten przykład pokazuje sposób interpretowania jednego rodzaju adresu ( `METADATA_ADDRESS_ARRAYELEM` ) `DEBUG_ADDRESS_UNION` struktury w języku C#. Pozostałe elementy można interpretować w taki sam sposób.  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(DEBUG_ADDRESS_UNION dau)  
        {  
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)  
            {  
                 METADATA_ADDRESS_ARRAYELEM arrayElem =  
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,  
                                 typeof(METADATA_ADDRESS_ARRAYELEM));  
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
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
