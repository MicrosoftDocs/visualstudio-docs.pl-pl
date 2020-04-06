---
title: IDebugProgramNode2::GetHostMachineName_V7 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a8c328c83ebe52f842b1990debe07aed3fd764c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722084"
---
# <a name="idebugprogramnode2gethostmachinename_v7"></a>IDebugProgramNode2::GetHostMachineName_V7

> [!Note]
> Przestarzałe. NIE UŻYWAĆ.

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

## <a name="parameters"></a>Parametry

`pbstrHostMachineName`\
[na zewnątrz] Zwraca nazwę komputera, na którym jest uruchomiony program.

## <a name="return-value"></a>Wartość zwracana

Implementacja powinna `E_NOTIMPL`zawsze zwracać .

## <a name="remarks"></a>Uwagi

> [!WARNING]
> Od programu Visual Studio 2005 ta metoda nie `E_NOTIMPL`jest już używana i zawsze powinna zwracać .

## <a name="see-also"></a>Zobacz też

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
