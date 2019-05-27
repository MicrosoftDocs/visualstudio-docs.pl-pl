---
title: IDebugDocument2::GetDocumentClassID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetDocumentClassID
helpviewer_keywords:
- IDebugDocument2::GetDocumentClassID
ms.assetid: 111c2b85-ebfa-487f-b896-2ec4a3eac4d1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 075d29334fd32b6f3351786d084d3c6d1758a782
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66204840"
---
# <a name="idebugdocument2getdocumentclassid"></a>IDebugDocument2::GetDocumentClassID
Pobiera identyfikator klasy dokumentu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetDocumentClassID( 
   CLSID* pclsid
);
```

```csharp
int GetDocumentClassID( 
   out Guid pclsid
);
```

## <a name="parameters"></a>Parametry
`pclsid` [out] Zwraca identyfikator GUID, który jest Identyfikatorem klasy dokumentu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Identyfikator GUID klasy może służyć do tworzenia wystąpień poszczególnych klas, z których każdy reprezentuje dokumentu.

## <a name="see-also"></a>Zobacz także
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)