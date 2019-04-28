---
title: IDebugClassField::GetDefaultIndexer | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetDefaultIndexer
helpviewer_keywords:
- IDebugClassField::GetDefaultIndexer method
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d884b8e066b539b925e50d4f49f65168ca6156c0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62922820"
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

#### <a name="parameters"></a>Parametry
 `pbstrIndexer`

 [out] Zwraca ciąg zawierający nazwę indeksatora domyślne.

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

## <a name="see-also"></a>Zobacz też
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)