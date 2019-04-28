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
ms.openlocfilehash: 421eea42c169f586657998e5d4cd57c4c797b71e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916907"
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

#### <a name="parameters"></a>Parametry
 `pbstrEngine`

 [out] Zwraca nazwę DE działania programu (C++-określonych: może to być wskaźnik zerowy, co oznacza, że obiekt wywołujący nie zainteresowanych nazwę aparat).

 `pguidEngine`

 [out] Zwraca unikatowy identyfikator globalny DE działania programu (C++-określonych: może to być wskaźnik zerowy, co oznacza, że obiekt wywołujący nie zainteresowani GUID aparatu).

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)