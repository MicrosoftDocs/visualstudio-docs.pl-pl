---
description: Opisuje różne atrybuty interfejsu IDebugProperty2 lub IDebugReference2.
title: DBG_ATTRIB_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f467c9ac66bc249974f919a48a1527bebb26f361
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170721"
---
# <a name="dbg_attrib_flags"></a>DBG_ATTRIB_FLAGS
Opisuje różne atrybuty interfejsu [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) lub [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) . Składowa struktury [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) .

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
 Nie wskazuje żadnych atrybutów.

 `DBG_ATTRIB_ALL`\
 Wskazuje wszystkie atrybuty.

 `DBG_ATTRIB_OBJ_IS_EXPANDABLE`\
 Wskazuje, że odwołanie lub właściwość zawiera elementy podrzędne.

 `DBG_ATTRIB_OBJ_HAS_ID`\
 Wskazuje, że identyfikator dla tego obiektu został utworzony.

 `DBG_ATTRIB_OBJ_CAN_HAVE_ID`\
 Wskazuje, że można utworzyć identyfikator dla tego obiektu.

 `DBG_ATTRIB_VALUE_READONLY`\
 Wskazuje, że wartość jest tylko do odczytu.

 `DBG_ATTRIB_VALUE_ERROR`\
 Wskazuje, że wartość jest błędem.

 `DBG_ATTRIB_VALUE_SIDE_EFFECT`\
 Wskazuje, że Ocena miała efekt uboczny.

 `DBG_ATTRIB_OVERLOADED_CONTAINER`\
 Wskazuje, że ta właściwość jest w rzeczywistości kontenerem przeciążenia.

 `DBG_ATTRIB_VALUE_BOOLEAN`\
 Wskazuje, że wartość w `DEBUG_PROPERTY_INFO::bstrValue` jest wartością logiczną.

 `DBG_ATTRIB_VALUE_BOOLEAN_TRUE`\
 Wskazuje, że wartość w `DEBUG_PROPERTY_INFO::bstrValue` jest wartością logiczną i `TRUE` .

 `DBG_ATTRIB_VALUE_INVALID`\
 Wskazuje, że wartość w `DEBUG_PROPERTY_INFO::bstrValue` jest nieprawidłowa.

 `DBG_ATTRIB_VALUE_NAT`\
 Wskazuje, że wartość w `DEBUG_PROPERTY_INFO::bstrValue` to "*nie jako*" (NAT). Translator adresów sieciowych opisuje flagę Register w procesorze Intel 64-bitowym, która wskazuje odroczone wyjątki.

 `DBG_ATTRIB_VALUE_AUTOEXPANDED`\
 Wskazuje, że wartość w `DEBUG_PROPERTY_INFO::bstrValue` jest prawdopodobnie rozszerzona.

 `DBG_ATTRIB_VALUE_TIMEOUT`\
 Wskazuje, że upłynął limit czasu obliczania.

 `DBG_ATTRIB_VALUE_RAW_STRING`\
 Wskazuje, że wartość w `DEBUG_PROPERTY_INFO::bstrValue` może być reprezentowana przez nieprzetworzony ciąg.

 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER`\
 Wskazuje, że ta właściwość ma skojarzoną co najmniej jedną przeglądarkę niestandardową.

 `DBG_ATTRIB_ACCESS_NONE`\
 Wskazuje obiekt, który nie ma ani nie ma `public` `private` `protected` dostępu do typu.

 `DBG_ATTRIB_ACCESS_PUBLIC`\
 Wskazuje obiekt, który ma dostęp publiczny.

 `DBG_ATTRIB_ACCESS_PRIVATE`\
 Wskazuje obiekt z dostępem prywatnym.

 `DBG_ATTRIB_ACCESS_PROTECTED`\
 Wskazuje obiekt z dostępem chronionym.

 `DBG_ATTRIB_ACCESS_FINAL`\
 Wskazuje obiekt, który ma końcowy dostęp.

 `DBG_ATTRIB_ACCESS_ALL`\
 Maska, z której mają zostać wyodrębnione atrybuty dostępu `DBG_ATTRIB_FLAGS` .

 `DBG_ATTRIB_STORAGE_NONE`\
 Wskazuje, że nie określono typu magazynu.

 `DBG_ATTRIB_STORAGE_GLOBAL`\
 Wskazuje globalny magazyn.

 `DBG_ATTRIB_STORAGE_STATIC`\
 Wskazuje magazyn statyczny.

 `DBG_ATTRIB_STORAGE_REGISTER`\
 Wskazuje magazyn w rejestrze.

 `DBG_ATTRIB_STORAGE_ALL`\
 Maskowanie, z którego mają zostać wyodrębnione atrybuty magazynu `DBG_ATTRIB_FLAGS` .

 `DBG_ATTRIB_TYPE_NONE`\
 Wskazuje, że nie ma modyfikatora typu.

 `DBG_ATTRIB_TYPE_VIRTUAL`\
 Wskazuje, że typ obiektu jest wirtualny.

 `DBG_ATTRIB_TYPE_CONSTANT`\
 Wskazuje, że typem obiektu jest stała.

 `DBG_ATTRIB_TYPE_SYNCHRONIZED`\
 Wskazuje, że typ obiektu jest synchronizowany.

 `DBG_ATTRIB_TYPE_VOLATILE`\
 Wskazuje, że typ obiektu jest nietrwały.

 `DBG_ATTRIB_TYPE_ALL`\
 Maska, z której mają zostać wyodrębnione atrybuty typu `DBG_ATTRIB_FLAGS` .

 `DBG_ATTRIB_DATA`\
 Wskazuje, że ten obiekt jest polem danych.

 `DBG_ATTRIB_METHOD`\
 Wskazuje, że ten obiekt jest metodą.

 `DBG_ATTRIB_PROPERTY`\
 Wskazuje, że ten obiekt jest właściwością.

 `DBG_ATTRIB_CLASS`\
 Wskazuje, że ten obiekt jest klasą.

 `DBG_ATTRIB_BASECLASS`\
 Wskazuje, że ten obiekt jest klasą bazową.

 `DBG_ATTRIB_INTERFACE`\
 Wskazuje, że ten obiekt jest interfejsem.

 `DBG_ATTRIB_INNERCLASS`\
 Wskazuje, że ten obiekt jest klasą wewnętrzną.

 `DBG_ATTRIB_MOSTDERIVED`\
 Wskazuje, że ten obiekt jest "*najbardziej pochodny*". Termin "*najbardziej pochodny*" oznacza rzeczywisty typ obiektu, a nie typ odwołania.

 `DBG_ATTRIB_CHILD_ALL`\
 Wskazuje maskę `DBG_ATTRIB_DATA` przez `DBG_ATTRIB_MOSTDERIVED` .

 `DBG_ATTRIB_MULTI_CUSTOM_VIEWERS`\
 Wskazuje, że do obiektu jest skojarzonych wiele niestandardowych podglądów.

## <a name="remarks"></a>Uwagi

> [!NOTE]
> Wartości w tym wyliczeniu nie są w rzeczywistości zdefiniowane w zestawie dla języka C#. Zamiast tego należy skopiować definicje do pliku źródłowego.

 Te flagi są również używane do filtrowania elementów podrzędnych obiektu, na przykład w przypadku przekazywania jako argumentu do [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md). Wartości mogą być połączone z bitową `OR` .

 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER`Flaga jest wskazaniem, aby [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] uzyskać Interfejs [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) z interfejsu [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) i wywołać [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) dla listy niestandardowych osób przeglądających.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
