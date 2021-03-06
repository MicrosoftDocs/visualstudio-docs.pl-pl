---
description: Pobiera nazwę domyślnego indeksatora.
title: 'IDebugClassField:: GetDefaultIndexer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetDefaultIndexer
helpviewer_keywords:
- IDebugClassField::GetDefaultIndexer method
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8ce8a492ea4d45a54a295617d7863b0623fd6a87
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088552"
---
# <a name="idebugclassfieldgetdefaultindexer"></a>IDebugClassField::GetDefaultIndexer
Pobiera nazwę domyślnego indeksatora.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetDefaultIndexer( 
   BSTR* pbstrIndexer
);
```

```csharp
int GetDefaultIndexer(
   out string pbstrIndexer
);
```

## <a name="parameters"></a>Parametry
`pbstrIndexer` określoną Zwraca ciąg zawierający nazwę domyślnego indeksatora.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca S_OK lub zwraca S_FALSE, jeśli nie ma domyślnego indeksatora. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Domyślny indeksator klasy jest właściwością, która jest oznaczona jako `Default` Właściwość dla dostępu do tablicy. Jest to specyficzne dla programu [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] . Oto przykład domyślnego indeksatora zadeklarowanego w [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] i sposobu jego użycia.

```vb
Imports System.Collections;

Public Class Class1
    Private myList as Hashtable

    Default Public Property Item(ByVal Index As Integer) As Integer
        Get
            Return CType(List(Index), Integer)
        End Get
        Set(ByVal Value As Integer)
            List(Index) = Value
        End Set
    End Property
End Class

Function GetItem(Index as Integer) as Integer
    Dim classList as Class1 = new Class1
    Dim value as Integer

    ' Access array through default indexer
    value = classList(2)

    ' Access array through explicit property
    value = classList.Item(2)

    Return value
End Function
```

## <a name="see-also"></a>Zobacz też
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
