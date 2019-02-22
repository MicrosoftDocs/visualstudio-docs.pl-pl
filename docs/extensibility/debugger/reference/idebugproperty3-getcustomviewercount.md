---
title: IDebugProperty3::GetCustomViewerCount | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerCount
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerCount
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4067fc314889e7aa991407c99ba949564b547087
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709151"
---
# <a name="idebugproperty3getcustomviewercount"></a>IDebugProperty3::GetCustomViewerCount
Pobiera liczbę przeglądarek niestandardowych, które mogą być dostępne dla tej właściwości.

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

#### <a name="parameters"></a>Parametry
`pcelt`

 [out] Liczba przeglądarek niestandardowych, które są dostępne dla tej właściwości.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Aby można było obsługiwać wizualizatorów typu, ta metoda przekazuje wywołanie do [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) metody. Jeśli Ewaluator wyrażeń również obsługuje przeglądarek niestandardowych dla tego typu właściwości, ta metoda dodaje numer przeglądarek niestandardowych do zwróconej wartości.

Aby uzyskać szczegółowe informacje na temat różnic między wizualizatorów typu i przeglądarek niestandardowych, zobacz [Wizualizator typów i Przeglądarka niestandardowa](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md).

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę, aby uzyskać **CProperty** obiekt ujawniający [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfejsu.

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
