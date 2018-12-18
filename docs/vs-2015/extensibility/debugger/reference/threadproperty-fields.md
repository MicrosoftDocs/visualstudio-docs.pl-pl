---
title: THREADPROPERTY_FIELDS | Dokumentacja firmy Microsoft
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
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1bcc299a9179a4e0aff5e405569690a9ce8db0ba
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774110"
---
# <a name="threadpropertyfields"></a>THREADPROPERTY_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa, jakie informacje o wątku do pobrania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD THREADPROPERTY_FIELDS;  
```  
  
```csharp  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 TPF_ID  
 Inicjowanie bądź użyj `dwThreadId` pole [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) struktury.  
  
 TPF_SUSPENDCOUNT  
 Inicjowanie bądź użyj `dwSuspendCount` pole `THREADPROPERTIE`Struktura.  
  
 TPF_STATE  
 Inicjowanie bądź użyj `dwThreadState` pole `THREADPROPERTIE`Struktura.  
  
 TPF_PRIORITY  
 Inicjowanie bądź użyj `bstrPriority` pole `THREADPROPERTIE`Struktura.  
  
 TPF_NAME  
 Inicjowanie bądź użyj `bstrName` pole `THREADPROPERTIE`Struktura.  
  
 TPF_LOCATION  
 Inicjowanie bądź użyj `bstrLocation` pole `THREADPROPERTIE`Struktura.  
  
 TPF_ALLFIELDS  
 Określa wszystkie pola.  
  
## <a name="remarks"></a>Uwagi  
 Te wartości są przekazywane jako argument do [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) metodę, aby wskazać, które pola [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) struktury, które mają zostać zainicjowane.  
  
 Te wartości są również używane w `dwFields` członkiem `THREADPROPERTIES` struktury, aby wskazać, które pola są używane i prawidłowy.  
  
 Te flagi mogą być łączone przy użyciu bitowego operatora `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)

