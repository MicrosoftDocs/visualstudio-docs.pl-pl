---
title: 'IDebugProcessQueryProperties:: QueryProperties | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties::QueryProperties
ms.assetid: 976a9962-b689-45bb-afb6-16b2c5dbc3b8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3b7a1bb22b163c06b24db57b15824b82243af4b5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900161"
---
# <a name="idebugprocessquerypropertiesqueryproperties"></a>IDebugProcessQueryProperties::QueryProperties
Ta metoda wykonuje zapytanie dotyczące określonych wartości właściwości procesu debugowania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT QueryProperties(
   ULONG                  celt,
   PROCESS_PROPERTY_TYPE *rgdwPropTypes,
   VARIANT               *rgtPropValues);
```

```csharp
int QueryProperties(
   uint                       celt,
   enum_PROCESS_PROPERTY_TYPE rgdwPropTypes,
   out object[ ]              rgtPropValues);
```

## <a name="parameters"></a>Parametry
`celt`\
podczas Rozmiar tablic zawierających definicje właściwości i wartości właściwości.

`dwPropType`\
podczas Tablica zawierająca definicje właściwości zapytań. Możliwe wartości są następujące:

- PROCESS_PROPERTY_COMMAND_LINE = 1

- PROCESS_PROPERTY_CURRENT_DIRECTORY = 2

- PROCESS_PROPERTY_ENVIRONMENT_VARIABLES = 3

`pvarPropValue`\
określoną Tablica zawierająca wartości właściwości.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest rzadko używana.

## <a name="see-also"></a>Zobacz też
- [IDebugProcessQueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties.md)
