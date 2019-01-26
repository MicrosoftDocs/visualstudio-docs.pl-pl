---
title: FIELD_MODIFIERS | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 282e7ec04f2cff029480701de10af2294a8185d6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54944504"
---
# <a name="fieldmodifiers"></a>FIELD_MODIFIERS
Określa Modyfikatory dla typu pola.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_FIELD_MODIFIERS {   
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
typedef DWORD FIELD_MODIFIERS;  
```  
  
```csharp  
public enum enum_FIELD_MODIFIERS {  
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 FIELD_MOD_ACCESS_TYPE  
 Wskazuje, że pole nie jest dostępny.  
  
 FIELD_MOD_ACCESS_PUBLIC  
 Wskazuje, że pole ma dostęp publiczny.  
  
 FIELD_MOD_ACCESS_PROTECTED  
 Wskazuje, czy pole zabezpieczył dostępu.  
  
 FIELD_MOD_ACCESS_PRIVATE  
 Wskazuje, czy pole ma dostęp do prywatnych.  
  
 FIELD_MOD_NOMODIFIERS  
 Wskazuje, że pole ma brak modyfikatorów.  
  
 FIELD_MOD_STATIC  
 Wskazuje, że pole jest statyczne.  
  
 FIELD_MOD_CONSTANT  
 Wskazuje, że pole jest stałą.  
  
 FIELD_MOD_TRANSIENT  
 Wskazuje, że pole jest przejściowy.  
  
 FIELD_MOD_VOLATILE  
 Wskazuje, że pole jest nietrwały.  
  
 FIELD_MOD_ABSTRACT  
 Wskazuje, że pole jest abstrakcyjna.  
  
 FIELD_MOD_NATIVE  
 Wskazuje, że pole jest native.  
  
 FIELD_MOD_SYNCHRONIZED  
 Wskazuje, że pole jest zsynchronizowany.  
  
 FIELD_MOD_VIRTUAL  
 Wskazuje, że pole jest wirtualny.  
  
 FIELD_MOD_INTERFACE  
 Wskazuje, że pole jest interfejs.  
  
 FIELD_MOD_FINAL  
 Wskazuje, że pole jest ostateczna.  
  
 FIELD_MOD_SENTINEL  
 Wskazuje, że pole jest wskaźnikowych.  
  
 FIELD_MOD_INNERCLASS  
 Wskazuje, że pole jest klasy wewnętrznej.  
  
 FIELD_TYPE_OPTIONAL  
 Wskazuje, że pole jest opcjonalne.  
  
 FIELD_MOD_BYREF  
 Wskazuje, że pole jest argument odwołania. Jest to szczególnie argumenty metody.  
  
 FIELD_MOD_HIDDEN  
 Wskazuje, czy pole musi być ukryty lub znajdujące się w innym kontekście; na przykład [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] statyczne zmienne lokalne.  
  
 FIELD_MOD_MARSHALASOBJECT  
 Wskazuje, że pole reprezentuje obiekt z `IUnknown` interfejsu.  
  
 FIELD_MOD_SPECIAL_NAME  
 Wskazuje, że pole ma specjalną nazwę, na przykład `.ctor` dla konstruktora ([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] tylko).  
  
 FIELD_MOD_HIDEBYSIG  
 Wskazuje, że pole ma `Overloads` zastosowano — słowo kluczowe ([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] tylko).  
  
 FIELD_MOD_WRITEONLY  
 Wskazuje, że pole jest tylko do zapisu. Ta wartość nie jest objęta `FIELD_MOD_ALL`, ponieważ tylko używać tych pól tylko do zapisu jest funkcja oceny. Użytkownik musi jawnie poprosić o `FIELD_MOD_WRITEONLY` pola.  
  
 FIELD_MOD_ACCESS_MASK  
 Określa maskę, aby uzyskać dostęp do pola.  
  
 FIELD_MOD_MASK  
 Określa maskę modyfikatorów pól.  
  
## <a name="remarks"></a>Uwagi  
 Używany do `dwModifiers` członkiem [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struktury.  
  
 Te wartości również są przekazywane do [enumfields —](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) metody, aby filtrować pod kątem konkretnych pól.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)