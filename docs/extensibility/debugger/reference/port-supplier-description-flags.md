---
title: PORT_SUPPLIER_DESCRIPTION_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- PORT_SUPPLIER_DESCRIPTION_FLAGS enumeration
ms.assetid: 5acee0ee-3a20-41c9-a7dc-0dadae6a5ba5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a0241265f05f616b8810f84c1a82689a8604237
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212733"
---
# <a name="portsupplierdescriptionflags"></a>PORT_SUPPLIER_DESCRIPTION_FLAGS

Definiuje metadanych, które mogą być pobierane o dostawcy portu.

## <a name="syntax"></a>Składnia

```cpp
enum enum_PORT_SUPPLIER_DESCRIPTION_FLAGS
{
    PSDFLAG_SHOW_WARNING_ICON = 0x1
};
typedef DWORD PORT_SUPPLIER_DESCRIPTION_FLAGS;
```

```csharp
public enum enum_PORT_SUPPLIER_DESCRIPTION_FLAGS
{
    PSDFLAG_SHOW_WARNING_ICON = 0x1
};
```

## <a name="fields"></a>Pola

`PSDFLAG_SHOW_WARNING_ICON`\
Jeśli zaznaczone, pojawi się ikona ostrzeżenia w interfejsie użytkownika.

## <a name="remarks"></a>Uwagi

To wyliczenie jest zwracany przez [GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md) metody.

## <a name="requirements"></a>Wymagania

Nagłówek: Msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także

- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)
