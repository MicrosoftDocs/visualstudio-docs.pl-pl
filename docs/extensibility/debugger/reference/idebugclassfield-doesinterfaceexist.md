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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4248b653f5eea43a91d0c78a593431d53f5e68b8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173471"
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
