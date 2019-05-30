---
title: IDebugProgramNode2::GetEngineInfo | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d49bbaf4ca4b4d85d198eeb51b2eb4d13508d39
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351158"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
Pobiera nazwę i identyfikator aparat debugowania (DE), który używa programu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetEngineInfo ( 
   BSTR* pbstrEngine,
   GUID* pguidEngine
);
```

```csharp
int GetEngineInfo(
   out string pbstrEngine,
   out Guid pguidEngine
);
```

## <a name="parameters"></a>Parametry
`pbstrEngine`\
[out] Zwraca nazwę DE działania programu (C++-określonych: może to być wskaźnik zerowy, co oznacza, że obiekt wywołujący nie zainteresowanych nazwę aparat).

`pguidEngine`\
[out] Zwraca unikatowy identyfikator globalny DE działania programu (C++-określonych: może to być wskaźnik zerowy, co oznacza, że obiekt wywołujący nie zainteresowani GUID aparatu).

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)