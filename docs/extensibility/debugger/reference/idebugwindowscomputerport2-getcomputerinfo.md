---
description: Pobiera informacje o komputerze, na którym działa debuger.
title: 'IDebugWindowsComputerPort2:: GetComputerInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetComputerInfo
- IDebugWindowsComputerPort2::GetComputerInfo
ms.assetid: 654910b2-c239-44c8-92fc-317680a5672f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2afc91ee00137889a22763c024b10d5d7788d49c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083469"
---
# <a name="idebugwindowscomputerport2getcomputerinfo"></a>IDebugWindowsComputerPort2::GetComputerInfo
Pobiera informacje o komputerze, na którym działa debuger.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetComputerInfo(
   COMPUTER_INFO * pInfo
);
```

```csharp
public int GetComputerInfo(
   out COMPUTER_INFO[] pInfo
);
```

## <a name="parameters"></a>Parametry
`pInfo`\
określoną Odwołanie do struktury zawierającej informacje o komputerze.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)
- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md)
