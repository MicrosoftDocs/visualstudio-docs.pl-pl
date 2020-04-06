---
title: DBG_ATTRIB_FLAGS | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c8b3f52eff80c187d3c43b87cea804ace483169
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737559"
---
# <a name="dbg_attrib_flags"></a>DBG_ATTRIB_FLAGS
Opisuje różne atrybuty dla [interfejsu IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) lub [IDebugReference2.](../../../extensibility/debugger/reference/idebugreference2.md) Członek [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury.

## <a name="syntax"></a>Składnia

```cpp
#define DBG_ATTRIB_NONE                 0x0000000000000000,
#define DBG_ATTRIB_ALL                  0x00000000ffffffff,

// Attributes about the object itself

#define DBG_ATTRIB_OBJ_IS_EXPANDABLE    0x0000000000000001,
#define DBG_ATTRIB_OBJ_HAS_ID           0x0000000000000002,
#define DBG_ATTRIB_OBJ_CAN_HAVE_ID      0x0000000000000004,

// Attributes about the value of the object

#define DBG_ATTRIB_VALUE_READONLY       0x0000000000000010,
#define DBG_ATTRIB_VALUE_ERROR          0x0000000000000020,
#define DBG_ATTRIB_VALUE_SIDE_EFFECT    0x0000000000000040,
#define DBG_ATTRIB_OVERLOADED_CONTAINER 0x0000000000000080,
#define DBG_ATTRIB_VALUE_BOOLEAN        0x0000000000000100,
#define DBG_ATTRIB_VALUE_BOOLEAN_TRUE   0x0000000000000200,
#define DBG_ATTRIB_VALUE_INVALID        0x0000000000000400,
#define DBG_ATTRIB_VALUE_NAT            0x0000000000000800,
#define DBG_ATTRIB_VALUE_AUTOEXPANDED   0x0000000000001000,
#define DBG_ATTRIB_VALUE_TIMEOUT        0x0000000000002000,
#define DBG_ATTRIB_VALUE_RAW_STRING     0x0000000000004000,
#define DBG_ATTRIB_VALUE_CUSTOM_VIEWER  0x0000000000008000,

// Attributes about field access types for the object

#define DBG_ATTRIB_ACCESS_NONE          0x0000000000010000,
#define DBG_ATTRIB_ACCESS_PUBLIC        0x0000000000020000,
#define DBG_ATTRIB_ACCESS_PRIVATE       0x0000000000040000,
#define DBG_ATTRIB_ACCESS_PROTECTED     0x0000000000080000,
#define DBG_ATTRIB_ACCESS_FINAL         0x0000000000100000,
#define DBG_ATTRIB_ACCESS_ALL           0x00000000001f0000,

// Attributes for the storage types of the object

#define DBG_ATTRIB_STORAGE_NONE         0x0000000001000000,
#define DBG_ATTRIB_STORAGE_GLOBAL       0x0000000002000000,
#define DBG_ATTRIB_STORAGE_STATIC       0x0000000004000000,
#define DBG_ATTRIB_STORAGE_REGISTER     0x0000000008000000,
#define DBG_ATTRIB_STORAGE_ALL          0x000000000f000000,

// Attributes for the type modifiers on the object

#define DBG_ATTRIB_TYPE_NONE            0x0000000100000000,
#define DBG_ATTRIB_TYPE_VIRTUAL         0x0000000200000000,
#define DBG_ATTRIB_TYPE_CONSTANT        0x0000000400000000,
#define DBG_ATTRIB_TYPE_SYNCHRONIZED    0x0000000800000000,
#define DBG_ATTRIB_TYPE_VOLATILE        0x0000001000000000,
#define DBG_ATTRIB_TYPE_ALL             0x0000001f00000000,

// Attributes that describe the type of object

#define DBG_ATTRIB_DATA                 0x0000010000000000,
#define DBG_ATTRIB_METHOD               0x0000020000000000,
#define DBG_ATTRIB_PROPERTY             0x0000040000000000,
#define DBG_ATTRIB_CLASS                0x0000080000000000,
#define DBG_ATTRIB_BASECLASS            0x0000100000000000,
#define DBG_ATTRIB_INTERFACE            0x0000200000000000,
#define DBG_ATTRIB_INNERCLASS           0x0000400000000000,
#define DBG_ATTRIB_MOSTDERIVED          0x0000800000000000,
#define DBG_ATTRIB_CHILD_ALL            0x0000ff0000000000,

// Miscellaneous attributes

#define DBG_ATTRIB_MULTI_CUSTOM_VIEWERS 0x0001000000000000

typedef UINT64 DBG_ATTRIB_FLAGS;
```

```csharp
public const int DBG_ATTRIB_NONE                 = 0x0000000000000000,
public const int DBG_ATTRIB_ALL                  = 0x00000000ffffffff,

// Attributes about the object itself

public const int DBG_ATTRIB_OBJ_IS_EXPANDABLE    = 0x0000000000000001,
public const int DBG_ATTRIB_OBJ_HAS_ID           = 0x0000000000000002,
public const int DBG_ATTRIB_OBJ_CAN_HAVE_ID      = 0x0000000000000004,

// Attributes about the value of the object

public const int DBG_ATTRIB_VALUE_READONLY       = 0x0000000000000010,
public const int DBG_ATTRIB_VALUE_ERROR          = 0x0000000000000020,
public const int DBG_ATTRIB_VALUE_SIDE_EFFECT    = 0x0000000000000040,
public const int DBG_ATTRIB_OVERLOADED_CONTAINER = 0x0000000000000080,
public const int DBG_ATTRIB_VALUE_BOOLEAN        = 0x0000000000000100,
public const int DBG_ATTRIB_VALUE_BOOLEAN_TRUE   = 0x0000000000000200,
public const int DBG_ATTRIB_VALUE_INVALID        = 0x0000000000000400,
public const int DBG_ATTRIB_VALUE_NAT            = 0x0000000000000800,
public const int DBG_ATTRIB_VALUE_AUTOEXPANDED   = 0x0000000000001000,
public const int DBG_ATTRIB_VALUE_TIMEOUT        = 0x0000000000002000,
public const int DBG_ATTRIB_VALUE_RAW_STRING     = 0x0000000000004000,
public const int DBG_ATTRIB_VALUE_CUSTOM_VIEWER  = 0x0000000000008000,

// Attributes about field access types for the object

public const int DBG_ATTRIB_ACCESS_NONE          = 0x0000000000010000,
public const int DBG_ATTRIB_ACCESS_PUBLIC        = 0x0000000000020000,
public const int DBG_ATTRIB_ACCESS_PRIVATE       = 0x0000000000040000,
public const int DBG_ATTRIB_ACCESS_PROTECTED     = 0x0000000000080000,
public const int DBG_ATTRIB_ACCESS_FINAL         = 0x0000000000100000,
public const int DBG_ATTRIB_ACCESS_ALL           = 0x00000000001f0000,

// Attributes for the storage types of the object

public const int DBG_ATTRIB_STORAGE_NONE         = 0x0000000001000000,
public const int DBG_ATTRIB_STORAGE_GLOBAL       = 0x0000000002000000,
public const int DBG_ATTRIB_STORAGE_STATIC       = 0x0000000004000000,
public const int DBG_ATTRIB_STORAGE_REGISTER     = 0x0000000008000000,
public const int DBG_ATTRIB_STORAGE_ALL          = 0x000000000f000000,

// Attributes for the type modifiers on the object

public const int DBG_ATTRIB_TYPE_NONE            = 0x0000000100000000,
public const int DBG_ATTRIB_TYPE_VIRTUAL         = 0x0000000200000000,
public const int DBG_ATTRIB_TYPE_CONSTANT        = 0x0000000400000000,
public const int DBG_ATTRIB_TYPE_SYNCHRONIZED    = 0x0000000800000000,
public const int DBG_ATTRIB_TYPE_VOLATILE        = 0x0000001000000000,
public const int DBG_ATTRIB_TYPE_ALL             = 0x0000001f00000000,

// Attributes that describe the type of object

public const int DBG_ATTRIB_DATA                 = 0x0000010000000000,
public const int DBG_ATTRIB_METHOD               = 0x0000020000000000,
public const int DBG_ATTRIB_PROPERTY             = 0x0000040000000000,
public const int DBG_ATTRIB_CLASS                = 0x0000080000000000,
public const int DBG_ATTRIB_BASECLASS            = 0x0000100000000000,
public const int DBG_ATTRIB_INTERFACE            = 0x0000200000000000,
public const int DBG_ATTRIB_INNERCLASS           = 0x0000400000000000,
public const int DBG_ATTRIB_MOSTDERIVED          = 0x0000800000000000,
public const int DBG_ATTRIB_CHILD_ALL            = 0x0000ff0000000000,

// Miscellaneous attributes

public const int DBG_ATTRIB_MULTI_CUSTOM_VIEWERS = 0x0001000000000000
```

## <a name="members"></a>Elementy członkowskie
 `DBG_ATTRIB_NONE`\
 Wskazuje brak atrybutów.

 `DBG_ATTRIB_ALL`\
 Wskazuje wszystkie atrybuty.

 `DBG_ATTRIB_OBJ_IS_EXPANDABLE`\
 Wskazuje, że odwołanie lub właściwość ma dzieci.

 `DBG_ATTRIB_OBJ_HAS_ID`\
 Wskazuje, że identyfikator tego obiektu został utworzony.

 `DBG_ATTRIB_OBJ_CAN_HAVE_ID`\
 Wskazuje, że można utworzyć identyfikator tego obiektu.

 `DBG_ATTRIB_VALUE_READONLY`\
 Wskazuje, że wartość jest tylko do odczytu.

 `DBG_ATTRIB_VALUE_ERROR`\
 Wskazuje, że wartość jest błędem.

 `DBG_ATTRIB_VALUE_SIDE_EFFECT`\
 Wskazuje, że ocena miała działanie niepożądane.

 `DBG_ATTRIB_OVERLOADED_CONTAINER`\
 Wskazuje, że ta właściwość jest naprawdę kontener przeciążeń.

 `DBG_ATTRIB_VALUE_BOOLEAN`\
 Wskazuje, że wartość `DEBUG_PROPERTY_INFO::bstrValue` w jest logiczna.

 `DBG_ATTRIB_VALUE_BOOLEAN_TRUE`\
 Wskazuje, że wartość `DEBUG_PROPERTY_INFO::bstrValue` w jest `TRUE`logiczna i .

 `DBG_ATTRIB_VALUE_INVALID`\
 Wskazuje, że wartość `DEBUG_PROPERTY_INFO::bstrValue` w jest nieprawidłowa.

 `DBG_ATTRIB_VALUE_NAT`\
 Wskazuje, że wartość `DEBUG_PROPERTY_INFO::bstrValue` w *"nie*jest rzeczą " (NAT). Translator informacji opisuje flagę rejestru w 64-bitowych procesorach Intel, która wskazuje odroczone wyjątki spekulacyjne.

 `DBG_ATTRIB_VALUE_AUTOEXPANDED`\
 Wskazuje, że wartość `DEBUG_PROPERTY_INFO::bstrValue` w prawdopodobnie został automatycznie rozwinięty.

 `DBG_ATTRIB_VALUE_TIMEOUT`\
 Wskazuje, że ocena ma limit czasu.

 `DBG_ATTRIB_VALUE_RAW_STRING`\
 Wskazuje, że wartość `DEBUG_PROPERTY_INFO::bstrValue` w może być reprezentowana przez ciąg nieprzetworzony.

 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER`\
 Wskazuje, że ta właściwość ma co najmniej jedną niestandardową przeglądarkę skojarzoną z nią.

 `DBG_ATTRIB_ACCESS_NONE`\
 Wskazuje obiekt, który nie `public` `private`ma `protected` , ani nie wpisz dostępu.

 `DBG_ATTRIB_ACCESS_PUBLIC`\
 Wskazuje obiekt, który ma dostęp publiczny.

 `DBG_ATTRIB_ACCESS_PRIVATE`\
 Wskazuje obiekt, który ma dostęp prywatny.

 `DBG_ATTRIB_ACCESS_PROTECTED`\
 Wskazuje obiekt, który ma chroniony dostęp.

 `DBG_ATTRIB_ACCESS_FINAL`\
 Wskazuje obiekt, który ma dostęp końcowy.

 `DBG_ATTRIB_ACCESS_ALL`\
 Maska, aby wyodrębnić atrybuty dostępu z `DBG_ATTRIB_FLAGS`programu .

 `DBG_ATTRIB_STORAGE_NONE`\
 Wskazuje, że nie określono typu magazynu.

 `DBG_ATTRIB_STORAGE_GLOBAL`\
 Wskazuje magazyn globalny.

 `DBG_ATTRIB_STORAGE_STATIC`\
 Wskazuje magazyn statyczny.

 `DBG_ATTRIB_STORAGE_REGISTER`\
 Wskazuje magazyn w rejestrze.

 `DBG_ATTRIB_STORAGE_ALL`\
 Maska, aby wyodrębnić atrybuty magazynu z `DBG_ATTRIB_FLAGS`pliku .

 `DBG_ATTRIB_TYPE_NONE`\
 Wskazuje, że nie ma żadnego modyfikatora typu.

 `DBG_ATTRIB_TYPE_VIRTUAL`\
 Wskazuje, że typ obiektu jest wirtualny.

 `DBG_ATTRIB_TYPE_CONSTANT`\
 Wskazuje, że typ obiektu jest stały.

 `DBG_ATTRIB_TYPE_SYNCHRONIZED`\
 Wskazuje, że typ obiektu jest zsynchronizowany.

 `DBG_ATTRIB_TYPE_VOLATILE`\
 Wskazuje, że typ obiektu jest zmienny.

 `DBG_ATTRIB_TYPE_ALL`\
 Maska, aby wyodrębnić atrybuty typu z `DBG_ATTRIB_FLAGS`pliku .

 `DBG_ATTRIB_DATA`\
 Wskazuje, że ten obiekt jest polem danych.

 `DBG_ATTRIB_METHOD`\
 Wskazuje, że ten obiekt jest metodą.

 `DBG_ATTRIB_PROPERTY`\
 Wskazuje, że ten obiekt jest właściwością.

 `DBG_ATTRIB_CLASS`\
 Wskazuje, że ten obiekt jest klasą.

 `DBG_ATTRIB_BASECLASS`\
 Wskazuje, że ten obiekt jest klasą podstawową.

 `DBG_ATTRIB_INTERFACE`\
 Wskazuje, że ten obiekt jest interfejsem.

 `DBG_ATTRIB_INNERCLASS`\
 Wskazuje, że ten obiekt jest klasą wewnętrzną.

 `DBG_ATTRIB_MOSTDERIVED`\
 Wskazuje, że ten obiekt jest '*najbardziej pochodnym*'. Termin "*najbardziej pochodne*" oznacza rzeczywisty typ obiektu, a nie typ jego odwołania.

 `DBG_ATTRIB_CHILD_ALL`\
 Wskazuje maskę `DBG_ATTRIB_DATA` przez `DBG_ATTRIB_MOSTDERIVED`.

 `DBG_ATTRIB_MULTI_CUSTOM_VIEWERS`\
 Wskazuje, że obiekt ma wiele niestandardowych widzów skojarzonych z nim.

## <a name="remarks"></a>Uwagi

> [!NOTE]
> Wartości w tym wyliczeniu nie są faktycznie zdefiniowane w zestawie dla języka C#. Zamiast tego należy skopiować definicje do pliku źródłowego.

 Flagi te są również używane do filtrowania podstawowych podstawowych obiekcie, na przykład, gdy przekazywane jako argument do [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md). Wartości mogą być łączone `OR`z bitowym .

 Flaga `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` jest wskazanie, aby [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] uzyskać interfejs [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) z interfejsu [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) i wywołać [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) dla listy niestandardowych przeglądarek.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
