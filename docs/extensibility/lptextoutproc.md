---
title: LPTEXTOUTPROC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 38c3e8263b9a30058c2de019e5e92160b716aa71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702790"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

Gdy użytkownik wykonuje operację kontroli źródła z wewnątrz zintegrowanego środowiska programistycznego (IDE), wtyczka do kontroli źródła może chcieć przekazać komunikaty o błędach lub stanie dotyczące operacji. Wtyczka może wyświetlać własne okna komunikatów do tego celu. Jednak w celu zapewnienia bardziej bezproblemowej integracji wtyczka może przekazywać ciągi do środowiska IDE, a następnie wyświetlać je w natywnym sposobie wyświetlania informacji o stanie. Mechanizmem tego jest `LPTEXTOUTPROC` wskaźnik funkcji. IDE implementuje tę funkcję (szczegółowo opisano poniżej) w celu wyświetlenia błędu i stanu.

IDE przechodzi do wtyczki kontroli źródła, która jest wskaźnikiem funkcji do tej funkcji, jako `lpTextOutProc` parametr podczas wywoływania [SccOpenProject](../extensibility/sccopenproject-function.md). Podczas operacji SCC, na przykład w trakcie wywołania [SccGet](../extensibility/sccget-function.md) obejmującego wiele plików, wtyczka może wywołać `LPTEXTOUTPROC` funkcję, okresowo przekazując ciągi do wyświetlenia. IDE może wyświetlać te ciągi na pasku stanu, w oknie danych wyjściowych lub w osobnym oknie komunikatu, zgodnie z potrzebami. Opcjonalnie IDE może być w stanie wyświetlić pewne komunikaty z przyciskiem **Anuluj** . Dzięki temu użytkownik może anulować operację i zapewnia IDE możliwość przekazania tych informacji z powrotem do wtyczki.

## <a name="signature"></a>Podpis
 Funkcja wyjściowa IDE ma następujący podpis:

```cpp
typedef LONG (*LPTEXTOUTPROC) (
   LPSTR display_string,
   LONG mesg_type
);
```

## <a name="parameters"></a>Parametry

display_string

Ciąg tekstowy do wyświetlenia. Ten ciąg nie powinien kończyć się znakiem powrotu karetki ani znakiem wysuwu wiersza.

mesg_type

Typ komunikatu. Poniższa tabela zawiera listę obsługiwanych wartości tego parametru.

|Wartość|Opis|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Komunikat jest traktowany jako informacja, ostrzeżenie lub błąd.|
|`SCC_MSG_STATUS`|Komunikat przedstawia stan i może być wyświetlany na pasku stanu.|
|`SCC_MSG_DOCANCEL`|Wysyłany bez ciągu komunikatu.|
|`SCC_MSG_STARTCANCEL`|Zaczyna wyświetlać przycisk **Anuluj** .|
|`SCC_MSG_STOPCANCEL`|Kończy wyświetlanie przycisku **Anuluj** .|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Pyta o środowisko IDE w przypadku anulowania operacji w tle: IDE zwraca `SCC_MSG_RTN_CANCEL` Jeśli operacja została anulowana; w przeciwnym razie zwraca wartość `SCC_MSG_RTN_OK` . `display_string`Parametr jest rzutowany jako struktura [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) , która jest dostarczana przez wtyczkę kontroli źródła.|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Informuje środowisko IDE o pliku przed jego pobraniem z kontroli wersji. `display_string`Parametr jest rzutowany jako struktura [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) , która jest dostarczana przez wtyczkę kontroli źródła.|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Informuje środowisko IDE o pliku po jego pobraniu z kontroli wersji. `display_string`Parametr jest rzutowany jako struktura [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) , która jest dostarczana przez wtyczkę kontroli źródła.|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Informuje IDE o bieżącym stanie operacji w tle. `display_string`Parametr jest rzutowany jako struktura [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) , która jest dostarczana przez wtyczkę kontroli źródła.|

## <a name="return-value"></a>Wartość zwracana

|Wartość|Opis|
|-----------|-----------------|
|SCC_MSG_RTN_OK|Ten ciąg został wyświetlony lub operacja została ukończona pomyślnie.|
|SCC_MSG_RTN_CANCEL|Użytkownik chce anulować operację.|

## <a name="example"></a>Przykład
 Załóżmy, że IDE wywołuje [SccGet](../extensibility/sccget-function.md) z dwudziestu nazw plików. Wtyczka do kontroli źródła chce uniemożliwić anulowanie operacji w trakcie pobierania pliku. Gdy pobierany jest każdy plik, wywołuje `lpTextOutProc` on informacje o stanie każdego pliku i wysyła komunikat, jeśli nie `SCC_MSG_DOCANCEL` ma stanu do raportowania. Jeśli w dowolnym momencie wtyczka otrzymuje wartość zwracaną z `SCC_MSG_RTN_CANCEL` IDE, natychmiast Anuluje operację pobierania, aby nie pobrano więcej plików.

## <a name="structures"></a>Struktury

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 Ta struktura jest wysyłana wraz z `SCC_MSG_BACKGROUND_IS_CANCELLED` wiadomością. Służy do przekazywania informacji o IDENTYFIKATORze operacji w tle, która została anulowana.

### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 Ta struktura jest wysyłana wraz z `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` wiadomością. Służy do przekazywania nazwy pliku do pobrania i identyfikatora operacji w tle, która wykonuje pobieranie.

### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 Ta struktura jest wysyłana wraz z `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` wiadomością. Służy do przekazywania wyniku pobrania określonego pliku, a także identyfikatora operacji w tle, która wykonała pobieranie. Zobacz wartości zwracane dla [SccGet](../extensibility/sccget-function.md) , co może być wyrażone jako wynik.

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 Ta struktura jest wysyłana wraz z `SCC_MSG_BACKGROUND_ON_MESSAGE` wiadomością. Służy do przekazywania bieżącego stanu operacji w tle. Stan jest wyrażony jako ciąg, który ma być wyświetlany przez IDE, i `bIsError` wskazuje ważność komunikatu ( `TRUE` dla komunikatu o błędzie; `FALSE` ostrzeżenie lub komunikat informacyjny). Zostanie również określony identyfikator operacji w tle wysyłającej stan.

## <a name="code-example"></a>Przykładowy kod
 Oto krótki przykład wywołania metody `LPTEXTOUTPROC` wysyłania `SCC_MSG_BACKGROUND_ON_MESSAGE` komunikatu, pokazujący, jak rzutować strukturę dla wywołania.

```cpp
LONG SendStatusMessage(
    LPTEXTOUTPROC pTextOutProc,
    DWORD         dwBackgroundID,
    LPCTSTR       pStatusMsg,
    BOOL          bIsError)
{
    SccMsgDataOnMessage msgData = { 0 };
    LONG                result  = 0;

    msgData.dwBackgroundOperationID = dwBackgroundID;
    msgData.szMessage               = pStatusMsg;
    msgData.bIsError                = bIsError;

    result = pTextOutProc(reinterpret_cast<LPCTSTR>(&msgData), SCC_MSG_BACKGROUND_ON_MESSAGE);
    return result;
}
```

## <a name="see-also"></a>Zobacz też
- [Funkcje wywołania zwrotnego zaimplementowane przez IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
