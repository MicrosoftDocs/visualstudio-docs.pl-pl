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
ms.openlocfilehash: 9e969d7c6f17aeaa8642b9988e741318ec1591d6
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691257"
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

#### <a name="parameters"></a>Parametry
 `pclsid`

 [out] Zwraca identyfikator GUID, który jest Identyfikatorem klasy dokumentu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Identyfikator GUID klasy może służyć do tworzenia wystąpień poszczególnych klas, z których każdy reprezentuje dokumentu.

## <a name="see-also"></a>Zobacz też
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)