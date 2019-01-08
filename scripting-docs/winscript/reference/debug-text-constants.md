---
title: Stałe DEBUG_TEXT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64cd178dc997f30f7afbf80279dda42d3c1b7be4
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089352"
---
# <a name="debugtext-constants"></a>Stałe DEBUG_TEXT
Używany podczas [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>Stałe  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION TYPU DWORD.|0x00000001|Wskazuje, czy tekst jest wyrażeniem, w przeciwieństwie do instrukcji. Ta flaga może mieć wpływ na sposób, w którym tekst jest analizowany przy niektórych języków.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Jeśli wartość zwracana jest dostępna, będzie używany przez obiekt wywołujący.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Nie zezwalaj na efekty uboczne. Jeśli ta flaga jest ustawiona, obliczania wyrażenia powinien zmienić bez stanu środowiska uruchomieniowego.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Zezwalaj na punkty przerwania podczas obliczania wartości tekstu. Jeśli ta flaga nie jest ustawiona, punkty przerwania zostaną zignorowane podczas obliczania wartości tekstu.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Zezwalaj na raporty o błędach podczas obliczania wartości tekstu. Jeśli ta flaga nie jest ustawiona, następnie błędów nie jest informowany o hoście podczas obliczania.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Wskazuje, że wyrażenie jest oceniane kontekst kodu, zamiast uruchamiać wyrażenia.|  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe, wyliczenia i struktury debugera aktywnego skryptu](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)