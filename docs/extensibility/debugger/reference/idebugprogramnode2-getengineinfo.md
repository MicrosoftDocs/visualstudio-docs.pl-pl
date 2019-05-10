---
title: IDebugProgramNode2::GetEngineInfo | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c31d3a858af2886a27a51e22e131cb89b2234d6e
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65459068"
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