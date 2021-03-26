---
description: Pobiera nazwę sesji debugowania tego procesu.
title: 'IDebugProcess2:: GetAttachedSessionName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 426904f777d65a25b92871767649cb26041e2af8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071548"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
Pobiera nazwę sesji debugowania tego procesu. IDE może wyświetlić te informacje dla użytkownika, który debuguje określony proces na konkretnym komputerze.

> [!NOTE]
> Ta metoda jest przestarzała i jej implementacja powinna zawsze zwrócić `E_NOTIMPL` .

## <a name="syntax"></a>Składnia

```
HRESULT GetAttachedSessionName(
   BSTR* pbstrSessionName
);
```

## <a name="parameters"></a>Parametry
`pbstrSessionName`\

## <a name="return-value"></a>Wartość zwracana
 Ta metoda powinna zawsze zwracać `E_NOTIMPL` .

## <a name="see-also"></a>Zobacz też
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
