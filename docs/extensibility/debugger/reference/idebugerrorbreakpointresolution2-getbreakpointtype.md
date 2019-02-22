---
title: IDebugErrorBreakpointResolution2::GetBreakpointType | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpointResolution2::GetBreakpointType
helpviewer_keywords:
- IDebugErrorBreakpointResolution2::GetBreakpointType
ms.assetid: 0bdb1152-4752-4464-ae7c-6d666dc293b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a733a600c8e8f3e346ffffdac306982c88994709
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56707682"
---
# <a name="idebugerrorbreakpointresolution2getbreakpointtype"></a>IDebugErrorBreakpointResolution2::GetBreakpointType
Pobiera typ punktu przerwania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetBreakpointType(
    BP_TYPE* pBPType
);
```

```csharp
int GetBreakpointType(
    out enum_BP_TYPE pBPType
);
```

#### <a name="parameters"></a>Parametry
`pBPType`

 [out] Zwraca wartość z zakresu od [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) wyliczenie opisujące typ punktu przerwania.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Ta metoda zwraca typ punktu przerwania, którego nie można powiązać, dlatego wymagającej zdarzenie punktu przerwania błędu.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę dla prostego `CDebugErrorBreakpointResolution` obiekt ujawniający [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) interfejsu.

```
HRESULT CDebugErrorBreakpointResolution::GetBreakpointType(BP_TYPE* pBPType)
{
    HRESULT hr;

    if (pBPType)
    {
        // Set default BP_TYPE.
        *pBPType = BPT_NONE;

        // Check if the BPERESI_BPRESLOCATION flag is set in BPERESI_FIELDS.
        if (IsFlagSet(m_bpErrorResolutionInfo.dwFields, BPERESI_BPRESLOCATION))
        {
            // Set the new BP_TYPE.
            *pBPType = m_bpErrorResolutionInfo.bpResLocation.bpType;
            hr = S_OK;
        }
        else
        {
            hr = E_FAIL;
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Zobacz też
- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
