---
title: IActiveScriptParse::ParseScriptText | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 8d88258a1bd16dba1de8d6ffa282f0f8ba409e2d
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088975"
---
# <a name="iactivescriptparseparsescripttext"></a>IActiveScriptParse::ParseScriptText
Analizuje danego skryptletu kodu, dodając deklaracje do przestrzeni nazw i oceniając kod, zgodnie z potrzebami.  
  
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
|`pstrCode`|[in] Adres tekstu scriptlet do oceny. Interpretacja tego ciągu zależy od języka skryptów.|  
|`pstrItemName`|[in] Adres nazwy elementu który podaje kontekst, w którym ma zostać obliczone scriptlet. Jeśli ten parametr ma wartość NULL, kod jest oceniany w kontekście globalnym silnika wykonywania skryptów.|  
|`punkContext`|[in] Adres obiektu kontekstu. Ten obiekt jest zarezerwowany do użytku w środowisku debugowania, gdzie taki kontekst może być świadczona przez debuger do reprezentowania aktywnego kontekstu wykonywania. Jeśli ten parametr ma wartość NULL, aparat używa parametru `pstrItemName` do zidentyfikowania kontekstu.|  
|`pstrDelimiter`|[in] Adres ogranicznika końcowego scriptlet. Gdy `pstrCode` jest analizowany ze strumienia tekstu, host zazwyczaj używa rozdzielnika, takiego jak dwa pojedyncze cudzysłowy ("), aby wykrywać koniec scriptletu. Ten parametr określa ogranicznik używany przez hosta, dzięki czemu silnik wykonywania skryptów zapewnić pierwotne przetwarzanie warunkowe (na przykład, zastępując pojedynczy znak cudzysłowu ['] dwoma pojedynczymi cudzysłowami do użytku w roli ogranicznika). Dokładnie jak (i czy) silnik wykonywania skryptów korzysta z tych informacji zależy od silnika wykonywania skryptów. Ustaw ten parametr na `NULL` Jeśli host nie korzystał z ogranicznika do oznaczenia końca scriptlet.|  
|`dwSourceContextCookie`|[in] Plik cookie używany do debugowania.|  
|`ulStartingLineNumber`|[in] Liczony od zera wartość, która określa, która linia będzie rozpoczynać analizę.|  
|`dwFlags`|[in] Flagi skojarzone ze scriptlet. Może być kombinacją tych wartości:|  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|Jeśli rozróżnienie między wyrażeniem obliczeniowe oraz instrukcji jest ważne, ale składniowo niejednoznaczne w języku skryptów, ta flaga Określa, że skryptlet ma być interpretowany jako wyrażenie, a nie jako instrukcja lub lista instrukcji. Domyślnie przyjęto instrukcje, chyba że odpowiedni wybór można ustalić na podstawie składni tekstu scriptlet.|  
|SCRIPTTEXT_ISPERSISTENT|Wskazuje, że kod dodany podczas tego wywołania powinien zostać zapisany, jeśli silnik wykonywania skryptów jest zapisany (na przykład poprzez wywołanie `IPersist*::Save`), lub jeśli silnik wykonywania skryptów jest resetowany za pomocą przejścia z powrotem do stanu zainicjowania.|  
|SCRIPTTEXT_ISVISIBLE|Wskazuje, że tekst skryptu powinien być widoczny (i w związku z tym, możliwy do wywołania według nazwy) jako metoda globalna w przestrzeni nazw skryptu.|  
  
|||  
|-|-|  
|`pvarResult`|[out] Adres buforu, który otrzymuje wyniki przetwarzania scriptlet lub `NULL` Jeśli wywołujący nie oczekuje żadnego wyniku (czyli wartość SCRIPTTEXT_ISEXPRESSION nie jest ustawiona).|  
|`pexcepinfo`|[out] Adres struktury, która otrzymuje informacje o wyjątku. Ta struktura jest wypełniana, jeśli `IActiveScriptParse::ParseScriptText` zwraca DISP_E_EXCEPTION.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`DISP_E_EXCEPTION`|Wystąpił wyjątek podczas przetwarzania scriptlet. `pexcepinfo` Parametr zawiera informacje o wyjątku.|  
|`E_INVALIDARG`|Argument ten był nieprawidłowy.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_NOTIMPL`|Ta metoda nie jest obsługiwana. Aparat skryptów nie obsługuje oceny wyrażeń lub instrukcji środowiska wykonawczego.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparat skryptów jest w stanie niezainicjowanym lub zamkniętym lub została ustawiona flaga SCRIPTTEXT_ISEXPRESSION i aparat skryptów znajduje się w stanie zainicjowanym).|  
|`OLESCRIPT_E_SYNTAX`|Wystąpił nieokreślony błąd składniowy w scriptlet.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli silnik wykonywania skryptów jest w stanie zainicjowania, żaden kod faktycznie nie będzie oceniany podczas tego wywołania; zamiast takiego kodu jest w kolejce i wykonywany, gdy silnik wykonywania skryptów jest przenoszone do (lub przez) stanu uruchomienia. Ponieważ wykonanie nie jest dozwolone w stanie zainicjowania, jest błędem jest wywołanie tej metody z flagą SCRIPTTEXT_ISEXPRESSION, gdy jest w stanie inicjowania.  
  
 Scriptlet może być wyrażeniem, listę instrukcji lub czymkolwiek dozwolonym przez język skryptów. Na przykład, ta metoda jest używana podczas obliczania elementu HTML \<SCRIPT > tag, który umożliwia instrukcji do wykonania, ponieważ ta strona jest generowana, a nie tylko wkompilowywanie ich w stan skryptu.  
  
 Kod przekazany do tej metody musi być pełną, prawidłową częścią kodu. Na przykład w języku VBScript jest niedozwolone wywołanie tej metody raz z Sub Function(x) i następnie po raz drugi z `End Sub`. Parser nie musi czekać na drugie wywołanie zakończyć podprocedurę, ale musi wygenerować błąd analizy, ponieważ deklarację podprocedury rozpoczęte, ale nie zakończona.  
  
 Aby uzyskać więcej informacji na temat stanów skryptów, zobacz sekcję stany aparatu obsługi skryptów [aparatów skryptów Windows](../../winscript/windows-script-engines.md).  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)