---
title: IDebugSymbolProviderDirect::GetMetaDataImport | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetMetaDataImport
- IDebugSymbolProviderDirect::GetMetaDataImport
ms.assetid: b51a492c-af00-4b08-93fb-6c19ee4916aa
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c2b6a97dd00edc66699fbf815ed56031ed74ac3b
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66207039"
---
# <a name="idebugsymbolproviderdirectgetmetadataimport"></a>IDebugSymbolProviderDirect::GetMetaDataImport
Pobiera informacje o Importowanie metadanych.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetMetaDataImport (
    GUID*      guid,
    DWORD      appID,
    IUnknown** ppImport
);
```

```csharp
int GetMetaDataImport (
    Guid       guid,
    uint       appID,
    out object ppImport
);
```

## <a name="parameters"></a>Parametry
`guid`\
[in] Unikatowy identyfikator dla modułu.

`appID`\
[in] Identyfikator domeny aplikacji.

`ppImport`\
[out] Zwraca obiekt, który zawiera metadane zaimportować informacje o.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)