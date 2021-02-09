---
title: 'IDebugProcessSecurity:: GetUserName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 075cc96866a2b7b4a987c04c6cb78dcd22da2b50
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912024"
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
