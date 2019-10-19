---
title: IDebugExpressionContext::P arseLanguageText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionContext.ParseLanguageText
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext::ParseLanguageText
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0493adde76e029088b637be3c6aaf02c55caaace
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573155"
---
# <a name="idebugexpressioncontextparselanguagetext"></a>IDebugExpressionContext::ParseLanguageText
Tworzy wyrażenie debugowania dla określonego tekstu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT ParseLanguageText(  
   LPCOLESTR           pstrCode,  
   UINT                nRadix,  
   LPCOLESTR           pstrDelimiter,  
   DWORD               dwFlags,  
   IDebugExpression**  ppe  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrCode`  
 podczas Zawiera tekst wyrażenia lub instrukcji.  
  
 `nRadix`  
 podczas Podstawy do użycia.  
  
 `pstrDelimiter`  
 podczas Ogranicznik blokowy końca skryptu. Gdy `pstrCode` jest analizowany ze strumienia tekstu, Host zwykle używa ogranicznika, takiego jak dwa znaki pojedynczego cudzysłowu (' '), w celu wykrycia końca bloku skryptu. Ten parametr określa ogranicznik używany przez hosta, który umożliwia aparatowi obsługi skryptów dostarczenie pewnych warunkowego przetwarzania wstępnego (na przykład zastępowanie pojedynczego cudzysłowu ['] dwoma pojedynczymi cudzysłowami do użycia jako ogranicznika). Dokładnie tak, jak (i jeśli) aparat skryptów używa tych informacji, zależy od aparatu skryptów. Ustaw ten parametr, aby `NULL`, Jeśli host nie używał ogranicznika do oznaczenia końca bloku skryptu.  
  
 `dwFlags`  
 podczas Kombinacja następujących flag tekstu debugowania:  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|Wskazuje, że tekst jest wyrażeniem, a nie instrukcją. Ta flaga może mieć wpływ na sposób analizowania tekstu przez niektóre języki.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Jeśli wartość zwracana jest dostępna, będzie używana przez wywołującego.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Nie Zezwalaj na skutki uboczne. Jeśli ta flaga jest ustawiona, obliczenie wyrażenia nie powinno zmienić stanu środowiska uruchomieniowego.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Umożliwia używanie punktów przerwania podczas obliczania tekstu. Jeśli ta flaga nie jest ustawiona, punkty przerwania są ignorowane podczas obliczania tekstu.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Umożliwia raportowanie błędów podczas obliczania tekstu. Jeśli ta flaga nie jest ustawiona, błędy nie są zgłaszane do hosta podczas obliczania.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Wskazuje, że wyrażenie ma być oceniane do kontekstu kodu, a nie do uruchomienia samego wyrażenia|  
  
 `ppe`  
 określoną Zwraca wyrażenie debugowania dla określonego tekstu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda tworzy wyrażenie debugowania dla określonego tekstu.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugExpressionContext, interfejs](../../winscript/reference/idebugexpressioncontext-interface.md)