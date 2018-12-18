---
title: BPERESI_FIELDS | Dokumentacja firmy Microsoft
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
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d6e21b5c75572ef320630dcea7a35f3cfc8a5d00
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51744097"
---
# <a name="bperesifields"></a>BPERESI_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa informacje, które mają zostać pobrane dotyczących rozwiązania nie powiodło się punktu przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD BPERESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 PERESI_BPRESLOCATION  
 Inicjowanie bądź użyj `bpResLocation` pola (lokalizacji punktu przerwania rozdzielczość) [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) struktury.  
  
 BPERESI_PROGRAM  
 Inicjowanie bądź użyj `pProgram` pole `BP_ERROR_RESOLUTION_INFO` struktury.  
  
 BPERESI_THREAD  
 Inicjowanie bądź użyj `pThread` pole `BP_ERROR_RESOLUTION_INFO` struktury.  
  
 BPERESI_MESSAGE  
 Inicjowanie bądź użyj `bstrMessage` pole `BP_ERROR_RESOLUTION_INFO` struktury.  
  
 BPERESI_TYPE  
 Inicjowanie bądź użyj `dwType` pola (typ punktu przerwania) `BP_ERROR_RESOLUTION_INFO` struktury.  
  
 BPERESI_ALLFIELDS  
 Inicjowanie bądź Użyj wszystkich pól `BP_ERROR_RESOLUTION_INFO` struktury.  
  
## <a name="remarks"></a>Uwagi  
 Przekazany jako parametr do [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) metodę, aby wskazać, które pola [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) struktury, które mają zostać zainicjowane.  
  
 Te wartości są również używane do wskazania, które pola w `BP_ERROR_RESOLUTION_INFO` struktury są używane i ważne, gdy tej struktury jest zwracany.  
  
 Te wartości mogą być łączone przy użyciu bitowego operatora `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)

