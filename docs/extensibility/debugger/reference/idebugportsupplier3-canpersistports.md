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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 092f6e372d8f98e731ad90a7d261fe015d019656
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172012"
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
