---
title: Metoda IActiveScriptProfilerCallback3::SetWebWorkerId | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0798a23b4c8ad4e5859bec73ebfed47a56b322d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993106"
---
# <a name="iactivescriptprofilercallback3setwebworkerid-method"></a>Metoda IActiveScriptProfilerCallback3::SetWebWorkerId
Powiadamia program profilujący o identyfikatorze procesów roboczych dla tej sesji profilowania. Jeśli funkcja nie może być wykonane w kontekście strony, ta metoda nie jest wywoływana. Wartość `webWorkerId` przyrosty o 1 dla każdego procesu roboczego, zaczynając od 1. Identyfikator wartości nie są przeznaczone do być stabilna poza sesję, a odpowiadają ich kolejność, w której utworzono pracowników.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `webWorkerId`  
 Identyfikator pracownika w sieci web  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość zwracana przez tę metodę jest ignorowana przez silnik wykonywania skryptów.