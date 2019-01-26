---
title: DISASSEMBLY_STREAM_FIELDS | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b293830dd4ba454e131f016d82d5b5cdfcf78371
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54985123"
---
# <a name="disassemblystreamfields"></a>DISASSEMBLY_STREAM_FIELDS
Określa, jakie informacje należy pobrać o polu dezasemblacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
typedef DWORD DISASSEMBLY_STREAM_FIELDS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 DSF_ADDRESS  
 Inicjowanie bądź użyj `bstrAddress` pola.  
  
 DSF_ADDRESSOFFSET  
 Inicjowanie bądź użyj `bstrAddressOffset` pola.  
  
 DSF_CODEBYTES  
 Inicjowanie bądź użyj `bstrCodeBytes` pola.  
  
 DSF_OPCODE  
 Inicjowanie bądź użyj `bstrOpCode` pola.  
  
 DSF_OPERANDS  
 Inicjowanie bądź użyj `bstrOperands` pola.  
  
 DSF_SYMBOL  
 Inicjowanie bądź użyj `bstrSymbol` pola.  
  
 DSF_CODELOCATIONID  
 Inicjowanie bądź użyj `uCodeLocationId` pola.  
  
 DSF_POSITION  
 Inicjowanie bądź użyj `posBeg` i `posEnd` pola.  
  
 DSF_DOCUMENTURL  
 Inicjowanie bądź użyj `bstrDocumentUrl` pola.  
  
 DSF_BYTEOFFSET  
 Inicjowanie bądź użyj `dwByteOffset` pola.  
  
 DSF_FLAGS  
 Inicjowanie bądź użyj `dwFlags` ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) pola.  
  
 DSF_OPERANDS_SYMBOLS  
 Dołącz nazwy symbolu w `bstrOperands` pola.  
  
 DSF_ALL  
 Określa wszystkie pola dla strumienia dezasemblacji.  
  
## <a name="remarks"></a>Uwagi  
 Przekazany jako parametr do [odczytu](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) metodę, aby wskazać, które pola [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struktury, które mają zostać zainicjowane.  
  
 Używany do `dwFields` członkiem `DisassemblyData` struktury, aby wskazać, pola, które są używane i ważne, gdy zwracany jest struktura.  
  
 Te wartości mogą być łączone przy użyciu bitowego operatora `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Odczyt](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)