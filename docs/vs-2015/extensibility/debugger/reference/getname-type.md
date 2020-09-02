---
title: GETNAME_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 648f84b106dab7aa6e38cc3e45e59162a216a875
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160136"
---
# <a name="getname_type"></a>GETNAME_TYPE
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
 Określa pełną ścieżkę do dokumentu lub kontekstu.  
  
 GN_BASENAME  
 Określa nazwę pliku podstawowego zamiast pełnej ścieżki dokumentu lub kontekstu.  
  
 GN_MONIKERNAME  
 Określa unikatową nazwę dokumentu lub kontekstu w formie monikera.  
  
 GN_URL  
 Określa nazwę adresu URL dokumentu lub kontekstu.  
  
 GN_TITLE  
 Określa tytuł dokumentu (jeśli taki istnieje).  
  
 GN_STARTPAGEURL  
 Pobiera adres URL strony początkowej dla procesów.  
  
## <a name="remarks"></a>Uwagi  
 Te wartości są przesyłane jako parametry do metod [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName i](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) , aby określić, jakiego rodzaju nazwa ma zostać zwrócona.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName —](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName —](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
