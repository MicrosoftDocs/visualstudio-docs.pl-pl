---
description: Ustawia wartość właściwości z danego ciągu.
title: 'IDebugProperty2:: SetValueAsString | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b86de71cd6df3e028697518de8c6faccad7e2336
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166726"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
Ustawia wartość właściwości z danego ciągu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetValueAsString ( 
   LPCOLESTR pszValue,
   UINT      nRadix,
   DWORD     dwTimeout
);
```

```csharp
int SetValueAsString ( 
   string pszValue,
   uint   nRadix,
   uint   dwTimeout
);
```

## <a name="parameters"></a>Parametry
`pszValue`\
podczas Ciąg zawierający wartość do ustawienia.

`nRadix`\
podczas Podstawy do użycia w interpretacji wszelkich informacji numerycznych. Może to być wartość 0, aby próbować określić podstawy automatycznie.

`dwTimeout`\
podczas Określa maksymalny czas oczekiwania (w milisekundach) przed powrotem z tej metody. Użyj `INFINITE` , aby czekać w nieskończoność.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono inne możliwe wartości.

|Wartość|Opis|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Nie można przekonwertować ciągu na wartość właściwości lub nie można ustawić wartości właściwości.|
|`E_SETVALUE_VALUE_IS_READONLY`|Właściwość jest tylko do odczytu.|

## <a name="see-also"></a>Zobacz też
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
