---
title: IDebugProgramNode2::GetProgramName | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetProgramName
helpviewer_keywords:
- IDebugProgramNode2::GetProgramName
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef32de11f1667e32684bf39e38f6b609fc67afa8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56714052"
---
# <a name="idebugprogramnode2getprogramname"></a>IDebugProgramNode2::GetProgramName
Pobiera nazwę programu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetProgramName (
    BSTR* pbstrProgramName
);
```

```csharp
int GetProgramName (
    out string pbstrProgramName
);
```

#### <a name="parameters"></a>Parametry
`pbstrProgramName`

 [out] Zwraca nazwę programu.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Nazwa programu nie jest tak samo jak ścieżka do programu, mimo że nazwę programu, może być częścią znajdzie takiej ścieżki.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę dla prostego `CProgram` obiekt, który implementuje [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interfejsu. `MakeBstr` Funkcja przydziela kopię określonego ciągu jako ciąg BSTR.

```cpp
HRESULT CProgram::GetProgramName(BSTR* pbstrProgramName) {
    if (!pbstrProgramName)
        return E_INVALIDARG;

    // Assign the member program name to the passed program name.
    *pbstrProgramName = MakeBstr(m_pszProgramName);
    return NOERROR;
}
```

## <a name="see-also"></a>Zobacz też
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
