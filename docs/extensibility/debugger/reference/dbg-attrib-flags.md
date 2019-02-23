---
title: DBG_ATTRIB_FLAGS | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 831d1326d88e70ffaba2cc0c242c55d7325be705
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689333"
---
# <a name="dbgattribflags"></a>DBG_ATTRIB_FLAGS
W tym artykule opisano różne atrybuty dla [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) lub [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) interfejsu. Członek [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury.

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
 DBG_ATTRIB_NONE wskazuje żadnych atrybutów.

 DBG_ATTRIB_ALL wskazuje wszystkie atrybuty.

 DBG_ATTRIB_OBJ_IS_EXPANDABLE wskazuje, że odwołanie lub właściwość ma elementy podrzędne.

 DBG_ATTRIB_OBJ_HAS_ID wskazuje, że utworzono Identyfikatora dla tego obiektu.

 DBG_ATTRIB_OBJ_CAN_HAVE_ID wskazuje, że można utworzyć Identyfikatora dla tego obiektu.

 DBG_ATTRIB_VALUE_READONLY wskazuje, że wartość jest tylko do odczytu.

 DBG_ATTRIB_VALUE_ERROR wskazuje, że wartość jest błędem.

 DBG_ATTRIB_VALUE_SIDE_EFFECT wskazuje, że ocena ma efekt uboczny.

 DBG_ATTRIB_OVERLOADED_CONTAINER wskazuje, że ta właściwość jest naprawdę kontener przeciążenia.

 DBG_ATTRIB_VALUE_BOOLEAN wskazuje, że wartość w `DEBUG_PROPERTY_INFO::bstrValue` jest wartością logiczną.

 DBG_ATTRIB_VALUE_BOOLEAN_TRUE wskazuje, że wartość w `DEBUG_PROPERTY_INFO::bstrValue` jest atrybut typu wartość logiczna i `TRUE`.

 DBG_ATTRIB_VALUE_INVALID wskazuje, że wartość w `DEBUG_PROPERTY_INFO::bstrValue` jest nieprawidłowy.

 DBG_ATTRIB_VALUE_NAT wskazuje, że wartość w `DEBUG_PROPERTY_INFO::bstrValue` jest "*nie niczego*" (NAT). Translator adresów Sieciowych w tym artykule opisano flagę rejestru w 64-bitowych procesorów Intel wskazującą odroczonego spekulacyjnego wyjątków.

 DBG_ATTRIB_VALUE_AUTOEXPANDED wskazuje, że wartość w `DEBUG_PROPERTY_INFO::bstrValue` prawdopodobnie został rozszerzony automatycznie.

 DBG_ATTRIB_VALUE_TIMEOUT wskazuje, że ocena przekroczyła limit czasu.

 DBG_ATTRIB_VALUE_RAW_STRING wskazuje, że wartość w `DEBUG_PROPERTY_INFO::bstrValue` może być reprezentowany przez nieprzetworzonego ciągu.

 DBG_ATTRIB_VALUE_CUSTOM_VIEWER wskazuje, że ta właściwość ma co najmniej jeden Przeglądarka niestandardowa skojarzonych z nim.

 DBG_ATTRIB_ACCESS_NONE wskazuje obiekt, który nie ma `public`, `private`, ani `protected` typu dostępu.

 DBG_ATTRIB_ACCESS_PUBLIC wskazuje obiekt, który ma dostęp publiczny.

 DBG_ATTRIB_ACCESS_PRIVATE wskazuje obiekt, który ma dostęp prywatny.

 DBG_ATTRIB_ACCESS_PROTECTED wskazuje obiekt, który został ochroną dostępu.

 DBG_ATTRIB_ACCESS_FINAL wskazuje obiekt, który ma dostęp do końcowej.

 Maska DBG_ATTRIB_ACCESS_ALL można wyodrębnić dostępu do atrybutów z `DBG_ATTRIB_FLAGS`.

 DBG_ATTRIB_STORAGE_NONE wskazuje, że nie ma bez określonego typu magazynu.

 Wskazuje DBG_ATTRIB_STORAGE_GLOBAL globalnej pamięci masowej.

 Wskazuje DBG_ATTRIB_STORAGE_STATIC statycznego magazynu.

 Wskazuje DBG_ATTRIB_STORAGE_REGISTER magazyn do rejestru.

 Maska DBG_ATTRIB_STORAGE_ALL można wyodrębnić magazyn atrybutów z `DBG_ATTRIB_FLAGS`.

 DBG_ATTRIB_TYPE_NONE wskazuje, że nie istnieje żadne modyfikatora typu.

 DBG_ATTRIB_TYPE_VIRTUAL wskazuje, że typ obiektu jest wirtualny.

 DBG_ATTRIB_TYPE_CONSTANT wskazuje, że typ obiektu jest stały.

 DBG_ATTRIB_TYPE_SYNCHRONIZED wskazuje, że typ obiektu, jest zsynchronizowany.

 DBG_ATTRIB_TYPE_VOLATILE wskazuje, że typ obiektu jest nietrwały.

 Maska DBG_ATTRIB_TYPE_ALL można wyodrębnić typ atrybutów z `DBG_ATTRIB_FLAGS`.

 DBG_ATTRIB_DATA wskazuje, czy ten obiekt jest polem danych.

 DBG_ATTRIB_METHOD wskazuje, czy ten obiekt jest metodą.

 DBG_ATTRIB_PROPERTY wskazuje, czy ten obiekt jest właściwością.

 DBG_ATTRIB_CLASS wskazuje, czy ten obiekt jest klasą.

 DBG_ATTRIB_BASECLASS wskazuje, czy ten obiekt jest klasą bazową.

 DBG_ATTRIB_INTERFACE wskazuje, że tego obiektu jest interfejsem.

 DBG_ATTRIB_INNERCLASS wskazuje, czy ten obiekt jest klasą wewnętrznego.

 DBG_ATTRIB_MOSTDERIVED wskazuje, że ten obiekt jest "*najbardziej pochodnego*". Termin "*najbardziej pochodnego*" oznacza, że rzeczywisty typ obiektu, a nie typu odwołanie.

 DBG_ATTRIB_CHILD_ALL wskazuje maską `DBG_ATTRIB_DATA` za pośrednictwem `DBG_ATTRIB_MOSTDERIVED`.

 DBG_ATTRIB_MULTI_CUSTOM_VIEWERS wskazuje, że obiekt ma wiele przeglądarek niestandardowych skojarzone z nią.

## <a name="remarks"></a>Uwagi

> [!NOTE]
>  Wartości w tym wyliczeniu nie są faktycznie zdefiniowane w zestawie dla języka C#. Zamiast tego należy skopiować definicji do pliku źródłowego.

 Te flagi są również używane do filtrowania elementy podrzędne obiektu, na przykład, gdy jest przekazywany jako argument do [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md). Wartości mogą być łączone przy użyciu bitowego operatora `OR`.

 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` Flaga jest wskazanie [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] uzyskać [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfejs z [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfejsu i wywołania [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) listę przeglądarek niestandardowych.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)