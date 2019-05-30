---
title: IDebugPortSupplier3::CanPersistPorts | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 11bc6e21e8b70a5bd95c001f4173a7da3f3fe4be
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340071"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Ta metoda określa, czy dostawca portu można utrwalić portów (zapisując je na dysku) między wywołań debugera.

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
 `S_OK` Jeśli porty mogą zostać utrwalone, lub `S_FALSE` do wskazania, czy porty nie może zostać utrwalona.

## <a name="remarks"></a>Uwagi
 Jeśli dostawcy portu można utrwalić portów, należy to zrobić, kiedy niszczony jest i ponownie załadować, gdy zostanie uruchomiony ponownie.

## <a name="see-also"></a>Zobacz także
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)