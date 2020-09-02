---
title: UNMANAGED_ADDRESS_PHYSICAL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_PHYSICAL
helpviewer_keywords:
- UNMANAGED_ADDRESS_PHYSICAL structure
ms.assetid: fed09686-caa6-4efc-851e-a0432019e9d0
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f8eccadbb2ae29f684c8c760ab34dae59c79ac7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204767"
---
# <a name="unmanaged_address_physical"></a>UNMANAGED_ADDRESS_PHYSICAL
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta struktura reprezentuje adres fizyczny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _tagUNMANAGED_ADDRESS_PHYSICAL {  
   ULONGLONG offset;  
} UNMANAGED_ADDRESS_PHYSICAL;  
```  
  
```csharp  
public struct UNMANAGED_ADDRESS_PHYSICAL {  
   public ulong offset;  
}  
```  
  
## <a name="terms"></a>Terminologia  
 przesunięcie  
 Przesunięcie 64-bitowe do fizycznej przestrzeni adresowej.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest częścią Unii w strukturze [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) , gdy `dwKind` pole `DEBUG_ADDRESS_UNION` struktury jest ustawione na `ADDRESS_KIND_UNMANAGED_PHYSICAL` (wartość z wyliczenia [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) ).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
