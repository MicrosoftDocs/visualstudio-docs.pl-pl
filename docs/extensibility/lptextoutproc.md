---
title: LPTEXTOUTPROC, | Microsoft Docs
description: Dowiedz się więcej o wskaźniku funkcji LPTEXTOUTPROC. W Visual Studio IDE zaimplementowano funkcję do wyświetlania błędów i stanu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c313375efe8afd17dd5d76f55de4cdaf016bab40
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903102"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

Gdy użytkownik wykonuje operację kontroli źródła z wewnątrz zintegrowanego środowiska projektowego (IDE), wtyczka kontroli źródła może chcieć przekazać komunikaty o błędach lub stanie dotyczące operacji. Wtyczka może wyświetlać w tym celu własne pola komunikatów. Jednak w celu bardziej bezproblemowej integracji wtyczka może przekazywać ciągi do środowiska IDE, które następnie wyświetla je w natywny sposób wyświetlania informacji o stanie. Mechanizmem tego jest wskaźnik `LPTEXTOUTPROC` funkcji. Ide implementuje tę funkcję (opisaną bardziej szczegółowo poniżej) w celu wyświetlania błędów i stanu.

Ide przekazuje do wtyczki kontroli źródła wskaźnik funkcji do tej funkcji jako parametr podczas wywoływania `lpTextOutProc` [SccOpenProject](../extensibility/sccopenproject-function.md). Podczas operacji SCC, na przykład w trakcie wywołania [SccGet](../extensibility/sccget-function.md) obejmującego wiele plików, wtyczka może wywołać funkcję, okresowo przekazując ciągi do `LPTEXTOUTPROC` wyświetlenia. Ide może wyświetlać te ciągi na pasku stanu, w oknie danych wyjściowych lub w osobnym oknie komunikatu, zgodnie z potrzebami. Opcjonalnie w ide może być możliwe wyświetlanie niektórych komunikatów za pomocą **przycisku Anuluj.** Dzięki temu użytkownik może anulować operację i daje ideom IDE możliwość przekazania tych informacji z powrotem do wtyczki.

## <a name="signature"></a>Podpis
 Funkcja wyjściowa środowiska IDE ma następujący podpis:

```cpp
typedef LONG (*LPTEXTOUTPROC) (
   LPSTR display_string,
   LONG mesg_type
);
```

## <a name="parameters"></a>Parametry

display_string

Ciąg tekstowy do wyświetlenia. Ten ciąg nie powinien być zakończony ze zwrotem karetki ani w wierszu informacyjnym.

mesg_type

Typ komunikatu. W poniższej tabeli wymieniono obsługiwane wartości dla tego parametru.

|Wartość|Opis|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Komunikat jest uznawany za informacje, ostrzeżenie lub błąd.|
|`SCC_MSG_STATUS`|Komunikat zawiera stan i może być wyświetlany na pasku stanu.|
|`SCC_MSG_DOCANCEL`|Wysłane bez ciągu komunikatu.|
|`SCC_MSG_STARTCANCEL`|Rozpoczyna wyświetlanie **przycisku Anuluj.**|
|`SCC_MSG_STOPCANCEL`|Zatrzymuje wyświetlanie **przycisku Anuluj.**|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Pyta idee, czy operacja w tle ma zostać anulowana: ide zwraca wartość `SCC_MSG_RTN_CANCEL` , jeśli operacja została anulowana. W przeciwnym razie zwraca wartość `SCC_MSG_RTN_OK` . Parametr `display_string` jest rzutowany jako struktura [SccMsgDataIsCancelled,](#LinkSccMsgDataIsCancelled) która jest dostarczana przez wtyczkę kontroli źródła.|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Informuje ideę IDE o pliku przed pobraniem go z kontroli wersji. Parametr `display_string` jest rzutowany jako struktura [SccMsgDataOnBeforeGetFile,](#LinkSccMsgDataOnBeforeGetFile) która jest dostarczana przez wtyczkę kontroli źródła.|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Informuje ideę IDE o pliku po jego pobraniu z kontroli wersji. Parametr `display_string` jest rzutowany jako struktura [SccMsgDataOnAfterGetFile,](#LinkSccMsgDataOnAfterGetFile) która jest dostarczana przez wtyczkę kontroli źródła.|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Informuje ideę IDE o bieżącym stanie operacji w tle. Parametr `display_string` jest rzutowany jako [struktura SccMsgDataOnMessage,](#LinkSccMsgDataOnMessage) która jest dostarczana przez wtyczkę kontroli źródła.|

## <a name="return-value"></a>Wartość zwracana

|Wartość|Opis|
|-----------|-----------------|
|SCC_MSG_RTN_OK|Ciąg został wyświetlony lub operacja została zakończona pomyślnie.|
|SCC_MSG_RTN_CANCEL|Użytkownik chce anulować operację.|

## <a name="example"></a>Przykład
 Załóżmy, że idee wywołuje [rozszerzenie SccGet z](../extensibility/sccget-function.md) dwudziestoma nazwami plików. Wtyczka kontroli źródła chce uniemożliwić anulowanie operacji w trakcie operacji get pliku. Po otrzymaniu każdego pliku wywołuje on , przekazując informacje o stanie każdego pliku i wysyła komunikat, jeśli nie ma `lpTextOutProc` `SCC_MSG_DOCANCEL` on stanu do zgłoszenia. Jeśli w dowolnym momencie wtyczka otrzyma wartość zwracaną ze środowiska IDE, natychmiast anuluje operację pobierania, dzięki czemu nie są pobierane `SCC_MSG_RTN_CANCEL` żadne więcej plików.

## <a name="structures"></a>Struktury

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 Ta struktura jest wysyłana z `SCC_MSG_BACKGROUND_IS_CANCELLED` komunikatem. Służy do przekazywania identyfikatora anulowanej operacji w tle.

### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 Ta struktura jest wysyłana z `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` komunikatem. Służy do przekazywania nazwy pliku, który ma zostać pobrany, oraz identyfikatora operacji w tle wykonującej pobieranie.

### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 Ta struktura jest wysyłana z `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` komunikatem. Służy do przekazywania wyniku pobierania określonego pliku, a także identyfikatora operacji w tle, która wyniosła pobieranie. Zobacz wartości zwracane dla [SccGet,](../extensibility/sccget-function.md) aby uzyskać informacje o tym, co może zostać podane w wyniku.

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 Ta struktura jest wysyłana z `SCC_MSG_BACKGROUND_ON_MESSAGE` komunikatem. Służy do przekazywania bieżącego stanu operacji w tle. Stan jest wyrażony jako ciąg do wyświetlania przez ideę i wskazuje ważność komunikatu ( w przypadku komunikatu o błędzie; ostrzeżenia lub komunikatu `bIsError` `TRUE` `FALSE` informacyjnego). Podano również identyfikator operacji wysyłania stanu w tle.

## <a name="code-example"></a>Przykładowy kod
 Oto krótki przykład wywołania w celu wysłania komunikatu, pokazujący `LPTEXTOUTPROC` `SCC_MSG_BACKGROUND_ON_MESSAGE` sposób rzutowania struktury dla wywołania.

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
- [Funkcje wywołania zwrotnego implementowane przez ide](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
