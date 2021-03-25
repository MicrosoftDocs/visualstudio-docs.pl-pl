---
description: Określa, czy określony interfejs jest zdefiniowany w klasie.
title: IDebugClassField::D oesInterfaceExist | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 60a9a64e408f182476d6f34b19fea45f6fe8ad48
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085028"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
Określa, czy określony interfejs jest zdefiniowany w klasie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT DoesInterfaceExist( 
   LPCOLESTR pszInterfaceName
);
```

```csharp
int DoesInterfaceExist(
   [In] string pszInterfaceName
);
```

## <a name="parameters"></a>Parametry
`pszInterfaceName`\
podczas Ciąg zawierający nazwę interfejsu do wyszukania.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK, zwraca S_FALSE, jeśli interfejs nie istnieje; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda w efekcie Pobiera wyliczenie wszystkich interfejsów i przeszukuje listę pod kątem zgodnego interfejsu.

## <a name="see-also"></a>Zobacz też
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
