---
title: Stałe DEBUG_TEXT | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: facbdc1258b3fca72a239d9d5cc41772cf577f13
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577371"
---
# <a name="debug_text-constants"></a>Stałe DEBUG_TEXT
Używane podczas [IDebugExpressionContext::P arselanguagetext](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>Stałe  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION DWORD|0x00000001|Wskazuje, że tekst jest wyrażeniem, a nie instrukcją. Ta flaga może mieć wpływ na sposób analizowania tekstu przez niektóre języki.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Jeśli wartość zwracana jest dostępna, będzie używana przez wywołującego.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Nie Zezwalaj na efekty uboczne. Jeśli ta flaga jest ustawiona, obliczenie wyrażenia nie powinno zmienić stanu środowiska uruchomieniowego.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Zezwalaj na punkty przerwania podczas obliczania tekstu. Jeśli ta flaga nie jest ustawiona, punkty przerwania zostaną zignorowane podczas obliczania tekstu.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Zezwalaj na raporty o błędach podczas obliczania tekstu. Jeśli ta flaga nie jest ustawiona, błędy nie będą raportowane dla hosta podczas obliczania.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Wskazuje, że wyrażenie ma być oceniane do kontekstu kodu, a nie do uruchomienia samego wyrażenia.|  
  
## <a name="see-also"></a>Zobacz także  
 [Stałe, wyliczenia i struktury debugera aktywnego skryptu](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)