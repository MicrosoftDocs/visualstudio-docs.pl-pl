---
title: MACHINE_INFO_FIELDS | Dokumentacja firmy Microsoft
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
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: efedc30b1e58388438127776a69b41ebb7b480ca
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51763666"
---
# <a name="machineinfofields"></a>MACHINE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa, jakiego rodzaju informacje należy pobrać dla określonego komputera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
typedef DWORD MACHINE_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 MCIF_NAME  
 Inicjowanie bądź użyj `bstrName` pole w strukturze.  
  
 MCIF_FLAGS  
 Inicjowanie bądź użyj `Flags` pole w strukturze.  
  
 MIF_ALL  
 Inicjowanie bądź użyj wszystkie pola w strukturze.  
  
## <a name="remarks"></a>Uwagi  
 Te wartości są przekazywane do [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) metodę, aby wskazać, którzy członkowie [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) struktury, które mają zostać zainicjowane.  
  
 Używany również w `Fields` członkiem `MACHINE_INFO` struktury, aby wskazać, które pola są używane i prawidłowy.  
  
 Te flagi mogą być łączone przy użyciu bitowego operatora `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)

