---
title: IActiveScriptParse::P arseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.ParseScriptText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_ParseScriptText
ms.assetid: 2d237d6c-cc65-415b-8808-72791304a136
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4f35b398a7348f4e2bdbaaa9ab3e322bf69ddb6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561625"
---
# <a name="iactivescriptparseparsescripttext"></a>IActiveScriptParse::ParseScriptText
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
  
|||  
|-|-|  
|`pstrCode`|podczas Adres tekstu Scriptlet do obliczenia. Interpretacja tego ciągu zależy od języka skryptowego.|  
|`pstrItemName`|podczas Adres nazwy elementu, który zawiera kontekst, w którym ma zostać obliczony Scriptlet. Jeśli ten parametr ma wartość NULL, kod jest oceniany w kontekście globalnym aparatu skryptów.|  
|`punkContext`|podczas Adres obiektu kontekstu. Ten obiekt jest zarezerwowany do użytku w środowisku debugowania, gdzie taki kontekst może być dostarczony przez debuger do reprezentowania aktywnego kontekstu czasu wykonywania. Jeśli ten parametr ma wartość NULL, aparat używa `pstrItemName` do identyfikowania kontekstu.|  
|`pstrDelimiter`|podczas Adres ogranicznika końca Scriptlet. Gdy `pstrCode` jest analizowany ze strumienia tekstu, Host zwykle używa ogranicznika, takiego jak dwa znaki pojedynczego cudzysłowu (' '), aby wykryć koniec Scriptlet. Ten parametr określa ogranicznik używany przez hosta, który umożliwia aparatowi obsługi skryptów dostarczenie pewnych warunkowego przetwarzania wstępnego (na przykład zastępowanie pojedynczego cudzysłowu ['] dwoma pojedynczymi cudzysłowami do użycia jako ogranicznika). Dokładnie tak, jak (i jeśli) aparat skryptów używa tych informacji, zależy od aparatu skryptów. Ustaw ten parametr, aby `NULL`, Jeśli host nie używał ogranicznika do oznaczenia końca Scriptlet.|  
|`dwSourceContextCookie`|podczas Plik cookie używany do celów debugowania.|  
|`ulStartingLineNumber`|podczas Wartość zerowa, która określa, w którym wierszu rozpocznie się analizowanie.|  
|`dwFlags`|podczas Flagi skojarzone z Scriptlet. Może być kombinacją następujących wartości:|  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|Jeśli rozróżnienie między wyrażeniem obliczeniowym a instrukcją jest ważne, ale syntaktycznie niejednoznaczne w języku skryptu, ta flaga określa, że Scriptlet ma być interpretowana jako wyrażenie, a nie jako instrukcja lub Lista instrukcji. Domyślnie instrukcje są zakładane, chyba że odpowiedni wybór można ustalić na podstawie składni tekstu Scriptlet.|  
|SCRIPTTEXT_ISPERSISTENT|Wskazuje, że kod dodany podczas tego wywołania powinien zostać zapisany, jeśli aparat skryptów jest zapisywany (na przykład przez wywołanie `IPersist*::Save`) lub jeśli aparat skryptów jest resetowany w wyniku przejścia z powrotem do stanu zainicjowania.|  
|SCRIPTTEXT_ISVISIBLE|Wskazuje, że tekst skryptu powinien być widoczny (i w związku z tym wywoływany przez nazwę) jako metoda globalna w przestrzeni nazw skryptu.|  
  
|||  
|-|-|  
|`pvarResult`|określoną Adres buforu, który odbiera wyniki przetwarzania Scriptlet lub `NULL`, jeśli obiekt wywołujący oczekuje braku wyniku (oznacza to, że wartość SCRIPTTEXT_ISEXPRESSION nie jest ustawiona).|  
|`pexcepinfo`|określoną Adres struktury, która otrzymuje informacje o wyjątku. Ta struktura jest wypełniana, jeśli `IActiveScriptParse::ParseScriptText` zwraca DISP_E_EXCEPTION.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Prawnego.|  
|`DISP_E_EXCEPTION`|Wystąpił wyjątek podczas przetwarzania Scriptlet. @No__t_0 parametr zawiera informacje o wyjątku.|  
|`E_INVALIDARG`|Nieprawidłowy argument.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_NOTIMPL`|Ta metoda nie jest obsługiwana. Aparat obsługi skryptów nie obsługuje oceny wyrażeń ani instrukcji w czasie wykonywania.|  
|`E_UNEXPECTED`|Wywołanie nie było oczekiwane (na przykład aparat skryptów jest w stanie niezainicjowanym lub zamkniętym albo ustawiono flagę SCRIPTTEXT_ISEXPRESSION, a aparat skryptów jest w stanie zainicjowania).|  
|`OLESCRIPT_E_SYNTAX`|Wystąpił nieokreślony błąd składniowy w Scriptlet.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli aparat skryptów jest w stanie zainicjowania, żaden kod nie będzie oceniany w trakcie tego wywołania; Zamiast tego kod jest umieszczany w kolejce i wykonywany, gdy aparat wykonywania skryptów jest przenoszony do (lub przez) stan uruchomienia. Ponieważ wykonywanie nie jest dozwolone w stanie zainicjowania, jest to błąd wywołania tej metody z flagą SCRIPTTEXT_ISEXPRESSION, gdy stan jest zainicjowany.  
  
 Scriptlet może być wyrażeniem, listą instrukcji lub wszelkimi dozwolonymi przez język skryptów. Na przykład ta metoda jest używana podczas obliczania znacznika > HTML \<SCRIPT, który umożliwia wykonywanie instrukcji, gdy jest tworzona strona HTML, a nie tylko kompiluje je do stanu skryptu.  
  
 Kod przesłany do tej metody musi być prawidłowym, kompletnym fragmentem kodu. Na przykład w języku VBScript nie jest dozwolone wywoływanie tej metody raz z funkcją sub (x), a następnie za drugim razem z `End Sub`. Analizator nie może czekać na drugie wywołanie do wykonania procedury podrzędnej, ale raczej nie musi wygenerować błędu analizy, ponieważ deklaracja procedury podrzędnej została uruchomiona, ale nie została ukończona.  
  
 Więcej informacji o Stanach skryptów znajduje się w sekcji Stany aparatu skryptów w [aparatach skryptów systemu Windows](../../winscript/windows-script-engines.md).  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)