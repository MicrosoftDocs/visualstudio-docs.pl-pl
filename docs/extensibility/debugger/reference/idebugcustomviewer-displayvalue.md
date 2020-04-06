---
title: IDebugCustomViewer::DisplayValue | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32e444d0d6a30484f708d3001b95e7a71856edd5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732440"
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
[w] Okno nadrzędne

`dwID`\
[w] Identyfikator dla niestandardowych widzów obsługujących więcej niż jeden typ.

`pHostServices`\
[w] Zastrzeżone. Zawsze ustawiona na wartość null.

`pDebugProperty`\
[w] Interfejs, który może służyć do pobierania wartości, które mają być wyświetlane.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wyświetlacz jest "modalny", ponieważ ta metoda utworzy niezbędne okno, wyświetli wartość, czeka na dane wejściowe i zamknie okno, a wszystko to przed powrotem do wywołującego. Oznacza to, że metoda musi obsługiwać wszystkie aspekty wyświetlania wartości właściwości, od tworzenia okna dla danych wyjściowych, do oczekiwania na dane wejściowe użytkownika, do zniszczenia okna.

 Aby obsługiwać zmianę wartości na danym obiekcie [IDebugProperty3,](../../../extensibility/debugger/reference/idebugproperty3.md) można użyć [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) metody , jeśli wartość może być wyrażona jako ciąg. W przeciwnym razie konieczne jest utworzenie interfejsu niestandardowego — wyłącznego dla oceniającego wyrażenie implementującego tę `DisplayValue` metodę — na tym samym obiekcie, który implementuje `IDebugProperty3` interfejs. Ten interfejs niestandardowy dostarcza metod zmiany danych o dowolnym rozmiarze lub złożoności.

## <a name="see-also"></a>Zobacz też
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)
