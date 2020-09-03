---
title: 'IDebugProcessEx2:: AddImplicitProgramNodes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 113c81e95e7384be04b7e02a5c58cd2cad7c9c6b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723396"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
Ta metoda dodaje węzeł programu dla każdego określonego aparatu debugowania (DE).

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

## <a name="parameters"></a>Parametry
`guidLaunchingEngine`\
podczas `GUID` Z de, która ma być używana do uruchamiania programów (i przyjęto dodanie własnych węzłów programu).

`rgguidSpecificEngines`\
podczas Tablica `GUID` s of des, dla której zostaną dodane węzły programu.

`celtSpecificEngines`\
podczas Liczba `GUID` s w `rgguidSpecificEngines` tablicy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
- [Węzły programu](../../../extensibility/debugger/program-nodes.md) zostaną dodane do każdego elementu poza wymienionym na liście w programie `rgguidSpecificEngines` — z wyłączeniem aparatu uruchamiania (zgodnie z opisem w temacie `guidLaunchingEngine` ), który jest założono, że zostanie dodany własny węzeł programu podczas uruchamiania programu.

## <a name="see-also"></a>Zobacz też
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [Węzły programu](../../../extensibility/debugger/program-nodes.md)
