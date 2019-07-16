---
title: DEBUGREF_INFO_FLAGS | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 05a073b3663ff85fe3d68878999aaf1dfa9e0017
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198847"
---
# <a name="debugrefinfoflags"></a>DEBUGREF_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa, jakie informacje należy pobrać o obiektu odwołania debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
typedef DWORD DEBUGREF_INFO_FLAGS;  
```  
  
```csharp  
public enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 DEBUGREF_INFO_NAME  
 Inicjowanie bądź użyj `bstrName` pole w strukturze.  
  
 DEBUGREF_INFO_TYPE  
 Inicjowanie bądź użyj `bstrType` pole w strukturze.  
  
 DEBUGREF_INFO_VALUE  
 Inicjowanie bądź użyj `bstrValue` pole w strukturze.  
  
 DEBUGREF_INFO_ATTRIB  
 Inicjowanie bądź użyj `dwAttrib` pole w strukturze.  
  
 DEBUGREF_INFO_REFTYPE  
 Inicjowanie bądź użyj `dwRefType` pole w strukturze.  
  
 DEBUGREF_INFO_REF  
 Inicjowanie bądź użyj `pReference` pole w strukturze.  
  
 DEBUGREF_INFO_VALUE_AUTOEXPAND  
 Pole wartości powinien zawierać wartość rozwinięte automatycznie, jeśli są dostępne dla tego typu obiektu.  
  
 DEBUGREF_INFO_NONE  
 Wskazuje, że nie flagi są ustawione.  
  
 DEBUGREF_INFO_ALL  
 Określa maskę flag.  
  
## <a name="remarks"></a>Uwagi  
 Te flagi są przekazywane do [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) i [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) metod, aby określić które pola [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktury, które mają zostać zainicjowane.  
  
 Używany do `dwFields` członkiem `DEBUG_REFERENCE_INFO` struktury, aby wskazać, pola, które są używane i ważne, gdy zwracany jest struktura.  
  
 Te wartości mogą być łączone przy użyciu bitowego operatora `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
