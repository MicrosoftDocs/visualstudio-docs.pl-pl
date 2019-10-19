---
title: 'IActiveScriptParse:: AddScriptlet | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_AddScriptlet
ms.assetid: 824929f4-4dd3-473a-92d9-0b96acea2f14
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c1b4ac460afea1efd538c64224d84afef49d1a67
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573536"
---
# <a name="iactivescriptparseaddscriptlet"></a>IActiveScriptParse::AddScriptlet
Dodaje kod Scriptlet do skryptu. Ta metoda jest używana w środowiskach, w których trwały stan skryptu jest intertwined z dokumentem hosta, a host jest odpowiedzialny za przywracanie skryptu, a nie za pomocą interfejsu `IPersist*`. Podstawowe przykłady to języki skryptów HTML, które zezwalają na skryptlety kodu osadzonego w dokumencie HTML do dołączenia do zdarzeń wewnętrznych (na przykład onkliknięciu = "Button1. text =" Exit "").  
  
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
 podczas Adres domyślnej nazwy do skojarzenia z Scriptlet. Jeśli Scriptlet nie zawiera informacji o nazewnictwie (jak w powyższym przykładzie onkliknij powyżej), ta nazwa będzie używana do identyfikowania Scriptlet. Jeśli ten parametr jest `NULL`, aparat skryptów produkuje unikatową nazwę, w razie potrzeby.  
  
 `pstrCode`  
 podczas Adres tekstu Scriptlet, który ma zostać dodany. Interpretacja tego ciągu zależy od języka skryptowego.  
  
 `pstrItemName`  
 podczas Adres buforu, który zawiera nazwę elementu skojarzoną z tym scriptletem. Ten parametr, oprócz `pstrSubItemName`, identyfikuje obiekt, dla którego Scriptlet jest programem obsługi zdarzeń.  
  
 `pstrSubItemName`  
 podczas Adres buforu, który zawiera nazwę `subobject` nazwanego elementu, z którym skojarzona jest ta Scriptlet; Ta nazwa musi być znaleziona w informacjach o typie nazwanego elementu. Ten parametr ma wartość NULL, jeśli Scriptlet ma być skojarzony z nazwanym elementem zamiast `subitem`. Ten parametr, oprócz `pstrItemName`, identyfikuje konkretny obiekt, dla którego Scriptlet jest programem obsługi zdarzeń.  
  
 `pstrEventName`  
 podczas Adres buforu, który zawiera nazwę zdarzenia, dla którego Scriptlet jest procedura obsługi zdarzeń.  
  
 `pstrDelimiter`  
 podczas Adres ogranicznika końca Scriptlet. Gdy parametr `pstrCode` jest analizowany ze strumienia tekstu, Host zwykle używa ogranicznika, takiego jak dwa znaki pojedynczego cudzysłowu (' '), aby wykryć koniec Scriptlet. Ten parametr określa ogranicznik używany przez hosta, który umożliwia aparatowi obsługi skryptów dostarczenie pewnych warunkowego przetwarzania wstępnego (na przykład zastępowanie pojedynczego cudzysłowu ['] dwoma pojedynczymi cudzysłowami do użycia jako ogranicznika). Dokładnie tak, jak (i jeśli) aparat skryptów używa tych informacji, zależy od aparatu skryptów. Ustaw ten parametr na wartość NULL, Jeśli host nie używał ogranicznika do oznaczenia końca Scriptlet.  
  
 `dwSourceContextCookie`  
 podczas Wartość zdefiniowana przez aplikację, która jest używana na potrzeby debugowania.  
  
 `ulStartingLineNumber`  
 podczas Wartość zerowa, która określa, w którym wierszu rozpocznie się analizowanie.  
  
 `dwFlags`  
 podczas Flagi skojarzone z Scriptlet. Może być kombinacją następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|Wskazuje, że tekst skryptu powinien być widoczny (i w związku z tym wywoływany przez nazwę) jako metoda globalna w przestrzeni nazw skryptu.|  
|SCRIPTTEXT_ISPERSISTENT|Wskazuje, że kod dodany podczas tego wywołania powinien zostać zapisany, jeśli aparat skryptów jest zapisywany (na przykład przez wywołanie `IPersist*::Save`) lub jeśli aparat skryptów jest resetowany w wyniku przejścia z powrotem do stanu zainicjowania. Aby uzyskać więcej informacji na temat tego stanu, zobacz Stany aparatu skryptów.|  
  
 `pbstrName`,  
 określoną Rzeczywista nazwa używana do identyfikowania Scriptlet. Jest to zgodne z preferencjami: Nazwa określona jawnie w tekście Scriptlet, nazwa domyślna podana w `pstrDefaultName` lub unikatowa nazwa, które są przekazywane przez aparat skryptów.  
  
 `pexcepinfo`,  
 określoną Adres struktury zawierającej informacje o wyjątku. Ta struktura powinna zostać wprowadzona, jeśli zostanie zwrócona wartość DISP_E_EXCEPTION.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Prawnego.|  
|`DISP_E_EXCEPTION`|Wystąpił wyjątek podczas analizowania Scriptlet. @No__t_0 parametr zawiera informacje o wyjątku.|  
|`E_INVALIDARG`|Nieprawidłowy argument.|  
|`E_NOTIMPL`|Ta metoda nie jest obsługiwana. aparat skryptów nie obsługuje dodawania skryptlety ujścia zdarzeń.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_UNEXPECTED`|Wywołanie nie było oczekiwane (na przykład aparat skryptów nie został jeszcze załadowany lub zainicjowany) i w związku z tym nie powiodło się.|  
|`OLESCRIPT_E_INVALIDNAME`|Podana nazwa domyślna jest nieprawidłowa w tym języku skryptowym.|  
|`OLESCRIPT_E_SYNTAX`|Wystąpił nieokreślony błąd składniowy w Scriptlet.|  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)