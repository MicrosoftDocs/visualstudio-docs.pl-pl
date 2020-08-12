---
title: IActiveScriptParse32::P arseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f33e454c-69d8-4cab-9150-d1e7fd04786d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9fd497dcda7e40cf0dbe6409193019ddae84c80b
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144405"
---
# <a name="iactivescriptparse32parsescripttext"></a>IActiveScriptParse32::ParseScriptText
Analizuje daną Scriptlet kodu, dodając deklaracje do przestrzeni nazw i oceniając kod zgodnie z potrzebami.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT ParseScriptText(  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // cookie for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    VARIANT *pvarResult,             // address of buffer for results  
    EXCEPINFO *pexcepinfo            // address of buffer for error data  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
| Parametr | Opis |  
|-|-|  
|`pstrCode`|podczas Adres tekstu Scriptlet do obliczenia. Interpretacja tego ciągu zależy od języka skryptowego.|  
|`pstrItemName`|podczas Adres nazwy elementu, który zawiera kontekst, w którym ma zostać obliczony Scriptlet. Jeśli ten parametr ma wartość NULL, kod jest oceniany w kontekście globalnym aparatu skryptów.|  
|`punkContext`|podczas Adres obiektu kontekstu. Ten obiekt jest zarezerwowany do użytku w środowisku debugowania, gdzie taki kontekst może być dostarczony przez debuger do reprezentowania aktywnego kontekstu czasu wykonywania. Jeśli ten parametr ma wartość NULL, aparat używa `pstrItemName` do identyfikowania kontekstu.|  
|`pstrDelimiter`|podczas Adres ogranicznika końca Scriptlet. Gdy `pstrCode` jest analizowany ze strumienia tekstu, Host zwykle używa ogranicznika, takiego jak dwa znaki pojedynczego cudzysłowu (' '), w celu wykrycia końca Scriptlet. Ten parametr określa ogranicznik używany przez hosta, który umożliwia aparatowi obsługi skryptów dostarczenie pewnych warunkowego przetwarzania wstępnego (na przykład zastępowanie pojedynczego cudzysłowu ['] dwoma pojedynczymi cudzysłowami do użycia jako ogranicznika). Dokładnie tak, jak (i jeśli) aparat skryptów używa tych informacji, zależy od aparatu skryptów. Ustaw ten parametr na `NULL` , Jeśli host nie używał ogranicznika do oznaczenia końca Scriptlet.|  
|`dwSourceContextCookie`|podczas Plik cookie używany do celów debugowania.|  
|`ulStartingLineNumber`|podczas Wartość zerowa, która określa, w którym wierszu rozpocznie się analizowanie.|  
|`dwFlags`|podczas Flagi skojarzone z Scriptlet. Może być kombinacją następujących wartości:|  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|Jeśli rozróżnienie między wyrażeniem obliczeniowym a instrukcją jest ważne, ale syntaktycznie niejednoznaczne w języku skryptu, ta flaga określa, że Scriptlet ma być interpretowana jako wyrażenie, a nie jako instrukcja lub Lista instrukcji. Domyślnie instrukcje są zakładane, chyba że odpowiedni wybór można ustalić na podstawie składni tekstu Scriptlet.|  
|SCRIPTTEXT_ISPERSISTENT|Wskazuje, że kod dodany podczas tego wywołania powinien zostać zapisany, jeśli aparat skryptów jest zapisywany (na przykład przez wywołanie do `IPersist*::Save` ) lub jeśli aparat skryptów jest resetowany w wyniku przejścia z powrotem do stanu zainicjowania.|  
|SCRIPTTEXT_ISVISIBLE|Wskazuje, że tekst skryptu powinien być widoczny (i w związku z tym wywoływany przez nazwę) jako metoda globalna w przestrzeni nazw skryptu.|  
  
| Parametr | Opis |  
|-|-|  
|`pvarResult`|określoną Adres buforu, który odbiera wyniki przetwarzania Scriptlet lub `NULL` Jeśli obiekt wywołujący oczekuje braku wyniku (to nie jest ustawienie wartości SCRIPTTEXT_ISEXPRESSIONej).|  
|`pexcepinfo`|określoną Adres struktury, która otrzymuje informacje o wyjątku. Ta struktura jest wypełniana, jeśli `IActiveScriptParse::ParseScriptText` zwraca DISP_E_EXCEPTION.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`DISP_E_EXCEPTION`|Wystąpił wyjątek podczas przetwarzania Scriptlet. `pexcepinfo`Parametr zawiera informacje o wyjątku.|  
|`E_INVALIDARG`|Nieprawidłowy argument.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_NOTIMPL`|Ta metoda nie jest obsługiwana. Aparat obsługi skryptów nie obsługuje oceny wyrażeń ani instrukcji w czasie wykonywania.|  
|`E_UNEXPECTED`|Wywołanie nie było oczekiwane (na przykład aparat skryptów jest w stanie niezainicjowanym lub zamkniętym albo ustawiono flagę SCRIPTTEXT_ISEXPRESSION i aparat skryptów jest w stanie zainicjowania).|  
|`OLESCRIPT_E_SYNTAX`|Wystąpił nieokreślony błąd składniowy w Scriptlet.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli aparat skryptów jest w stanie zainicjowania, żaden kod nie będzie oceniany w trakcie tego wywołania; Zamiast tego kod jest umieszczany w kolejce i wykonywany, gdy aparat wykonywania skryptów jest przenoszony do (lub przez) stan uruchomienia. Ponieważ wykonywanie nie jest dozwolone w stanie zainicjowania, jest to błąd wywołania tej metody z flagą SCRIPTTEXT_ISEXPRESSION, gdy stan jest zainicjowany.  
  
 Scriptlet może być wyrażeniem, listą instrukcji lub wszelkimi dozwolonymi przez język skryptów. Na przykład ta metoda jest używana w ocenie \<SCRIPT> znacznika HTML, który umożliwia wykonywanie instrukcji podczas konstruowania strony HTML, a nie tylko Kompilowanie ich do stanu skryptu.  
  
 Kod przesłany do tej metody musi być prawidłowym, kompletnym fragmentem kodu. Na przykład w języku VBScript nie jest dozwolone wywoływanie tej metody raz z funkcją sub (x), a następnie po raz drugi `End Sub` . Analizator nie może czekać na drugie wywołanie do wykonania procedury podrzędnej, ale raczej nie musi wygenerować błędu analizy, ponieważ deklaracja procedury podrzędnej została uruchomiona, ale nie została ukończona.  
  
 Więcej informacji o Stanach skryptów znajduje się w sekcji Stany aparatu skryptów w [aparatach skryptów systemu Windows](../../winscript/windows-script-engines.md).  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)