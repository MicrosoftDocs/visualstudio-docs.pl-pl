---
title: Interfejs IDispError | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDispError interface
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b717ebfe740a9b356513bb0f15e90c629a14e147
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345841"
---
# <a name="idisperror-interface"></a>Interfejs IDispError
Zawiera informacje o szczegółowy komunikat o błędzie kontekstowych.  
  
> [!NOTE]
>  Ten interfejs nie jest zaimplementowana.  
  
 Oprócz metod odziedziczone `IUnknown`, `IDispError` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|Pobiera informacje o błędzie określonego typu.|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|Pobiera następnych `IDispError` obiektu.|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|Pobiera kod błędu z `IDispError` obiektu.|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|Zwraca identyfikator programowy zależne od języka dla klasy lub aplikacji, który spowodował błąd.|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|Zwraca ścieżkę do pliku pomocy i identyfikator kontekstu tematu, który wyjaśni ten błąd, jeśli jest to możliwe.|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|Zwraca tekstowy opis błędu.|