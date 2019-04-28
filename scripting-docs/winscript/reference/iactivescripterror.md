---
title: IActiveScriptError | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptError interface
ms.assetid: c8e0288d-38ff-4145-a7e3-f8cdfb72eefe
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ca783e2100fe74ed05499f9611a9b8f3399817f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62954996"
---
# <a name="iactivescripterror"></a>IActiveScriptError
Obiekt implementującej interfejs ten jest przekazywany do [IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md) metody zawsze wtedy, gdy silnik wykonywania skryptów wystąpi nieobsługiwany błąd. Host następnie wywołuje metody dla tego obiektu w celu uzyskania informacji na temat błędu, który wystąpił.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptError::GetExceptionInfo](../../winscript/reference/iactivescripterror-getexceptioninfo.md)|Pobiera informacje o błędzie.|  
|[IActiveScriptError::GetSourcePosition](../../winscript/reference/iactivescripterror-getsourceposition.md)|Pobiera lokalizację w kodzie źródłowym, w której wystąpił błąd.|  
|[IActiveScriptError::GetSourceLineText](../../winscript/reference/iactivescripterror-getsourcelinetext.md)|Pobiera wiersz w pliku źródłowym, w którym wystąpił błąd.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy aktywnego skryptu](../../winscript/reference/active-script-interfaces.md)