---
title: LPTEXTOUTPROC | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
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
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f14942ffd59ce2c6eacf7da2d0d1ab252d58e2cb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60100511"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gdy użytkownik wykonuje operacji kontroli źródła z wewnątrz zintegrowanego środowiska programistycznego (IDE), wtyczka do kontroli źródła może być błąd lub komunikatów o stanie dotyczące operacji przekazywania. Wtyczki można wyświetlać swój własny okien komunikatów w tym celu. Jednak aby uzyskać więcej bezproblemową integrację, dodatku typu plug-in można przekazać ciągów do środowiska IDE, następnie wyświetli je w swojej natywnej sposób wyświetlania informacji o stanie. Jest to mechanizm `LPTEXTOUTPROC` wskaźnika funkcji. IDE implementuje tej funkcji (opisane bardziej szczegółowo poniżej) do wyświetlania błędów i stanów.  
  
 IDE przekazuje do kontroli źródła wtyczek wskaźnika funkcji dotyczących wyłącznie tej funkcji jako `lpTextOutProc` podczas wywoływania parametru [SccOpenProject](../extensibility/sccopenproject-function.md). Podczas operacji SCC, na przykład w trakcie wywołania [SccGet](../extensibility/sccget-function.md) obejmujących wiele plików, wtyczka może wywołać `LPTEXTOUTPROC` funkcję, przekazując okresowo ciągów do wyświetlenia. IDE te ciągi mogą być wyświetlane na pasku stanu, w oknie danych wyjściowych lub w osobnym oknie komunikatu, zgodnie z potrzebami. Opcjonalnie, IDE może być możliwe wyświetlanie niektórych komunikatów za pomocą **anulować** przycisku. Dzięki temu użytkownikowi anulować operację i daje możliwość przekazywania tych informacji do wtyczki środowiska IDE.  
  
## <a name="signature"></a>Podpis  
 Funkcja ma następujący podpis wyjścia IDE:  
  
```cpp#  
typedef LONG (*LPTEXTOUTPROC) (  
   LPSTR display_string,  
   LONG mesg_type  
);  
```  
  
## <a name="parameters"></a>Parametry  
 display_string  
 Ciąg tekstowy do wyświetlenia. Ten ciąg nie powinno być zakończone znakiem karetki zwrotu lub wysuwu wiersza.  
  
 mesg_type  
 Typ komunikatu. W poniższej tabeli wymieniono obsługiwane wartości tego parametru.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Komunikat jest uznawany za informacje, ostrzeżenia lub błędu.|  
|`SCC_MSG_STATUS`|Komunikat informujący o stanie i może być wyświetlany na pasku stanu.|  
|`SCC_MSG_DOCANCEL`|Wysyłane z nie ciągu wiadomości.|  
|`SCC_MSG_STARTCANCEL`|Zaczyna się wyświetlanie **anulować** przycisku.|  
|`SCC_MSG_STOPCANCEL`|Zatrzymuje wyświetlanie **anulować** przycisku.|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Pyta IDE, czy można anulować operacji w tle: Zwraca IDE `SCC_MSG_RTN_CANCEL` Jeśli operacja została anulowana; w przeciwnym razie zwraca `SCC_MSG_RTN_OK`. `display_string` Parametru jest rzutowany jako [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) struktury, która jest dostarczana przez wtyczka do kontroli źródła.|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Informuje o pliku IDE, zanim zostaną pobrane z kontroli wersji. `display_string` Parametru jest rzutowany jako [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) struktury, która jest dostarczana przez wtyczka do kontroli źródła.|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Informuje o pliku IDE, po pobraniu go z kontroli wersji. `display_string` Parametru jest rzutowany jako [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) struktury, która jest dostarczana przez wtyczka do kontroli źródła.|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Informuje IDE bieżącego stanu operacji w tle. `display_string` Parametru jest rzutowany jako [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) struktury, która jest dostarczana przez wtyczka do kontroli źródła.|  
  
## <a name="return-value"></a>Wartość zwracana  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|Ten ciąg został wyświetlony lub operacja została ukończona pomyślnie.|  
|SCC_MSG_RTN_CANCEL|Użytkownik chce, aby anulować operację.|  
  
## <a name="example"></a>Przykład  
 Załóżmy, że wywołania IDE [SccGet](../extensibility/sccget-function.md) dwadzieścia nazwy pliku. Wtyczka do kontroli źródła chce uniemożliwić anulowanie operacji w trakcie pobierania plików. Po otrzymaniu każdego pliku, wywoływanych przez nią `lpTextOutProc`, a następnie przekazanie jej informacje o stanie dla każdego pliku i wysyła `SCC_MSG_DOCANCEL` komunikat, jeśli nie można raportować jej stanu. Jeśli w dowolnym momencie wtyczki odbiera wartość zwracaną `SCC_MSG_RTN_CANCEL` z poziomu środowiska IDE anuluje operację pobierania natychmiast, dzięki czemu nie ma więcej plików są pobierane.  
  
## <a name="structures"></a>Struktury  
  
### <a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 Ta struktura jest wysyłany z `SCC_MSG_BACKGROUND_IS_CANCELLED` wiadomości. Jest on używany do komunikowania się identyfikator operacji w tle, które zostało anulowane.  
  
### <a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 Ta struktura jest wysyłany z `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` wiadomości. Jest on używany do komunikowania się nazwę pliku do pobrania i Identyfikatorem operacji w tle, który wykonuje pobierania.  
  
### <a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 Ta struktura jest wysyłany z `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` wiadomości. Jest on używany do komunikowania się wynikiem pobieranie określonego pliku, a także identyfikator operacji w tle, czy podczas pobierania. Zobacz wartości zwracane dla [SccGet](../extensibility/sccget-function.md) dla co można podać w wyniku.  
  
### <a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage  
 [C++]  
  
```  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 Ta struktura jest wysyłany z `SCC_MSG_BACKGROUND_ON_MESSAGE` wiadomości. Jest on używany do komunikowania się bieżący stan operacji w tle. Stan jest wyrażona jako ciąg, który ma być wyświetlany w IDE, a `bIsError` wskazuje ważność wiadomości (`TRUE` komunikatu o błędzie; `FALSE` ostrzeżenie lub komunikat informacyjny). Identyfikator wysyłania stanu operacji w tle jest również podana.  
  
## <a name="code-example"></a>Przykład kodu  
 Poniżej przedstawiono krótki przykład wywołania metody `LPTEXTOUTPROC` wysyłać `SCC_MSG_BACKGROUND_ON_MESSAGE` wiadomości, przedstawiający sposób rzutowania struktury na wywołanie.  
  
```cpp#  
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
 [Funkcje wywołania zwrotnego implementowane przez środowisko IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
