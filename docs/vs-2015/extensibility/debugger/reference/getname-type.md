---
title: GETNAME_TYPE | Dokumentacja firmy Microsoft
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
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8edbf690851d820adc2fc8fdb61044aa9c9d46e2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725027"
---
# <a name="getnametype"></a>GETNAME_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa typ nazwy plików do pobrania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
typedef DWORD GETNAME_TYPE;  
```  
  
```csharp  
public enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 GN_NAME  
 Określa przyjazną nazwę dokumentu lub kontekstu.  
  
 GN_FILENAME  
 Określa pełną ścieżkę dokumentu lub kontekstu.  
  
 GN_BASENAME  
 Określa nazwę pliku podstawowego zamiast pełnej ścieżki dokumentu lub kontekstu.  
  
 GN_MONIKERNAME  
 Określa unikatową nazwę dokumentu lub kontekstu w postaci krótka.  
  
 GN_URL  
 Określa nazwę adresu URL dokumentu lub kontekstu.  
  
 GN_TITLE  
 Określa tytuł dokumentu, jeśli taka istnieje.  
  
 GN_STARTPAGEURL  
 Pobiera początkowy adres URL strony dla procesów.  
  
## <a name="remarks"></a>Uwagi  
 Te wartości są przekazywane jako parametry [getname —](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [getname —](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md), i [getname —](../../../extensibility/debugger/reference/idebugprocess2-getname.md) metody, aby określić, jakiego rodzaju nazwy do zwrócenia.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Getname —](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [Getname —](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)

