---
title: 'IActiveScriptSiteWindow:: EnableModeless | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.EnableModeless
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_EnableModeless
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 756bda6209b6209ff14f6d67fef18faaed0b5618
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574127"
---
# <a name="iactivescriptsitewindowenablemodeless"></a>IActiveScriptSiteWindow::EnableModeless
Powoduje włączenie lub wyłączenie okna głównego oraz niemodalnych okien dialogowych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fEnable`  
 podczas Oflaguj, że jeśli `TRUE`, włącza okno główne i Niemodalne okna dialogowe lub, jeśli `FALSE`, wyłącza je.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`, jeśli się powiedzie, lub `E_FAIL` w przypadku wystąpienia błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest taka sama jak Metoda `IOleInPlaceFrame::EnableModeless`.  
  
 Wywołania tej metody mogą być zagnieżdżane.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)