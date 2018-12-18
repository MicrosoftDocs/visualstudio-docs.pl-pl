---
title: DEBUGPROP_INFO_FLAGS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 52c728c0ac31a64ebe462d2dddd798c085aea1bb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779336"
---
# <a name="debugpropinfoflags"></a>DEBUGPROP_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa, jakie informacje należy pobrać o obiekcie właściwości debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
typedef DWORD DEBUGPROP_INFO_FLAGS;  
```  
  
```csharp  
public enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 DEBUGPROP_INFO_FULLNAME  
 Inicjowanie bądź użyj `bstrFullName` pola.  
  
 DEBUGPROP_INFO_NAME  
 Inicjowanie bądź użyj `bstrName` pola.  
  
 DEBUGPROP_INFO_TYPE  
 Inicjowanie bądź użyj `bstrType` pola.  
  
 DEBUGPROP_INFO_VALUE  
 Inicjowanie bądź użyj `bstrValue` pola.  
  
 DEBUGPROP_INFO_ATTRIB  
 Inicjowanie bądź użyj `dwAttrib` pola.  
  
 DEBUGPROP_INFO_PROP,  
 Inicjowanie bądź użyj `pProperty` pola, które zawiera [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfejsu.  
  
 DEBUGPROP_INFO_VALUE_AUTOEXPAND  
 Oznacza, że wartość pola może zawierać wartość rozwinięte automatycznie, jeśli są dostępne dla tego typu obiektu.  
  
 DEBUGPROP_INFO_VALUE_NOFUNCEVAL  
 Przestarzałe.  
  
 DEBUGPROP_INFO_VALUE_RAW  
 Nie zwracają żadnych wartości beautified lub elementów członkowskich (czyli nie Formatuj wartości).  
  
 DEBUGPROP_INFO_VALUE_NO_TOSTRING  
 Nie zwraca żadnych specjalnych wartości syntetyzowany (na przykład nie należy wywoływać metody `ToString()` na obiekcie w celu utworzenia wartości).  
  
 DEBUGPROP_INFO_NONE  
 Określa, czy nie flagi są ustawione.  
  
 DEBUGPROP_INFO_STANDARD  
 Inicjowanie bądź użyj `dwAttrib`, `bstrName`, `bstrType`, i `bstrValue` pola.  
  
 DEBUGPROP_INFO_All  
 Określa maskę wszystkie flagi.  
  
## <a name="remarks"></a>Uwagi  
 Te wartości są przekazywane do [getpropertyinfo —](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md), i [enumproperties —](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) metod, aby określić pola, które mają zostać zainicjowane [ DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury.  
  
 Te wartości są używane również do `dwFields` członkiem `DEBUG_PROPERTY_INFO` struktury, aby wskazać, pola, które struktury są używane i ważne, gdy zwracany jest struktura.  
  
 Te wartości mogą być łączone przy użyciu bitowego operatora `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [Getpropertyinfo —](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [Enumproperties —](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)

