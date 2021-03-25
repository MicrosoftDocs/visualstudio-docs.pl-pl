---
description: Umożliwia programowi Expression ewaluatora (EE) określenie interfejsu wywołania zwrotnego, który będzie używany przez aparat debugera (DE) do odczytu ustawień metryki.
title: 'IDebugExpressionEvaluator2:: setcallback | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d29707fb75a83b4e9508052531c18e8fa4796e2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095384"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
Umożliwia programowi Expression ewaluatora (EE) określenie interfejsu wywołania zwrotnego, który będzie używany przez aparat debugera (DE) do odczytu ustawień metryki.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetCallback (
    IDebugSettingsCallback2* pCallback
);
```

```csharp
int SetCallback (
    IDebugSettingsCallback2 pCallback
);
```

## <a name="parameters"></a>Parametry
`pCallback`\
podczas Interfejs do użycia dla wywołania zwrotnego ustawień.

## <a name="return-value"></a>Wartość zwracana
Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Ta metoda zapewnia interfejs do Menedżera debugowania sesji, którego ewaluatora wyrażeń można używać do odczytywania ustawień metryki. Jest to przydatne w przypadku zdalnego debugowania do odczytywania metryk na [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] komputerze.

## <a name="example"></a>Przykład
W poniższych przykładach pokazano, jak zaimplementować tę metodę dla obiektu **CEE** , który uwidacznia Interfejs [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) .

```cpp
HRESULT CEE::SetCallback(IDebugSettingsCallback2* in_pCallback)
{
    // precondition
    INVARIANT( this );

    // function body
    if (NULL != this->m_LanguageSpecificUseCases.pfSetCallback)
    {
        EEDomain::fSetCallback DomainVal =
        {
            in_pCallback
        };

        BOOL bSuccess = (*this->m_LanguageSpecificUseCases.pfSetCallback)(DomainVal);
        ENSURE( bSuccess );
    }

    // postcondition
    INVARIANT( this );

    return S_OK;
}
```

## <a name="see-also"></a>Zobacz też
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
