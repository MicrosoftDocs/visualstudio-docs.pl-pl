---
title: DISASSEMBLY_STREAM_SCOPE | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0132aad5ad6e37e7bb811693afde7ebfe80b272d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198834"
---
# <a name="disassemblystreamscope"></a>DISASSEMBLY_STREAM_SCOPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa zakres strumienia dezasemblacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
typedef DWORD DISASSEMBLY_STREAM_SCOPE;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 DSS_HUGE  
 Określa, że deasemblowanie kontekst kodu będzie generować więcej danych wyjściowych niż klient będzie zazwyczaj ma zostać pobrane w jednym wywołaniu.  
  
 DSS_FUNCTION  
 Określa funkcję zawarte w kontekście kod powinien zostać zdezasemblowany. Określa, że strumienia dezasemblacji reprezentuje funkcji, gdy zwracany przez [getscope —](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) metody.  
  
 DSS_MODULE  
 Po zwróceniu przez `IDebugDisassemblyStream2::GetScope` metody Określa, że strumień dezasemblacji reprezentuje moduł.  
  
 DSS_ALL  
 Określa dezasemblację dla całą przestrzenią adresową.  
  
## <a name="remarks"></a>Uwagi  
 Przekazywany jako argument do [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) metody i zwrócone przez [getscope —](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) metody.  
  
 Te wartości mogą być łączone przy użyciu bitowego operatora `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
