---
title: IDebugProcessEx2::AddImplicitProgramNodes | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723396"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
Ta metoda dodaje węzeł programu dla każdego aparatu debugowania (DE) określony.

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
[w] De, `GUID` który ma być używany do uruchamiania programów (i zakłada się, aby dodać własne węzły programu).

`rgguidSpecificEngines`\
[w] Tablica `GUID`s DEs, dla których zostaną dodane węzły programu.

`celtSpecificEngines`\
[w] Liczba `GUID`s w `rgguidSpecificEngines` tablicy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
- [Węzły programu](../../../extensibility/debugger/program-nodes.md) zostaną dodane dla `rgguidSpecificEngines`każdego DE wymienione w —z `guidLaunchingEngine`wyłączeniem silnika uruchamiania (jak podano w ), który zakłada się, aby dodać własny węzeł programu po uruchomieniu programu.

## <a name="see-also"></a>Zobacz też
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [Węzły programu](../../../extensibility/debugger/program-nodes.md)
