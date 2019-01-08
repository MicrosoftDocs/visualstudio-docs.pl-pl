---
title: IActiveScriptSiteWindow::EnableModeless | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4cea23890539ca80abf8e3e58b0f8c48b7ca1fc9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093018"
---
# <a name="iactivescriptsitewindowenablemodeless"></a>IActiveScriptSiteWindow::EnableModeless
Powoduje, że host włączyć lub wyłączyć wyświetleniem głównego okna, a także Niemodalne okna dialogowe.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fEnable`  
 [in] Flaga, jeśli `TRUE`, umożliwia Niemodalne okna dialogowe i okna głównego lub, jeśli `FALSE`, wyłącza je.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia lub `E_FAIL` Jeśli wystąpił błąd.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest taka sama jak `IOleInPlaceFrame::EnableModeless` metody.  
  
 Mogą być zagnieżdżone wywołania tej metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)