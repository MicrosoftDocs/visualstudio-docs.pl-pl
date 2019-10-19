---
title: IActiveScriptParseProcedureOld::P arseProcedureText | Microsoft Docs
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
ms.openlocfilehash: 116cbc7fac0d53b55c9766945d56ecebd27b6785
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577451"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
Analizuje daną procedurę kodu i dodaje anonimową procedurę do przestrzeni nazw.  
  
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
 podczas Tekst procedury do obliczenia. Interpretacja tego ciągu zależy od języka skryptowego.  
  
 `pstrFormalParams`  
 podczas Formalne nazwy parametrów dla procedury. Nazwy parametrów muszą być oddzielone odpowiednimi ogranicznikami aparatu obsługi skryptów. Nazwy nie powinny być ujęte w nawiasy.  
  
 `pstrItemName`  
 podczas Nazwa nazwanego elementu, który zawiera kontekst, w którym ma zostać oceniona procedura. Jeśli ten parametr jest `NULL`, kod jest oceniany w kontekście globalnym aparatu skryptów.  
  
 `punkContext`  
 podczas Obiekt kontekstu. Ten obiekt jest zarezerwowany do użytku w środowisku debugowania, gdzie taki kontekst może być dostarczony przez debuger do reprezentowania aktywnego kontekstu czasu wykonywania. Jeśli ten parametr jest `NULL`, aparat używa `pstrItemName` do identyfikowania kontekstu.  
  
 `pstrDelimiter`  
 podczas Ogranicznik końca procedury. Gdy `pstrCode` jest analizowany ze strumienia tekstu, Host zwykle używa ogranicznika, takiego jak dwa znaki pojedynczego cudzysłowu (' '), w celu wykrycia końca procedury. Ten parametr określa ogranicznik używany przez hosta, co pozwala aparatowi skryptów zapewnić pewne warunkowe, pierwotne przetwarzanie wstępne (na przykład zastępowanie pojedynczego cudzysłowu ['] dwoma pojedynczymi cudzysłowami do użycia jako ogranicznika). Dokładnie tak, jak (i jeśli) aparat skryptów używa tych informacji, zależy od aparatu skryptów. Ustaw ten parametr, aby `NULL`, Jeśli host nie używał ogranicznika do oznaczenia końca procedury.  
  
 `dwSourceContextCookie`  
 podczas Wartość zdefiniowana przez aplikację, która jest używana na potrzeby debugowania.  
  
 `ulStartingLineNumber`  
 podczas Wartość zerowa, która określa, w którym wierszu rozpocznie się analizowanie.  
  
 `dwFlags`  
 podczas Flagi skojarzone z procedurą. Może być kombinacją tych wartości.  
  
|Stała|Wartość|Znaczenie|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|Wskazuje, że kod w `pstrCode` jest wyrażeniem, które reprezentuje wartość zwracaną przez procedurę.|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|Wskazuje, że w zakresie procedury znajduje się wskaźnik `this`.|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|Wskazuje, że elementy nadrzędne wskaźnika `this` są zawarte w zakresie procedury.|  
  
 `ppdisp`  
 określoną Zwraca otokę wysyłania, w której metoda domyślna jest procedurą przeanalizowana przez tę metodę.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_INVALIDARG`|Nieprawidłowy argument.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_NOTIMPL`|Ta metoda nie jest obsługiwana. Aparat skryptów nie obsługuje dodawania procedur do przestrzeni nazw w czasie wykonywania.|  
|`E_UNEXPECTED`|Wywołanie nie było oczekiwane (na przykład aparat skryptów jest w stanie niezainicjowanym lub zamkniętym).|  
|`OLESCRIPT_E_SYNTAX`|W procedurze Wystąpił nieokreślony błąd składniowy.|  
|`S_FALSE`|Aparat skryptów nie obsługuje obiektu wysyłania; `ppdisp`parameter jest ustawiona na `NULL`.|  
  
## <a name="remarks"></a>Uwagi  
 Kod skryptu nie jest oceniany podczas tego wywołania; Zamiast tego procedura została skompilowana do metody na `ppdisp`, gdzie może być wywoływana przez skrypt później.  
  
 Ten interfejs jest przestarzały na korzyść interfejsu `IActiveScriptParseProcedure`. Metoda `IActiveScriptParseProcedure::ParseProcedureText` jest podobna do tej metody, ale umożliwia określenie nazwy procedury. We wszystkich okolicznościach należy używać `IActiveScriptParseProcedure::ParseProcedureText`.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptParseProcedureOld   interfejsu](../../winscript/reference/iactivescriptparseprocedureold-interface.md)  
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)