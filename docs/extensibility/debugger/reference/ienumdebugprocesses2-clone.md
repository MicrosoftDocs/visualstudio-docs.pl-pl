---
title: IEnumDebugProcesses2::Clone | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2::Clone
helpviewer_keywords:
- IEnumDebugProcesses2::Clone
ms.assetid: 3d4196d3-5a80-4f76-b8b2-f72e80c8d406
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e4c8e10f532bc6bc52ffc5abda246b7bd190f8ba
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203361"
---
# <a name="ienumdebugprocesses2clone"></a>IEnumDebugProcesses2::Clone
Zwraca kopię bieżącego wyliczenia jako oddzielny obiekt.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Clone(
   IEnumDebugProcesses2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugProcesses2 ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\
[out] Zwraca kopię tego wyliczenia jako oddzielny obiekt.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Kopię wyliczenia ma ten sam stan, co oryginalny w czasie, którego ta metoda jest wywoływana. Jednak stany kopiowania i oryginalne są niezależne i można zmieniać indywidualnie.

## <a name="see-also"></a>Zobacz także
- [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)