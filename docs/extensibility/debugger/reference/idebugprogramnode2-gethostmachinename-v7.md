---
title: IDebugProgramNode2::GetHostMachineName_V7 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b40d3350fb348afb654ae09785eb0956fb950bb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869854"
---
# <a name="idebugprogramnode2gethostmachinenamev7"></a>IDebugProgramNode2::GetHostMachineName_V7

> [!Note]
> PRZESTARZAŁE. NIE NALEŻY UŻYWAĆ.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetHostMachineName_V7 (
   BSTR* pbstrHostMachineName
);
```

```csharp
int GetHostMachineName_V7 (
   out string pbstrHostMachineName
);
```

#### <a name="parameters"></a>Parametry

`pbstrHostMachineName`

 [out] Zwraca nazwę komputera, w którym jest uruchomiony program.

## <a name="return-value"></a>Wartość zwracana

Implementacja zawsze powinna zwrócić `E_NOTIMPL`.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> Począwszy od programu Visual Studio 2005, ta metoda nie jest już używany i powinien zawsze zwracają `E_NOTIMPL`.

## <a name="see-also"></a>Zobacz też

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)