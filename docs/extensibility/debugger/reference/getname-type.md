---
title: GETNAME_TYPE | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6443c4c359562cc6b04ab413c31fb61441511ef4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916566"
---
# <a name="getnametype"></a>GETNAME_TYPE
Określa typ nazwy plików do pobrania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Getname —](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [Getname —](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)