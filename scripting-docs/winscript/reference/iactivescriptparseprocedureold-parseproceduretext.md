---
title: IActiveScriptParseProcedureOld::ParseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld.ParseProcedureText
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld::ParseProcedureText
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e521bbdcd8d7397c1c2dfb377fd9b41811499f5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993218"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
Analizuje procedury danego kodu i dodaje procedurę anonimowych do przestrzeni nazw.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT ParseProcedureText(  
   LPCOLESTR    pstrCode,  
   LPCOLESTR    pstrFormalParams,  
   LPCOLESTR    pstrItemName,  
   IUnknown*    punkContext,  
   LPCOLESTR    pstrDelimiter,  
   DWORD_PTR    dwSourceContextCookie,  
   ULONG        ulStartingLineNumber,  
   DWORD        dwFlags,  
   IDispatch**  ppdisp  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrCode`  
 [in] Tekst procedury do oceny. Interpretacja tego ciągu zależy od języka skryptów.  
  
 `pstrFormalParams`  
 [in] Nazwy parametrów formalnych w procedurze. Nazwy parametrów muszą być oddzielone ogranicznikami odpowiednie dla silnika wykonywania skryptów. Nazwy nie powinna zostać ujęta w nawiasy.  
  
 `pstrItemName`  
 [in] Nazwa elementu o nazwie, który podaje kontekst, w którym ma zostać obliczone procedury. Jeśli ten parametr jest `NULL`, kod jest oceniany w kontekście globalnym silnika wykonywania skryptów.  
  
 `punkContext`  
 [in] Obiekt kontekstu. Ten obiekt jest zarezerwowany do użytku w środowisku debugowania, gdzie taki kontekst może być świadczona przez debuger do reprezentowania aktywnego kontekstu wykonywania. Jeśli ten parametr jest `NULL`, aparat używa parametru `pstrItemName` do zidentyfikowania kontekstu.  
  
 `pstrDelimiter`  
 [in] Ogranicznik końcowy wewnętrzny. Gdy `pstrCode` jest analizowany ze strumienia tekstu, host zazwyczaj używa rozdzielnika, takiego jak dwa pojedyncze cudzysłowy ("), aby wykrywać koniec procedury. Ten parametr określa ogranicznik używany przez hosta, dzięki czemu silnik wykonywania skryptów zapewnić niektóre warunkowe pierwotne przetwarzanie (na przykład, zastępując pojedynczy znak cudzysłowu ['] dwoma pojedynczymi cudzysłowami do użytku w roli ogranicznika). Dokładnie jak (i czy) używa aparatu skryptów, te informacje zależy od silnika wykonywania skryptów. Ustaw ten parametr na `NULL` Jeśli host nie korzystał z ogranicznika do oznaczenia końca procedury.  
  
 `dwSourceContextCookie`  
 [in] Wartość zdefiniowanych przez aplikację, która jest używana na potrzeby debugowania.  
  
 `ulStartingLineNumber`  
 [in] Liczony od zera wartość, która określa, na która linia będzie rozpoczynać analizę.  
  
 `dwFlags`  
 [in] Flagi skojarzone z tą procedurą. Może być kombinacją tych wartości.  
  
|Stała|Wartość|Znaczenie|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|Oznacza to, że kod w `pstrCode` jest wyrażeniem, która reprezentuje wartość zwracaną przez procedurę.|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|Oznacza to, że `this` wskaźnik myszy znajduje się w zakresie procedury.|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|Oznacza to, że nadrzędne `this` wskaźnika znajdują się w zakresie procedury.|  
  
 `ppdisp`  
 [out] Zwraca otoki wysyłki, w których domyślną metodą jest procedurą analizowane przez tę metodę.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_INVALIDARG`|Argument ten był nieprawidłowy.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_NOTIMPL`|Ta metoda nie jest obsługiwana. Aparat skryptów nie obsługuje dodawania czasu wykonywania procedur do przestrzeni nazw.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparat skryptów jest w stanie niezainicjowanym lub zamkniętym).|  
|`OLESCRIPT_E_SYNTAX`|Wystąpił nieokreślony błąd składniowy w procedurze.|  
|`S_FALSE`|Aparat skryptów nie obsługuje obiektu dispatch; `ppdisp`parametr ma wartość `NULL`.|  
  
## <a name="remarks"></a>Uwagi  
 Brak kodu skryptu jest oceniany podczas tego wywołania; Przeciwnie, procedura jest kompilowana do metody na `ppdisp` gdzie może być wywołany przez skrypt później.  
  
 Ten interfejs jest przestarzała zastąpiona ceną `IActiveScriptParseProcedure` interfejsu. `IActiveScriptParseProcedure::ParseProcedureText` Metoda jest podobna do tej metody, ale pozwala na podanie nazwy procedury. W każdych okolicznościach `IActiveScriptParseProcedure::ParseProcedureText` powinny być używane.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptParseProcedureOld Interface](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)