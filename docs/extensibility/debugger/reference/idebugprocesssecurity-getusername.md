---
title: IDebugProcessSecurity::GetUserName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f8340e9fd9e5f38963a9de78e2974404f600deef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917456"
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

#### <a name="parameters"></a>Parametry
 `pbstrUserName`

 [out] Ciąg zawierający nazwę użytkownika.

## <a name="return-value"></a>Wartość zwracana
 Jeśli metoda się powiedzie, zwraca `S_OK`. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 `GetUserName` Zwraca nazwę użytkownika, która jest wyświetlana w **nazwa_użytkownika** kolumny **dołączyć do procesu** okno dialogowe. Aby wyświetlić **dołączyć do procesu** okno dialogowe, kliknij przycisk **dołączyć do procesu** na **narzędzia** menu w [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE).

## <a name="see-also"></a>Zobacz też
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)