---
title: DISASSEMBLY_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d48fcf9dd941194b56e2c794ad7f5673f8e58421
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159314"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa flagi do odzbiór.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
typedef DWORD DISASSEMBLY_FLAGS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 DF_DOCUMENTCHANGE  
 Wskazuje, że ta instrukcja znajduje się w innym dokumencie niż poprzedni.  
  
 DF_DISABLED  
 Wskazuje, że ta instrukcja nie zostanie wykonana.  
  
 DF_INSTRUCTION_ACTIVE  
 Wskazuje, że ta instrukcja jest jedną z następnych instrukcji do wykonania (może być więcej niż jeden).  
  
 DF_DATA  
 Wskazuje, że ta instrukcja jest naprawdę danymi (nie kod).  
  
 DF_HASSOURCE  
 Wskazuje, że ta instrukcja ma źródło. Niektóre instrukcje, takie jak profilowanie lub kod odzyskiwania pamięci, nie mają odpowiedniego źródła.  
  
 DF_DOCUMENT_CHECKSUM  
 Wskazuje, że `bstrDocumentUrl` pole zawiera dane sum kontrolnych po adresie URL dokumentu. Zapoznaj się z sekcją uwagi struktury [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) , w jaki sposób są przechowywane dane sum kontrolnych.  
  
## <a name="remarks"></a>Uwagi  
 Używane jako `dwFlags` element członkowski struktury [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) .  
  
 Flagi te mogą być połączone z bitową `OR` .  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
