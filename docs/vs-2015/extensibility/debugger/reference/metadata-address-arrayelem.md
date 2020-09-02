---
title: METADATA_ADDRESS_ARRAYELEM | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_ARRAYELEM
helpviewer_keywords:
- METADATA_ADDRESS_ARRAYELEM structure
ms.assetid: 24321be5-7c17-4038-82a1-c20a2b68ff3c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f558dc11f4f338cd370442bf9feaed419ce29411
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547601"
---
# <a name="metadata_address_arrayelem"></a>METADATA_ADDRESS_ARRAYELEM
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta struktura reprezentuje element tablicy w tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_ARRAYELEM {  
   _mdToken tokMethod;  
   DWORD    dwIndex;  
} METADATA_ADDRESS_ARRAYELEM;  
```  
  
```csharp  
public struct METADATA_ADDRESS_ARRAYELEM {  
   public int  tokMethod;  
   public uint dwIndex;  
}  
```  
  
## <a name="terms"></a>Terminologia  
 tokMethod  
 Identyfikator tablicy, do której należy ten element.  
  
 [C++] `_mdToken` jest `typedef` dla 32-bitowej `int` .  
  
 dwIndex  
 Indeks tego elementu w tablicy.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest częścią Unii w strukturze [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) , gdy `dwKind` pole `DEBUG_ADDRESS_UNION` struktury jest ustawione na `ADDRESS_KIND_ARRAYELEM` (wartość z wyliczenia [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) ).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
