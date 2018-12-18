---
title: FIELD_INFO_FIELDS | Dokumentacja firmy Microsoft
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
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ceebad12604fc788cabeef770052409ffb7bb2b0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761618"
---
# <a name="fieldinfofields"></a>FIELD_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa, jakie informacje należy pobrać o [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_FIELD_INFO_FIELDS {   
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
typedef DWORD FIELD_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_FIELD_INFO_FIELDS {  
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 FIF_FULLNAME  
 Inicjowanie bądź użyj `bstrFullName` pole [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struktury.  
  
 FIF_NAME  
 Inicjowanie bądź użyj `bstrName` pole `FIELD_INFO` struktury.  
  
 FIF_TYPE  
 Inicjowanie bądź użyj `bstrType` pole `FIELD_INFO` struktury.  
  
 FIF_MODIFIERS  
 Inicjowanie bądź użyj `bstrModifiers` pole `FIELD_INFO` struktury.  
  
## <a name="remarks"></a>Uwagi  
 Te wartości również są przekazywane jako argument do [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) metodę, aby określić które pola [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struktury, które mają zostać zainicjowane.  
  
 Te wartości są również używane w `dwFields` członkiem `FIELD_INFO` struktury, aby wskazać, które pola są używane i prawidłowy.  
  
 Te flagi mogą być łączone przy użyciu bitowego operatora `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)

