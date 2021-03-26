---
description: Ta metoda określa, czy dostawca portu może utrzymywać porty (pisząc je na dysku) między wywołaniami debugera.
title: 'IDebugPortSupplier3:: CanPersistPorts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 570409a114acbf19697b0eb3ef3e5496fdfde93a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071977"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Ta metoda określa, czy dostawca portu może utrzymywać porty (pisząc je na dysku) między wywołaniami debugera.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>Parametry
 Brak.

## <a name="return-value"></a>Wartość zwracana
 `S_OK` Jeśli porty mogą być utrwalane lub `S_FALSE` wskazywać, że nie można utrwalić portów.

## <a name="remarks"></a>Uwagi
 Jeśli dostawca portu może utrzymywać porty, należy to zrobić, gdy zostanie zniszczony, a następnie ponownie załaduj ponownie po utworzeniu wystąpienia.

## <a name="see-also"></a>Zobacz też
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
