---
title: 'IDebugClassField:: GetDefaultIndexer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetDefaultIndexer
helpviewer_keywords:
- IDebugClassField::GetDefaultIndexer method
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 57e00107374485043af370967794bdade1c213d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734422"
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
