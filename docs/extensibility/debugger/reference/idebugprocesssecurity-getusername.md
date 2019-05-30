---
title: IDebugProcessSecurity::GetUserName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a42b67eb3fd308011bf725f8dd7e24a4d9ddca6f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311521"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Pobiera nazwę użytkownika z dostawcy portu.

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
[out] Ciąg zawierający nazwę użytkownika.

## <a name="return-value"></a>Wartość zwracana
 Jeśli metoda się powiedzie, zwraca `S_OK`. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 `GetUserName` Zwraca nazwę użytkownika, która jest wyświetlana w **nazwa_użytkownika** kolumny **dołączyć do procesu** okno dialogowe. Aby wyświetlić **dołączyć do procesu** okno dialogowe, kliknij przycisk **dołączyć do procesu** na **narzędzia** menu w [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE).

## <a name="see-also"></a>Zobacz także
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)