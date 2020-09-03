---
title: 'IDebugDisassemblyStream2:: GetCurrentLocation | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCurrentLocation
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCurrentLocation
ms.assetid: 512302f1-12b1-4107-8a6e-c5bc878ce1c3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 440afc26688522da5cc8b6c20b2712872b4ce6b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732226"
---
# <a name="idebugdisassemblystream2getcurrentlocation"></a>IDebugDisassemblyStream2::GetCurrentLocation
Zwraca identyfikator lokalizacji kodu, który reprezentuje bieżącą lokalizację kodu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetCurrentLocation( 
   UINT64* puCodeLocationId
);
```

```csharp
int GetCurrentLocation( 
   out ulong puCodeLocationId
);
```

## <a name="parameters"></a>Parametry
`puCodeLocationId`\
określoną Zwraca identyfikator lokalizacji kodu. Zapoznaj się z sekcją spostrzeżenia metody [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) , aby uzyskać opis identyfikatora lokalizacji kodu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Identyfikator lokalizacji kodu można przekonwertować na kontekst kodu, wywołując metodę [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) .

## <a name="see-also"></a>Zobacz też
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
