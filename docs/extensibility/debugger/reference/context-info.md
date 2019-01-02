---
title: CONTEXT_INFO | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a88a1a3c2d07387399a1701b6645d300bce8993d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53927249"
---
# <a name="contextinfo"></a>CONTEXT_INFO
Ta struktura zawiera opis kontekście pamięci lub kontekst kodu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _tagCONTEXT_INFO {   
   CONTEXT_INFO_FIELDS dwFields;  
   BSTR                bstrModuleUrl;  
   BSTR                bstrFunction;  
   TEXT_POSITION       posFunctionOffset;  
   BSTR                bstrAddress;  
   BSTR                bstrAddressOffset;  
   BSTR                bstrAddressAbsolute;  
} CONTEXT_INFO;  
```  
  
```csharp  
public struct CONTEXT_INFO {  
   public uint          dwFields;  
   public string        bstrModuleUrl;  
   public string        bstrFunction;  
   public TEXT_POSITION posFunctionOffset;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrAddressAbsolute;  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 dwFields  
 Kombinacja flag z on [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) wyliczenia, która określa pola, które są wypełnione<strong>.</strong>  
  
 bstrModuleUrl  
 Nazwa modułu, w którym znajduje się kontekst.  
  
 bstrFunction  
 Nazwa funkcji, w którym znajduje się kontekst.  
  
 posFunctionOffset  
 A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struktura, która identyfikuje przesunięcie wiersza i kolumny funkcji skojarzonego z kontekstem kodu.  
  
 bstrAddress  
 Adres w kodzie, w którym znajduje się dany kontekst.  
  
 bstrAddressOffset  
 Przesunięcie adresu w kodzie, w którym znajduje się dany kontekst.  
  
 bstrAddressAbsolute  
 Bezwzględny adres w pamięci, w którym znajduje się dany kontekst.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest zwracany z wywołania [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) metody.  
  
 Typowym zastosowaniem dla tej struktury jest wspierających **pamięci** okna debugowania.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktur i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)