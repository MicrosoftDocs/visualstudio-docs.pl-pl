---
title: THREADPROPERTY_FIELDS | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b31c43187d1136f7a194c42749c430de6cd064a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713398"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
Określa, jakie informacje o wątku mają być pobierane.

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
 Zainicjować/użyć `dwThreadId` pola [threadproperties](../../../extensibility/debugger/reference/threadproperties.md) struktury.

 `TPF_SUSPENDCOUNT`\
 Inicjowanie/używanie `dwSuspendCount` pola `THREADPROPERTIE`struktury S.

 `TPF_STATE`\
 Inicjowanie/używanie `dwThreadState` pola `THREADPROPERTIE`struktury S.

 `TPF_PRIORITY`\
 Inicjowanie/używanie `bstrPriority` pola `THREADPROPERTIE`struktury S.

 `TPF_NAME`\
 Inicjowanie/używanie `bstrName` pola `THREADPROPERTIE`struktury S.

 `TPF_LOCATION`\
 Inicjowanie/używanie `bstrLocation` pola `THREADPROPERTIE`struktury S.

 `TPF_ALLFIELDS`\
 Określa wszystkie pola.

## <a name="remarks"></a>Uwagi
 Wartości te są przekazywane jako argument do [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) metody, aby wskazać, które pola [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) struktury mają być zainicjowane.

 Wartości te są `dwFields` również używane `THREADPROPERTIES` w elementów członkowskich struktury, aby wskazać, które pola są używane i prawidłowe.

 Flagi te mogą być łączone z bitowym `OR`.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
