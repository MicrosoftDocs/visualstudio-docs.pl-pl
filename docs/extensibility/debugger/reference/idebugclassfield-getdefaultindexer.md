---
title: IDebugClassField::GetDefaultIndexer | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetDefaultIndexer
helpviewer_keywords:
- IDebugClassField::GetDefaultIndexer method
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 95387f65382c970ec2e9847e95ff49e139cf69b8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350753"
---
# <a name="idebugclassfieldgetdefaultindexer"></a>IDebugClassField::GetDefaultIndexer
Pobiera nazwę indeksatora domyślne.

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
`pbstrIndexer` [out] Zwraca ciąg zawierający nazwę indeksatora domyślne.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca wartość S_OK lub zwraca wartość S_FALSE, jeśli Brak indeksatora domyślne. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Indeksator domyślnej klasy jest właściwość, która jest oznaczona jako `Default` właściwość uzyskuje dostęp do tablicy. Taka sytuacja dotyczy [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]. Poniżej przedstawiono przykładowy indeksator domyślnej zadeklarowanej w [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] i sposobie ich użycia.

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

## <a name="see-also"></a>Zobacz także
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)