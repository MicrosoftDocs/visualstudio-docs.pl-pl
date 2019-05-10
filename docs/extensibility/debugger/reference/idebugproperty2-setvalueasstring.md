---
title: IDebugProperty2::SetValueAsString | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 310d2e3cd8c7f1caea4e245c7c591cd402afdaf4
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458874"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
Ustawia wartości właściwości z ciągu.

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

 [in] Ciąg zawierający wartość do ustawienia.

 `nRadix`\

 [in] Podstawy do użycia w interpretacji wszelkie dane liczbowe. Może to być 0, aby podjąć próbę automatycznego określenia podstawy.

 `dwTimeout`\

 [in] Określa maksymalny czas (w milisekundach) oczekiwania przed zwróceniem z tej metody. Użyj `INFINITE` czekanie w nieskończoność.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono inne możliwe wartości.

|Wartość|Opis|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Nie można przekonwertować ciągu na wartość właściwości lub nie można ustawić wartości właściwości.|
|`E_SETVALUE_VALUE_IS_READONLY`|Właściwość jest tylko do odczytu.|

## <a name="see-also"></a>Zobacz także
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)