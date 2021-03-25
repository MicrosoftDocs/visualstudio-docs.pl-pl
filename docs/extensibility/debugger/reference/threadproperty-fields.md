---
description: Określa, jakie informacje o wątku mają być pobierane.
title: THREADPROPERTY_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 81d185a80761e42e706dc3ef36da056bb37b0b1c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070872"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
Określa, jakie informacje o wątku mają być pobierane.

## <a name="syntax"></a>Składnia

```cpp
enum enum_THREADPROPERTY_FIELDS { 
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
public enum enum_THREADPROPERTY_FIELDS { 
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
 Zainicjuj/Użyj `dwThreadId` pola struktury [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) .

 `TPF_SUSPENDCOUNT`\
 Zainicjuj/Użyj `dwSuspendCount` pola `THREADPROPERTIE` struktury S.

 `TPF_STATE`\
 Zainicjuj/Użyj `dwThreadState` pola `THREADPROPERTIE` struktury S.

 `TPF_PRIORITY`\
 Zainicjuj/Użyj `bstrPriority` pola `THREADPROPERTIE` struktury S.

 `TPF_NAME`\
 Zainicjuj/Użyj `bstrName` pola `THREADPROPERTIE` struktury S.

 `TPF_LOCATION`\
 Zainicjuj/Użyj `bstrLocation` pola `THREADPROPERTIE` struktury S.

 `TPF_ALLFIELDS`\
 Określa wszystkie pola.

## <a name="remarks"></a>Uwagi
 Te wartości są przesyłane jako argument do metody [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) , aby wskazać, które pola struktury [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) mają być inicjowane.

 Te wartości są również używane w `dwFields` składowej `THREADPROPERTIES` struktury, aby wskazać, które pola są używane i są prawidłowe.

 Flagi te mogą być połączone z bitową `OR` .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
