---
title: IDebugCustomViewer::DisplayValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e711fc91a1d234957a136572cc4f5fddb9a47944
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54991090"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
Ta metoda jest wywoływana, aby wyświetlić określoną wartość.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `hwnd`  
 [in] Okno nadrzędne  
  
 `dwID`  
 [in] Identyfikator dla przeglądarek niestandardowych, które obsługują więcej niż jednego typu.  
  
 `pHostServices`  
 [in] Zastrzeżone. Zawsze ustawione na wartość null.  
  
 `pDebugProperty`  
 [in] Interfejs, który może służyć do pobierania wartości, które mają być wyświetlane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wyświetlanie ma "modal", ponieważ ta metoda będzie utworzenie niezbędnych okna, wyświetlić wartość, czeka na dane wejściowe i zamknij okno, wszystkie przed zwróceniem do obiektu wywołującego. Oznacza to, że metoda musi obsługiwać wszystkich aspektów wyświetlanie wartości właściwości, od tworzenia okna danych wyjściowych, trwa oczekiwanie na dane wejściowe użytkownika do niszczenie okna.  
  
 Do obsługi, zmieniając wartość na danej [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) obiektu, możesz użyć [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) metody — Jeśli wartość może być wyrażona jako ciąg. W przeciwnym razie jest niezbędne do tworzenia niestandardowego interfejsu — wyłącznie w ewaluatorze wyrażeń zaimplementowanie tego `DisplayValue` metody — w ten sam obiekt, który implementuje `IDebugProperty3` interfejsu. Ten niestandardowy interfejs musi dostarczać metody do zmieniania danych o dowolnym rozmiarze i poziomie złożoności.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)