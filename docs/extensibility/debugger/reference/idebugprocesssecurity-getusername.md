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
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 793a3072160230744ab66a5805cd99c24e20cb7c
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200451"
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