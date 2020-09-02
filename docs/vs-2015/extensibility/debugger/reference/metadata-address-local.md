---
title: METADATA_ADDRESS_LOCAL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5928f6092adc62dc8f0eb075f20367c056fc50c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547172"
---
# <a name="metadata_address_local"></a>METADATA_ADDRESS_LOCAL
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta struktura reprezentuje adres zmiennej lokalnej w zakresie (zazwyczaj jest to funkcja lub metoda).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_LOCAL {  
   _mdToken  tokMethod;  
   IUnknown* pLocal;  
   DWORD     dwIndex;  
} METADATA_ADDRESS_LOCAL;  
```  
  
```csharp  
public struct METADATA_ADDRESS_LOCAL {  
   public int    tokMethod;  
   public object pLocal;  
   public uint   dwIndex;  
}  
```  
  
## <a name="terms"></a>Terminologia  
 tokMethod  
 Identyfikator metody lub funkcji, do której należy zmienna lokalna.  
  
 [C++] `_mdToken` jest `typedef` dla 32-bitowej `int` .  
  
 pLocal  
 Token, którego adres reprezentuje Ta struktura.  
  
 dwIndex  
 Może to być indeks tej zmiennej lokalnej w metodzie lub funkcji albo inne wartości (specyficzne dla języka).  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest częścią Unii w strukturze [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) , gdy `dwKind` pole `DEBUG_ADDRESS_UNION` struktury jest ustawione na `ADDRESS_KIND_LOCAL` (wartość z wyliczenia [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) ).  
  
 `Warning:` [Tylko C++]  Jeśli `pLocal` wartość nie jest równa null, należy wywołać `Release` wskaźnik tokenu ( `addr` jest polem w strukturze [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) ):  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
