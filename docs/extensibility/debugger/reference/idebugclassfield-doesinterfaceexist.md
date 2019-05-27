---
title: IDebugClassField::DoesInterfaceExist | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0aa0eb7ea97b93b4140feb44fb2b4f02d7500331
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203246"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
Określa, jeśli określony interfejs jest zdefiniowana w klasie.

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
[in] Ciąg zawierający nazwę interfejsu do wyszukania.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca wartość S_OK, zwraca wartość S_FALSE, jeśli nie ma interfejsu; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda obowiązuje pobiera wyliczenie wszystkich interfejsów i wyszukuje listę zgodnych interfejsu.

## <a name="see-also"></a>Zobacz także
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)