---
title: IDebugProperty3::GetCustomViewerCount | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerCount
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerCount
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16cb623f58668362e5e308e1d66dfd6ca7c0fb8c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721184"
---
# <a name="idebugproperty3getcustomviewercount"></a>IDebugProperty3::GetCustomViewerCount
Pobiera liczbę niestandardowych widzów, które mogą być dostępne dla tej właściwości.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetCustomViewerCount(
    ULONG* pcelt
);
```

```csharp
int GetCustomViewerCount(
    out uint pcelt
);
```

## <a name="parameters"></a>Parametry
`pcelt`\
[na zewnątrz] Liczba niestandardowych widzów dostępnych dla tej usługi.

## <a name="return-value"></a>Wartość zwracana
Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Aby obsługiwać wizualizatorów typu, ta metoda przekazuje wywołanie [getCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) metody. Jeśli oceniający wyrażenie obsługuje również niestandardowe przeglądarki dla tego typu właściwości, ta metoda dodaje liczbę niestandardowych widzów do zwracanej wartości.

Aby uzyskać szczegółowe informacje na temat różnic między wizualizatorami typów a przeglądarkami niestandardowymi, zobacz [Typ wizualizatora i Podgląd niestandardowy](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md).

## <a name="example"></a>Przykład
W poniższym przykładzie pokazano, jak zaimplementować tę metodę dla **CProperty** obiektu, który udostępnia [interfejs IDebugProperty3.](../../../extensibility/debugger/reference/idebugproperty3.md)

```cpp
STDMETHODIMP CProperty::GetCustomViewerCount(ULONG* pcelt)
{
    if (pcelt == NULL)
    {
        return E_POINTER;
    }

    if (GetVisualizerService())
    {
        return m_pIEEVisualizerService->GetCustomViewerCount(pcelt);
    }
    else
    {
        return E_NOTIMPL;
    }
}
```

## <a name="see-also"></a>Zobacz też
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)
- [Wizualizator typów i przeglądarka niestandardowa](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
