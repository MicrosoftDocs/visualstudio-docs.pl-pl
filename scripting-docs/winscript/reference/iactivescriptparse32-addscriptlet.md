---
title: IActiveScriptParse32::AddScriptlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fcf11eb2-8e71-4cca-afda-a91791c243ff
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: b5a680eea5f5695d3a7253b9cf722af6ebf537c6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089547"
---
# <a name="iactivescriptparse32addscriptlet"></a>IActiveScriptParse32::AddScriptlet
Dodaje skryptletu kodu do skryptu. Ta metoda jest używana w środowiskach, gdzie trwały stan skryptu jest sprzężony z dokumentem hosta, a host jest odpowiedzialny za Przywracanie skryptu, a nie za pomocą `IPersist*` interfejsu. Podstawowe przykłady są języków skryptów HTML, umożliwiające skryptlety kodu osadzane w dokumencie HTML do podłączenia do zdarzenia wewnętrzne (na przykład ONCLICK="button1.text='Exit" ").  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT AddScriptlet(  
    LPCOLESTR pstrDefaultName,       // address of default name of scriptlet  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    LPCOLESTR pstrSubItemName,       // address of subitem name  
    LPCOLESTR pstrEventName,         // address of event name  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    BSTR *pbstrName,                 // address of actual name of scriptlet  
    EXCEPINFO *pexcepinfo            // address of exception information  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrDefaultName`  
 [in] Adres domyślną nazwę do skojarzenia z scriptlet. Jeśli scriptlet nie zawiera informacje dotyczące nazewnictwa (tak jak w powyższym przykładzie ONCLICK), ta nazwa będzie służyć do identyfikowania scriptlet. Jeśli ten parametr jest `NULL`, aparat skryptów są produkowane unikatową nazwę, jeśli to konieczne.  
  
 `pstrCode`  
 [in] Adres tekstu scriptlet do dodania. Interpretacja tego ciągu zależy od języka skryptów.  
  
 `pstrItemName`  
 [in] Adres buforu, który zawiera nazwę elementu skojarzone z tym scriptlet. Ten parametr, oprócz `pstrSubItemName`, identyfikuje obiekt, dla którego scriptlet ma program obsługi zdarzeń.  
  
 `pstrSubItemName`  
 [in] Adres buforu, który zawiera nazwę `subobject` nazwanego elementu za pomocą którego ten scriptlet jest skojarzona; ta nazwa musi zostać znaleziony w informacje o typie nazwanego elementu. Ten parametr ma wartość NULL, jeśli scriptlet ma być skojarzona z nazwanego elementu zamiast `subitem`. Ten parametr, oprócz `pstrItemName`, identyfikuje określonego obiektu, dla którego scriptlet ma program obsługi zdarzeń.  
  
 `pstrEventName`  
 [in] Adres buforu, który zawiera nazwę zdarzenia, dla którego scriptlet ma program obsługi zdarzeń.  
  
 `pstrDelimiter`  
 [in] Adres ogranicznika końcowego scriptlet. Gdy `pstrCode` parametru jest analizowany ze strumienia tekstu, host zazwyczaj używa rozdzielnika, takiego jak dwa pojedyncze cudzysłowy ("), aby wykrywać koniec scriptletu. Ten parametr określa ogranicznik używany przez hosta, dzięki czemu silnik wykonywania skryptów zapewnić pierwotne przetwarzanie warunkowe (na przykład, zastępując pojedynczy znak cudzysłowu ['] dwoma pojedynczymi cudzysłowami do użytku w roli ogranicznika). Dokładnie jak (i czy) silnik wykonywania skryptów korzysta z tych informacji zależy od silnika wykonywania skryptów. Ustaw ten parametr na wartość NULL, jeśli host nie korzystał z ogranicznika do oznaczenia końca scriptlet.  
  
 `dwSourceContextCookie`  
 [in] Wartość zdefiniowanych przez aplikację, która jest używana na potrzeby debugowania.  
  
 `ulStartingLineNumber`  
 [in] Liczony od zera wartość, która określa, która linia będzie rozpoczynać analizę.  
  
 `dwFlags`  
 [in] Flagi skojarzone ze scriptlet. Może być kombinacją następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|Wskazuje, że tekst skryptu powinien być widoczny (i w związku z tym, możliwy do wywołania według nazwy) jako metoda globalna w przestrzeni nazw skryptu.|  
|SCRIPTTEXT_ISPERSISTENT|Wskazuje, że kod dodany podczas tego wywołania powinien zostać zapisany, jeśli silnik wykonywania skryptów jest zapisany (na przykład poprzez wywołanie `IPersist*::Save`), lub jeśli silnik wykonywania skryptów jest resetowany za pomocą przejścia z powrotem do stanu zainicjowania. Aby uzyskać więcej informacji o tym stanie Zobacz stany aparatu obsługi skryptów.|  
  
 `pbstrName` ,  
 [out] Rzeczywista nazwa używana do identyfikowania scriptlet. Należy go w kolejności preferencji: Nazwa jawnie określona w tekstu scriptlet, domyślną nazwą jest podawany `pstrDefaultName`, lub unikatową nazwę przekształcony przez silnik wykonywania skryptów.  
  
 `pexcepinfo` ,  
 [out] Adres struktury zawierającej informacje o wyjątku. Ta struktura powinno być wypełnione, jeśli zostanie zwrócony DISP_E_EXCEPTION.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`DISP_E_EXCEPTION`|Wystąpił wyjątek podczas analizowania scriptlet. `pexcepinfo` Parametr zawiera informacje o wyjątku.|  
|`E_INVALIDARG`|Argument ten był nieprawidłowy.|  
|`E_NOTIMPL`|Ta metoda nie jest obsługiwana; aparat skryptów nie obsługuje dodawania skryptlety wychwytywania zdarzeń.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparat skryptów jeszcze nie został załadowany lub zainicjowany) i w związku z tym nie powiodła się.|  
|`OLESCRIPT_E_INVALIDNAME`|Podana nazwa domyślna jest nieprawidłowy w tym języku skryptów.|  
|`OLESCRIPT_E_SYNTAX`|Wystąpił nieokreślony błąd składniowy w scriptlet.|  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)