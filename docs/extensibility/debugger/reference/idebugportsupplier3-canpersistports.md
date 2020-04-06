---
title: IDebugPortSupplier3::CanPersistPorts | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2bf436d788b517300bee9a13b66b0ca3747bcc43
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724464"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Ta metoda określa, czy dostawca portu może utrwalać porty (zapisując je na dysku) między wywołaniami debugera.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>Parametry
 Brak.

## <a name="return-value"></a>Wartość zwracana
 `S_OK`jeśli porty mogą być `S_FALSE` zachowywane lub wskazać, że porty nie mogą być utrwalone.

## <a name="remarks"></a>Uwagi
 Jeśli dostawca portu może utrzymywać porty, należy to zrobić, gdy jest niszczony, a następnie ponownie załadować je po ponownym wystąpieniu.

## <a name="see-also"></a>Zobacz też
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
