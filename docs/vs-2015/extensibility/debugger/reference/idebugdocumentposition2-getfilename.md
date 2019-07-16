---
title: IDebugDocumentPosition2::GetFileName | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetFileName
helpviewer_keywords:
- IDebugDocumentPosition2::GetFileName
ms.assetid: d713635e-088f-465b-b26d-00ac971c9e86
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8298388f9f7bd0504cf586241fbbf4945feebdd0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200269"
---
# <a name="idebugdocumentposition2getfilename"></a>IDebugDocumentPosition2::GetFileName
Pobiera nazwę pliku pliku źródłowego, który zawiera położenie dokumentu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetFileName( 
   BSTR* pbstrFileName
);
```

```csharp
int GetFileName( 
   out string pbstrFileName
);
```

#### <a name="parameters"></a>Parametry
 `pbstrFileName`

 [out] Zwraca nazwę pliku źródłowego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Plik źródłowy nie może mieć zawsze nazwę pliku (pliku źródłowego może nie istnieć na dysku, na przykład).

## <a name="see-also"></a>Zobacz też
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)