---
title: Metoda IActiveScriptSiteUIControl::GetUIBehavior | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 9a944335-856a-4c6b-b2bc-8872542941b7
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b52c94e9c8b14218362000df401fba24568ea426
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097308"
---
# <a name="iactivescriptsiteuicontrolgetuibehavior-method"></a>Metoda IActiveScriptSiteUIControl::GetUIBehavior
Pobiera [wyliczenie SCRIPTUICHANDLING](../../winscript/reference/scriptuichandling-enumeration.md) reprezentujący sposób obsługi kontrolek interfejsu użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetUIBehavior(     [in] SCRIPTUICITEM UicItem,     [out] SCRIPTUICHANDLING * pUicHandling );   
```  
  
#### <a name="parameters"></a>Parametry  
 `UicItem`  
 Typ formantu.  
  
 `pUicHandling`  
 Sposób, który formant powinien zostać obsłużony.