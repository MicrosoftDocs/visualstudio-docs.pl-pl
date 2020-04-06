---
title: IDebugExpressionEvaluator2::SetCallback | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 907fdaa928b3f84f6ff37490d5c54a9d48515053
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729336"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
Umożliwia oceniającemu wyrażenie (EE) określenie interfejsu wywołania zwrotnego, który aparat debugera (DE) użyje do odczytu ustawień metryki.

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
[w] Interfejs do użycia dla ustawień wywołania zwrotnego.

## <a name="return-value"></a>Wartość zwracana
Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Ta metoda zapewnia interfejs do menedżera debugowania sesji, który oceniający wyrażenie może używać do odczytu ustawień metryki. Jest to przydatne w zdalnym debugowaniu [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] do odczytu metryki na komputerze.

## <a name="example"></a>Przykład
Poniższe przykłady pokazują, jak zaimplementować tę metodę dla obiektu **CEE,** który udostępnia interfejs [IDebugSettingsCallback2.](../../../extensibility/debugger/reference/idebugsettingscallback2.md)

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
