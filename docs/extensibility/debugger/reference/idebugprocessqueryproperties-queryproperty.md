---
title: 'IDebugProcessQueryProperties:: QueryProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties::QueryProperty
ms.assetid: 9a91707d-a590-44ef-b122-69d9816a7a79
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b190d7ed1d3690be898334270bbd1d16584b81a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723298"
---
# <a name="idebugprocessquerypropertiesqueryproperty"></a>IDebugProcessQueryProperties::QueryProperty
Ta metoda wykonuje zapytanie dotyczące określonej wartości właściwości procesu debugowania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT QueryProperty(
   PROCESS_PROPERTY_TYPE  dwPropType,
   VARIANT               *pvarPropValue);
```

```csharp
int QueryProperty(
   enum_PROCESS_PROPERTY_TYPE dwPropType,
   out object                 pvarPropValue);
```

## <a name="parameters"></a>Parametry
`dwPropType`\
podczas Definicja właściwości, której dotyczy kwerenda. Potrzebne wartości:

- PROCESS_PROPERTY_COMMAND_LINE = 1

- PROCESS_PROPERTY_CURRENT_DIRECTORY = 2

- PROCESS_PROPERTY_ENVIRONMENT_VARIABLES = 3

`pvarPropValue`\
określoną Wartość właściwości.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest rzadko używana.

## <a name="see-also"></a>Zobacz też
- [IDebugProcessQueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties.md)
