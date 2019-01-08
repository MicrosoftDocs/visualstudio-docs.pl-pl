---
title: IDebugExpressionContext::ParseLanguageText | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a55dc9ae2ae92a76c2b426d1f36949573b37a265
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087727"
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
 [in] Zawiera tekst, wyrażenia lub instrukcji.  
  
 `nRadix`  
 [in] Podstawy do użycia.  
  
 `pstrDelimiter`  
 [in] Ogranicznik końcowy z skrypt bloku. Gdy `pstrCode` jest analizowany ze strumienia tekstu, host zazwyczaj używa rozdzielnika, takiego jak dwa pojedyncze cudzysłowy ("), aby wykrywać koniec bloku skryptu. Ten parametr określa ogranicznik używany przez hosta, dzięki czemu silnik wykonywania skryptów zapewnić pierwotne przetwarzanie warunkowe (na przykład, zastępując pojedynczy znak cudzysłowu ['] dwoma pojedynczymi cudzysłowami do użytku w roli ogranicznika). Dokładnie jak (i czy) używa aparatu skryptów, te informacje zależy od silnika wykonywania skryptów. Ustaw ten parametr na `NULL` Jeśli host nie korzystał z ogranicznika do oznaczenia końca bloku skryptu.  
  
 `dwFlags`  
 [in] Kombinacja następujących flag tekstu debugowania:  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|Wskazuje, czy tekst jest wyrażeniem, w przeciwieństwie do instrukcji. Ta flaga może mieć wpływ na sposób, w którym tekst jest analizowany przy niektórych języków.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Jeśli wartość zwracana jest dostępna, będzie używany przez obiekt wywołujący.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Nie zezwalaj na efekty uboczne. Jeśli ta flaga jest ustawiona, obliczania wyrażenia powinien zmienić bez stanu środowiska uruchomieniowego.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Umożliwia użycie punktów przerwania podczas obliczania wartości tekstu. Jeśli ta flaga nie jest ustawiona punkty przerwania zostaną zignorowane podczas obliczania wartości tekstu.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Umożliwia raportów o błędach podczas obliczania wartości tekstu. Jeśli ta flaga nie jest ustawiona. następnie błędy nie są zgłaszane na hoście podczas obliczania.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Określa wyrażenie, które ma zostać obliczone dla kontekstu kodu, zamiast uruchamiać wyrażenia|  
  
 `ppe`  
 [out] Zwraca wyrażenie debugowania dla określonego tekstu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda tworzy wyrażenie debugowania dla określonego tekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugExpressionContext, interfejs](../../winscript/reference/idebugexpressioncontext-interface.md)