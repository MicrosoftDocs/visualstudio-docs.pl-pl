---
description: Ta metoda jest wywoływana w celu wyświetlenia określonej wartości.
title: IDebugCustomViewer::D isplayValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 11a93ba7a3367a9ff61debfe338c349549ee429d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077580"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
Ta metoda jest wywoływana w celu wyświetlenia określonej wartości.

## <a name="syntax"></a>Składnia

```cpp
HRESULT DisplayValue(
   HWND             hwnd,
   DWORD            dwID,
   IUnknown *       pHostServices,
   IDebugProperty3* pDebugProperty);
);
```

```csharp
int DisplayValue(
   IntPtr          hwnd,
   uint            dwID,
   object          pHostServices,
   IDebugProperty3 pDebugProperty
);
```

## <a name="parameters"></a>Parametry
`hwnd`\
podczas Okno nadrzędne

`dwID`\
podczas Identyfikator dla podglądów niestandardowych, które obsługują więcej niż jeden typ.

`pHostServices`\
podczas Rezerwacj. Zawsze ustawiono wartość null.

`pDebugProperty`\
podczas Interfejs, którego można użyć do pobrania wartości do wyświetlenia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wyświetlanie jest "modalne" w tej metodzie, która spowoduje utworzenie niezbędnego okna, wyświetlenie wartości, oczekiwanie na dane wejściowe i zamknięcie okna, przed powrotem do obiektu wywołującego. Oznacza to, że metoda musi obsługiwać wszystkie aspekty wyświetlania wartości właściwości, od tworzenia okna dla danych wyjściowych, aby oczekiwać na dane wejściowe użytkownika w celu zniszczenia okna.

 Aby zapewnić obsługę zmiany wartości w danym obiekcie [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) , można użyć metody [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) — Jeśli wartość może być wyrażona jako ciąg. W przeciwnym razie konieczne jest utworzenie niestandardowego interfejsu — wyłącznie dla ewaluatora wyrażeń implementujących tę `DisplayValue` metodę — w tym samym obiekcie, który implementuje `IDebugProperty3` interfejs. Ten niestandardowy interfejs udostępnia metody zmiany danych o dowolnym rozmiarze lub złożoności.

## <a name="see-also"></a>Zobacz też
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)
