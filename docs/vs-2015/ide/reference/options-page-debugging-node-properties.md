---
title: Strona opcji, debugowanie właściwości węzła | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 564cc8b2-0084-420e-b560-200cc5621a7e
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 10537fb64e6ae0ebbe185024b76442704437e273
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668838"
---
# <a name="options-page-debugging-node-properties"></a>Strona opcji, debugowanie — Właściwości węzła
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W poniższych tabelach opisano strony (lub kolekcje właściwości), które są skojarzone z kategorią **debugowania** okna `DTE.Properties("Debugging", <Property Page>)` dialogowego **Opcje** .

## <a name="general"></a>Ogólne
 `DTE.Properties("Debugging", "General")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|PromptOnBreakpointDelete|Get/Set (wartość logiczna)|Określa, czy debuger będzie monitował o uprawnienia przed usunięciem wszystkich punktów przerwania w projekcie.|
|BreakAllProcesses|Get/Set (wartość logiczna)|Określa, czy debuger przerywa wszystkie procesy za każdym razem, gdy jeden proces zostanie przerwany.|
|BreakAtBoundaries|Get/Set (wartość logiczna)|Określa, czy debuger przerywa wykonywanie, gdy wyjątek przecina obramowanie między elementami AppDomain lub między kodem zarządzanym i natywnym.|
|EnableAddressLevelDebugging|Get/Set (wartość logiczna)|Określa, czy są włączone funkcje debugowania na poziomie adresu.|
|ShowDisassemblyIfNoSource|Get/Set (wartość logiczna)|Określa, czy debuger wyświetla kod demontażu, gdy kod źródłowy jest niedostępny.|
|EnableBreakpointFilters|Get/Set (wartość logiczna)|Określa, czy jest włączone filtrowanie punktów przerwania.|
|EnableExceptionAssistant|Get/Set (wartość logiczna)|Określa, czy Asystent wyjątków jest używany w przypadku wyjątków zarządzanych.|
|UnwindCallstack|Get/Set (wartość logiczna)|Określa, czy debuger rozwinięcia stosu wywołań dla nieobsługiwanego wyjątku.|
|EnableJustMyCode|Get/Set (wartość logiczna)|Określa, czy Tylko mój kod jest włączona dla języka C# i kodu Visual Basic.|
|ShowAllMembers|Get/Set (wartość logiczna)|W przypadku obiektów niebędących użytkownikami program określa, czy debuger ma wyświetlać wszystkie elementy członkowskie obiektów w oknach zmiennych. Ta opcja nie działa, chyba że Tylko mój kod jest włączona.|
|WarnIfNoUserCode|Get/Set (wartość logiczna)|Określa, czy debuger emituje ostrzeżenie, gdy użytkownik próbuje dołączyć do procesu, który nie ma kodu użytkownika. Ta opcja nie działa, chyba że Tylko mój kod jest włączona.|
|EnablePropertyEvaluation|Get/Set (wartość logiczna)|Określa, czy debuger automatycznie oblicza właściwości i niejawne wywołania funkcji w kodzie zarządzanym.|
|CallStringConversion|Get/Set (wartość logiczna)|Określa, czy debuger niejawnie wywołuje funkcję konwersji ciągów na obiektach w oknach zmiennych. Ta opcja dotyczy tylko kodu w języku C# i JScript.|
|EnableSourceServer|Get/Set (wartość logiczna)|Określa, czy debuger może uzyskać dostęp do kodu z serwera źródłowego.|
|PrintSourceServerDiagnostics|Get/Set (wartość logiczna)|Określa, czy w oknie danych wyjściowych są wyświetlane komunikaty diagnostyczne powiązane z serwerem źródłowym. Ta opcja nie działa, jeśli nie jest włączony dostęp do serwera źródłowego.|
|HighlightEntireLine|Get/Set (wartość logiczna)|Określa, czy debuger podświetla cały wiersz dla punktów przerwania i bieżącej instrukcji.|
|RequireSourceToMatch|Get/Set (wartość logiczna)|Określa, czy debuger wymaga, aby pliki źródłowe były dokładnie zgodne z oryginalną wersją podczas otwierania plików na potrzeby debugowania.|
|RedirectOutputToImmediate|Get/Set (wartość logiczna)|Określa, czy dane wyjściowe okna danych wyjściowych są przekierowywane do okna bezpośredniego.|
|ShowRawVariableStructure|Get/Set (wartość logiczna)|Określa, czy obiekty w oknach zmiennych są wyświetlane w postaci surowej.|
|SuppressJitOptimization|Get/Set (wartość logiczna)|Dla kodu zarządzanego, określa, czy Optymalizacja just in time jest pomijana przez debuger.|
|WarnIfNoSymbols|Get/Set (wartość logiczna)|Określa, czy debuger wyświetla ostrzeżenie, jeśli podczas uruchamiania procesu nie są dostępne żadne symbole debugowania.|
|WarnIfScriptDisabled|Get/Set (wartość logiczna)|Określa, czy debuger wyświetla ostrzeżenie, jeśli debugowanie skryptu nie jest włączone podczas uruchamiania procesu.|
|ShowMarkersForAllThreads|Get/Set (wartość logiczna)|Określa, czy debuger wyświetla znaczniki wątków.|
|StepOverPropertiesAndOperators|Get/Set (wartość logiczna)|Określa, czy należy przekroczyć właściwości i operatory tylko w kodzie zarządzanym.|

## <a name="edit-and-continue"></a>Edytuj i kontynuuj
 `DTE.Properties("Debugging", "EditAndContinue")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|EnableEditAndContinue|Get/Set (wartość logiczna)|Określa, czy funkcja Edytuj i Kontynuuj jest włączona. Ta opcja ma zastosowanie do wszystkich języków, które obsługują polecenie Edytuj i Kontynuuj.|
|InvokedByCommands|Get/Set (wartość logiczna)|Określa, czy opcja Edytuj i Kontynuuj automatycznie stosuje zmiany kodu, gdy użytkownik wybierze polecenie debugowania, takie jak **krok** lub **Kontynuuj**. Ta opcja ma zastosowanie tylko do kodu natywnego.|
|InvokedByCommandsAskFirst|Get/Set (wartość logiczna)|Określa, czy polecenie Edytuj i Kontynuuj monituje użytkownika o zgodę na zastosowanie zmian kodu, gdy użytkownik wybierze polecenia debugowania, takie jak **krok** lub **Kontynuuj**. Ta opcja ma zastosowanie tylko do kodu natywnego.|
|WarnAboutStaleCode|Get/Set (wartość logiczna)|Określa, czy debuger wyświetla komunikat ostrzegawczy, gdy polecenie Edytuj i Kontynuuj spowoduje wykonanie nieaktualnych lub przestarzałych kodów. Ta opcja ma zastosowanie tylko do kodu natywnego.|
|RelinkChangesOnStop|Pobierz/ustaw (krótki)|Określa, czy program Visual Studio ponownie łączy zmiany kodu zastosowane przez proces Edytuj i Kontynuuj w przypadku zatrzymania wykonywania aplikacji. Ta opcja ma zastosowanie tylko do kodu natywnego.|
|AllowPrecompiling|Pobierz/ustaw (krótki)|Określa, czy operacje Edytuj i Kontynuuj mogą ładować prekompilowane nagłówki w tle. Ta opcja ma zastosowanie tylko do kodu natywnego.|

## <a name="just-in-time"></a>just in time
 `DTE.Properties("Debugging", "JustInTime")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|JitManaged|Get/Set (wartość logiczna)|Określa, czy debugowanie just in time jest włączone dla kodu zarządzanego.|
|JitNative|Get/Set (wartość logiczna)|Określa, czy debugowanie just in time jest włączone dla kodu natywnego.|
|JitScript|Get/Set (wartość logiczna)|Określa, czy debugowanie just in time jest włączone dla kodu skryptu.|

## <a name="native"></a>Natywna
 `DTE.Properties("Debugging", "Native")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|LoadDllExports|Get/Set (wartość logiczna)|Określa, czy debuger ładuje tabele eksportu DLL.|
|EnableRPC|Get/Set (wartość logiczna)|Określa, czy debuger może przechodzić do zdalnych wywołań procedur COM.|

## <a name="see-also"></a>Zobacz też
 [Kontrolowanie ustawień opcji](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) [określających nazwy elementów właściwości na](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa) stronie Opcje strony opcji [, czcionki i kolory](../../ide/reference/options-page-fonts-and-colors-node-properties.md) [Strona Opcje właściwości węzła, Edytor tekstu właściwości węzła](../../ide/reference/options-page-text-editor-node-properties.md) [Ogólne, debugowanie, Opcje okno dialogowe](../../debugger/general-debugging-options-dialog-box.md) [Edycja i kontynuowanie, debugowanie, Opcje okno dialogowe](https://msdn.microsoft.com/library/009d225f-ef65-463f-a146-e4c518f86103) ( [just-in-Time), debugowanie, Opcje — okno dialogowe](../../debugger/just-in-time-debugging-options-dialog-box.md)
