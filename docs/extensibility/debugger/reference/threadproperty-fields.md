---
title: THREADPROPERTY_FIELDS | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c908658662d96d5c1ad5f3b16e9dcce2e4f7235
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458485"
---
# <a name="threadpropertyfields"></a>THREADPROPERTY_FIELDS
Określa, jakie informacje o wątku do pobrania.

## <a name="syntax"></a>Składnia

```cpp
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

## <a name="fields"></a>Pola
 `TPF_ID`\
 Inicjowanie bądź użyj `dwThreadId` pole [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) struktury.

 `TPF_SUSPENDCOUNT`\
 Inicjowanie bądź użyj `dwSuspendCount` pole `THREADPROPERTIE`Struktura.

 `TPF_STATE`\
 Inicjowanie bądź użyj `dwThreadState` pole `THREADPROPERTIE`Struktura.

 `TPF_PRIORITY`\
 Inicjowanie bądź użyj `bstrPriority` pole `THREADPROPERTIE`Struktura.

 `TPF_NAME`\
 Inicjowanie bądź użyj `bstrName` pole `THREADPROPERTIE`Struktura.

 `TPF_LOCATION`\
 Inicjowanie bądź użyj `bstrLocation` pole `THREADPROPERTIE`Struktura.

 `TPF_ALLFIELDS`\
 Określa wszystkie pola.

## <a name="remarks"></a>Uwagi
 Te wartości są przekazywane jako argument do [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) metodę, aby wskazać, które pola [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) struktury, które mają zostać zainicjowane.

 Te wartości są również używane w `dwFields` członkiem `THREADPROPERTIES` struktury, aby wskazać, które pola są używane i prawidłowy.

 Te flagi mogą być łączone przy użyciu bitowego operatora `OR`.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)