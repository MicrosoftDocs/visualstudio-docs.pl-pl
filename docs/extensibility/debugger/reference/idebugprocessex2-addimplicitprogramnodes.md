---
title: IDebugProcessEx2::AddImplicitProgramNodes | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6203b12defbe70d3807508953d85f39ff725a746
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693524"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
Metoda ta umożliwia dodanie węzła dla każdego silnika debugowania (DE) określony program.

## <a name="syntax"></a>Składnia

```cpp
HRESULT AddImplicitProgramNodes(
   REFGUID guidLaunchingEngine,
   GUID*   rgguidSpecificEngines,
   DWORD   celtSpecificEngines
);
```

```csharp
int AddImplicitProgramNodes(
   ref Guid guidLaunchingEngine,
   Guid[]   rgguidSpecificEngines,
   uint     celtSpecificEngines
);
```

#### <a name="parameters"></a>Parametry
 `guidLaunchingEngine`

 [in] `GUID` Z DE, która ma być używany do uruchamiania programów (przyjęto, że można dodać węzły swój własny program).

 `rgguidSpecificEngines`

 [in] Tablica `GUID`s DEs dla programu, który zostanie dodany węzłów.

 `celtSpecificEngines`

 [in] Liczba `GUID`s w `rgguidSpecificEngines` tablicy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
- [Program węzłów](../../../extensibility/debugger/program-nodes.md) zostanie dodana dla każdego DE wymienionych w `rgguidSpecificEngines`— z wyjątkiem uruchamiania aparatu (podany w `guidLaunchingEngine`), który zakłada się, że dodanie węzła swój własny program jest uruchamiany program.

## <a name="see-also"></a>Zobacz też
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [Węzły programu](../../../extensibility/debugger/program-nodes.md)