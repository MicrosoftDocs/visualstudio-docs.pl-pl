---
title: CONTEXT_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4e8c1b438cd2fa2721e81f055695e5836c26d12
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179942"
---
# <a name="context_info"></a>CONTEXT_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta struktura opisuje kontekst pamięci lub kontekst kodu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 Kombinacja flag z wyliczenia [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) , która określa, które pola są wypełniane<strong>.</strong>  
  
 bstrModuleUrl  
 Nazwa modułu, w którym znajduje się kontekst.  
  
 bstrFunction  
 Nazwa funkcji, w której znajduje się kontekst.  
  
 posFunctionOffset  
 Struktura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , która identyfikuje przesunięcie wiersza i kolumny funkcji skojarzonej z kontekstem kodu.  
  
 bstrAddress  
 Adres w kodzie, w którym znajduje się dany kontekst.  
  
 bstrAddressOffset  
 Przesunięcie adresu w kodzie, w którym znajduje się dany kontekst.  
  
 bstrAddressAbsolute  
 Adres bezwzględny w pamięci, w której znajduje się dany kontekst.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest zwracana z wywołania metody [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) .  
  
 Typowym zastosowaniem tej struktury jest obsługa okna debugowania **pamięci** .  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
