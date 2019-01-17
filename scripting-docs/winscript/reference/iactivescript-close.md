---
title: IActiveScript::Close | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Close
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Close
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 886ab1c4c39cf7c64571862bfd28f2fbd1062694
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348806"
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Powoduje, że aparat skryptów zrezygnowania z dowolnego aktualnie załadowanych skryptu, utraty stanu i zwolnij wszystkie wskaźniki interfejsu, które inne obiekty, w związku z tym wprowadzenie stanu zamkniętego. Obiekty sink zdarzenia, tekst skryptu natychmiast wykonane i wywołań makra, które są już w toku odbywa się przed zmianami stanu (Użyj [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) anulowania uruchomionego wątku skryptu). Ta metoda musi wywoływana przez tworzenie hostów, przed udostępnieniem interfejsu, aby uniknąć problemów z odwołanie cykliczne.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparat skryptów był już w stanie zamkniętym).|  
|`OLESCRIPT_S_PENDING`|Metoda zostało pomyślnie dodane do kolejki, ale nie zmienił się stan jeszcze. Podczas zmiany stanu, lokacja znajduje się nastąpi wywołanie zwrotne na [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) metody.|  
|`S_FALSE`|Wykonanie metody powiodło się, ale skrypt został już zamknięty.|  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript](../../winscript/reference/iactivescript.md)