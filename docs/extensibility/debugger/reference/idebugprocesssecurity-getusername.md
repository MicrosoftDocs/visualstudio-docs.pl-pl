---
title: 'IDebugProcessSecurity:: GetUserName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef00a0b7489c3e5cb709520546f3d3f26c8a4eba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723256"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Pobiera nazwę użytkownika z dostawcy portów.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetUserName(
    BSTR *pbstrUserName
);
```

```csharp
int GetUserName (
    string pbstrUserName
);
```

## <a name="parameters"></a>Parametry
`pbstrUserName`\
określoną Ciąg zawierający nazwę użytkownika.

## <a name="return-value"></a>Wartość zwracana
 Jeśli metoda się powiedzie, zwraca wartość `S_OK` . W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 `GetUserName` Zwraca nazwę użytkownika, która jest wyświetlana w kolumnie **Nazwa użytkownika** w oknie dialogowym **Dołącz do procesu** . Aby wyświetlić okno dialogowe **dołączanie do procesu** , kliknij przycisk **Dołącz do procesu** w menu **Narzędzia** w [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] zintegrowanym środowisku programistycznym (IDE).

## <a name="see-also"></a>Zobacz też
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
