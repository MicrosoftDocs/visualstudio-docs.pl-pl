---
title: LPTEXTOUTPROC | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702790"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

Gdy użytkownik wykonuje operację kontroli źródła z wewnątrz zintegrowanego środowiska programistycznego (IDE), wtyczka kontroli źródła może chcieć przekazać komunikaty o błędzie lub stanie związane z operacją. W tym celu wtyczka może wyświetlać własne pola komunikatów. Jednak dla bardziej bezproblemowej integracji, dodatek można przekazać ciągi do IDE, który następnie wyświetla je w jego macierzysty sposób wyświetlania informacji o stanie. Mechanizm do tego `LPTEXTOUTPROC` jest wskaźnik funkcji. IDE implementuje tę funkcję (opisaną bardziej szczegółowo poniżej) do wyświetlania błędów i stanu.

IDE przekazuje do wtyczki kontroli źródła wskaźnik funkcji do `lpTextOutProc` tej funkcji, jako parametr, podczas wywoływania [SccOpenProject](../extensibility/sccopenproject-function.md). Podczas operacji SCC, na przykład w środku wywołania [SccGet](../extensibility/sccget-function.md) obejmujące wiele plików, wtyczka może wywołać `LPTEXTOUTPROC` funkcję, okresowo przekazując ciągi do wyświetlenia. IDE może wyświetlać te ciągi na pasku stanu, w oknie danych wyjściowych lub w osobnym oknie komunikatu, odpowiednio. Opcjonalnie IDE może być w stanie wyświetlić niektóre komunikaty za pomocą przycisku **Anuluj.** Dzięki temu użytkownik może anulować operację i daje IDE możliwość przekazania tych informacji z powrotem do dodatku plug-in.

## <a name="signature"></a>Sygnatura
 Funkcja wyjściowa IDE ma następujący podpis:

```cpp
typedef LONG (*LPTEXTOUTPROC) (
   LPSTR display_string,
   LONG mesg_type
);
```

## <a name="parameters"></a>Parametry

display_string

Ciąg tekstowy do wyświetlenia. Ten ciąg nie powinien być zakończony z powrotem karetki lub posuwu wiersza.

mesg_type

Typ wiadomości. W poniższej tabeli wymieniono obsługiwane wartości tego parametru.

|Wartość|Opis|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Komunikat jest uważany za informacje, ostrzeżenie lub błąd.|
|`SCC_MSG_STATUS`|Komunikat pokazuje stan i może być wyświetlany na pasku stanu.|
|`SCC_MSG_DOCANCEL`|Wysyłane bez ciągu wiadomości.|
|`SCC_MSG_STARTCANCEL`|Rozpoczyna wyświetlanie przycisku **Anuluj.**|
|`SCC_MSG_STOPCANCEL`|Zatrzymuje wyświetlanie przycisku **Anuluj.**|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Pyta IDE, czy operacja w tle ma `SCC_MSG_RTN_CANCEL` zostać anulowana: IDE zwraca, jeśli operacja została anulowana; w przeciwnym `SCC_MSG_RTN_OK`razie zwraca plik . Parametr `display_string` jest rzutowany jako [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) struktury, która jest dostarczana przez wtyczkę kontroli źródła.|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Informuje IDE o pliku, zanim zostanie pobrany z kontroli wersji. Parametr `display_string` jest rzutowy jako [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) struktury, który jest dostarczany przez wtyczkę kontroli źródła.|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Informuje IDE o pliku po pobraniu z kontroli wersji. Parametr `display_string` jest rzutowy jako [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) struktury, który jest dostarczany przez wtyczkę kontroli źródła.|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Informuje IDE o bieżącym stanie operacji w tle. Parametr `display_string` jest rzutowy jako struktura [SccMsgDataOnMessage,](#LinkSccMsgDataOnMessage) która jest dostarczana przez wtyczkę formantu źródła.|

## <a name="return-value"></a>Wartość zwracana

|Wartość|Opis|
|-----------|-----------------|
|SCC_MSG_RTN_OK|Ciąg został wyświetlony lub operacja została ukończona pomyślnie.|
|SCC_MSG_RTN_CANCEL|Użytkownik chce anulować operację.|

## <a name="example"></a>Przykład
 Załóżmy, że IDE wywołuje [SccGet](../extensibility/sccget-function.md) z dwudziestu nazw plików. Wtyczka kontroli źródła chce zapobiec anulowaniu operacji w środku pliku. Po otrzymaniu każdego pliku `lpTextOutProc`wywołuje , przekazując go informacje o `SCC_MSG_DOCANCEL` stanie każdego pliku i wysyła wiadomość, jeśli nie ma stanu do raportu. Jeśli w dowolnym momencie dodatek otrzyma `SCC_MSG_RTN_CANCEL` wartość zwracaną z IDE, natychmiast anuluje operację get, dzięki czemu nie są pobierane żadne pliki.

## <a name="structures"></a>Struktury

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a>SccMsgDataIsCancelled

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 Ta struktura jest `SCC_MSG_BACKGROUND_IS_CANCELLED` wysyłana z wiadomością. Służy do przekazywania identyfikator operacji w tle, który został anulowany.

### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a>SccMsgDataOnBeforeGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 Ta struktura jest `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` wysyłana z wiadomością. Służy do przekazywania nazwy pliku, który ma zostać pobrany, oraz identyfikator operacji w tle, która wykonuje pobieranie.

### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a>SccMsgDataOnAfterGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 Ta struktura jest `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` wysyłana z wiadomością. Służy do komunikowania wynik pobierania określonego pliku, jak również identyfikator operacji w tle, który nie pobierania. Zobacz zwracane wartości [dla SccGet](../extensibility/sccget-function.md) dla tego, co można podać w wyniku.

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a>SccMsgDataOnMessage

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 Ta struktura jest `SCC_MSG_BACKGROUND_ON_MESSAGE` wysyłana z wiadomością. Służy do komunikowania bieżącego stanu operacji w tle. Stan jest wyrażony jako ciąg, który ma być `bIsError` wyświetlany przez IDE i`TRUE` wskazuje ważność wiadomości ( dla komunikatu o błędzie; `FALSE` ostrzeżenia lub komunikatu informacyjnego). Podano również identyfikator operacji w tle wysyłającej stan.

## <a name="code-example"></a>Przykładowy kod
 Oto krótki przykład wywołania, `LPTEXTOUTPROC` `SCC_MSG_BACKGROUND_ON_MESSAGE` aby wysłać wiadomość, pokazując, jak oddać strukturę dla połączenia.

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
