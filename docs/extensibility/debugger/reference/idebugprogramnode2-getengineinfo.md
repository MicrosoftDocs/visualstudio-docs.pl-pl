---
title: IDebugProgramNode2::GetEngineInfo | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c2e74ba3c0f826314818bc883778a6364ff3fb6e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722104"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
Pobiera nazwę i identyfikator aparatu debugowania (DE) z uruchomionym programem.

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
[na zewnątrz] Zwraca nazwę DE uruchomionego programu (C++-specific: może to być wskaźnik null wskazujący, że wywołujący nie jest zainteresowany nazwą aparatu).

`pguidEngine`\
[na zewnątrz] Zwraca globalnie unikatowy identyfikator de uruchomiony program (C++-specific: może to być wskaźnik null wskazujący, że wywołujący nie jest zainteresowany identyfikatorem GUID aparatu).

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
