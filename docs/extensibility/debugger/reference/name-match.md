---
title: NAME_MATCH | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- NAME_MATCH
helpviewer_keywords:
- NAME_MATCH enumeration
ms.assetid: 3842c417-a3c9-4259-a05f-52b64b829ef6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26666ff9955d7516ff30c7276bfd46e990577e70
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56714832"
---
# <a name="namematch"></a>NAME_MATCH
Wybierze case opcję do dopasowania nazwy.

## <a name="syntax"></a>Składnia

```cpp
typedef enum { 
   nmNone            = 0,
   nmCaseSensitive   = 1,
   nmCaseInsensitive = 2
} NAME_MATCH;
```

```csharp
public enum NameMatchOptions { 
   nmNone            = 0,
   nmCaseSensitive   = 1,
   nmCaseInsensitive = 2
}
```

## <a name="members"></a>Elementy członkowskie
 nmNone, których nie określono opcji.

 Wskazuje, że nazwy mają być dopasowywane nmCaseSensitive jest rozróżniana wielkość liter.

 Wskazuje, że nazwy mają być dopasowywane nmCaseInsensitive nie jest rozróżniana wielkość liter.

## <a name="remarks"></a>Uwagi
 Przekazywany jako argument do następujących metod:

-   [GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)

-   [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)

-   [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)

-   [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)
- [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)
- [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)