---
title: IActiveScriptSiteUIControl::GetUIBehavior Method | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 9a944335-856a-4c6b-b2bc-8872542941b7
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e3f6247afc70ef1197ea759ffdf475c2d6c0a0c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58158217"
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