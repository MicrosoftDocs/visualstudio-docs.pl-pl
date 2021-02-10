---
title: Pomocnicy zestawu SDK na potrzeby debugowania | Microsoft Docs
description: Więcej informacji na temat funkcji i deklaracji, które są globalnymi funkcjami pomocniczymi do implementowania aparatów debugowania, ocen wyrażeń i dostawców symboli w języku C++.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7b98914d4e7fc2d63fd6cc9f79789c389e19b784
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936005"
---
# <a name="sdk-helpers-for-debugging"></a>Pomocnicy zestawu SDK do debugowania
Te funkcje i deklaracje to globalne funkcje pomocnicze służące do implementowania aparatów debugowania, oceniania wyrażeń i dostawców symboli w języku C++.

> [!NOTE]
> W tej chwili nie ma żadnych zarządzanych wersji tych funkcji i deklaracji.

## <a name="overview"></a>Omówienie
 Aby można było używać aparatów debugowania, oceniania wyrażeń i dostawców symboli, które mają być używane przez program Visual Studio, muszą one być zarejestrowane. W tym celu należy skonfigurować podklucze i wpisy rejestru, w przeciwnym razie "Ustawianie metryk". Następujące funkcje globalne zostały zaprojektowane w celu uproszczenia procesu aktualizowania tych metryk. Zapoznaj się z sekcją w lokalizacji rejestru, aby dowiedzieć się, jak ustalić układ każdego podklucza rejestru, który został zaktualizowany przez te funkcje.

## <a name="general-metric-functions"></a>Ogólne funkcje metryk
 Są to ogólne funkcje używane przez aparaty debugowania. Wyspecjalizowane funkcje dla ocen wyrażeń i dostawców symboli są szczegółowo opisane w dalszej części.

### <a name="getmetric-method"></a>GetMetric — Metoda
 Pobiera wartość metryki z rejestru.

```cpp
HRESULT GetMetric(
   LPCWSTR pszMachine,
   LPCWSTR pszType,
   REFGUID guidSection,
   LPCWSTR pszMetric,
   DWORD * pdwValue,
   LPCWSTR pszAltRoot
);
```

|Parametr|Opis|
|---------------|-----------------|
|pszMachine|podczas Nazwa prawdopodobnie zdalnej maszyny, której rejestr zostanie zapisany ( `NULL` oznacza maszynę lokalną).|
|pszType|podczas Jeden z typów metryk.|
|guidSection|podczas Identyfikator GUID określonego aparatu, ewaluatora, wyjątek itd. Określa podsekcję w typie metryki dla określonego elementu.|
|pszMetric|podczas Metryka, która ma zostać uzyskana. Odpowiada to określonej nazwie wartości.|
|pdwValue|podczas Lokalizacja przechowywania wartości z metryki. Istnieje kilka rodzajów elementu GetMetric, które mogą zwracać dane typu DWORD (jak w tym przykładzie), BSTR, identyfikator GUID lub tablicę identyfikatorów GUID.|
|pszAltRoot|podczas Alternatywny katalog główny rejestru do użycia. Ustaw, aby `NULL` użyć wartości domyślnej.|

### <a name="setmetric-method"></a>SetMetric — Metoda
 Ustawia określoną wartość metryki w rejestrze.

```cpp
HRESULT SetMetric(
         LPCWSTR pszType,
         REFGUID guidSection,
         LPCWSTR pszMetric,
   const DWORD   dwValue,
         bool    fUserSpecific,
         LPCWSTR pszAltRoot
);
```

|Parametr|Opis|
|---------------|-----------------|
|pszType|podczas Jeden z typów metryk.|
|guidSection|podczas Identyfikator GUID określonego aparatu, ewaluatora, wyjątek itd. Określa podsekcję w typie metryki dla określonego elementu.|
|pszMetric|podczas Metryka, która ma zostać uzyskana. Odpowiada to określonej nazwie wartości.|
|dwValue|podczas Lokalizacja przechowywania wartości w metryce. Istnieje kilka typów właściwości SetMetric, które mogą przechowywać dane typu DWORD (w tym przykładzie), BSTR, identyfikator GUID lub tablicę identyfikatorów GUID.|
|fUserSpecific|podczas Ma wartość TRUE, jeśli Metryka jest specyficzna dla użytkownika i jeśli powinna być zapisywana w gałęzi użytkownika, a nie w gałęzi maszyny lokalnej.|
|pszAltRoot|podczas Alternatywny katalog główny rejestru do użycia. Ustaw, aby `NULL` użyć wartości domyślnej.|

### <a name="removemetric-method"></a>RemoveMetric, Metoda
 Usuwa określoną metrykę z rejestru.

```cpp
HRESULT RemoveMetric(
   LPCWSTR pszType,
   REFGUID guidSection,
   LPCWSTR pszMetric,
   LPCWSTR pszAltRoot
);
```

|Parametr|Opis|
|---------------|-----------------|
|pszType|podczas Jeden z typów metryk.|
|guidSection|podczas Identyfikator GUID określonego aparatu, ewaluatora, wyjątek itd. Określa podsekcję w typie metryki dla określonego elementu.|
|pszMetric|podczas Metryka, która ma zostać usunięta. Odpowiada to określonej nazwie wartości.|
|pszAltRoot|podczas Alternatywny katalog główny rejestru do użycia. Ustaw, aby `NULL` użyć wartości domyślnej.|

### <a name="enummetricsections-method"></a>EnumMetricSections, Metoda
 Wylicza różne sekcje metryk w rejestrze.

```cpp
HRESULT EnumMetricSections(
   LPCWSTR pszMachine,
   LPCWSTR pszType,
   GUID *  rgguidSections,
   DWORD * pdwSize,
   LPCWSTR pszAltRoot
);
```

|Parametr|Opis|
|---------------|-----------------|
|pszMachine|podczas Nazwa prawdopodobnie zdalnej maszyny, której rejestr zostanie zapisany ( `NULL` oznacza maszynę lokalną).|
|pszType|podczas Jeden z typów metryk.|
|rgguidSections|[in. out] Wstępnie przydzieloną tablicę identyfikatorów GUID do wypełnienia.|
|pdwSize|podczas Maksymalna liczba identyfikatorów GUID, które mogą być przechowywane w `rgguidSections` tablicy.|
|pszAltRoot|podczas Alternatywny katalog główny rejestru do użycia. Ustaw, aby `NULL` użyć wartości domyślnej.|

## <a name="expression-evaluator-functions"></a>Funkcje ewaluatora wyrażeń

|Funkcja|Opis|
|--------------|-----------------|
|GetEEMetric|Pobiera wartość metryki z rejestru.|
|SetEEMetric|Ustawia określoną wartość metryki w rejestrze.|
|RemoveEEMetric|Usuwa określoną metrykę z rejestru.|
|GetEEMetricFile|Pobiera nazwę pliku z określonej metryki i ładuje ją, zwracając zawartość pliku jako ciąg.|

## <a name="exception-functions"></a>Funkcje wyjątków

|Funkcja|Opis|
|--------------|-----------------|
|GetExceptionMetric|Pobiera wartość metryki z rejestru.|
|SetExceptionMetric|Ustawia określoną wartość metryki w rejestrze.|
|RemoveExceptionMetric|Usuwa określoną metrykę z rejestru.|
|RemoveAllExceptionMetrics|Usuwa wszystkie metryki wyjątków z rejestru.|

## <a name="symbol-provider-functions"></a>Funkcje dostawcy symboli

|Funkcja|Opis|
|--------------|-----------------|
|GetSPMetric|Pobiera wartość metryki z rejestru.|
|SetSPMetric|Ustawia określoną wartość metryki w rejestrze.|
|RemoveSPMetric|Usuwa określoną metrykę z rejestru.|

## <a name="enumeration-functions"></a>Funkcje wyliczania

|Funkcja|Opis|
|--------------|-----------------|
|EnumMetricSections|Wylicza wszystkie metryki dla określonego typu metryki.|
|EnumDebugEngine|Wylicza zarejestrowane aparaty debugowania.|
|EnumEEs|Wylicza zarejestrowane oceny wyrażeń.|
|EnumExceptionMetrics|Wylicza wszystkie metryki wyjątków.|

## <a name="metric-definitions"></a>Definicje metryk
 Definicje te mogą służyć do definiowania wstępnie zdefiniowanych nazw metryk. Nazwy odnoszą się do różnych kluczy rejestru i nazw wartości, a wszystkie są definiowane jako ciągi znaków dwubajtowych: na przykład `extern LPCWSTR metrictypeEngine` .

|Wstępnie zdefiniowane typy metryk|Opis: klucz podstawowy dla...|
|-----------------------------|---------------------------------------|
|metrictypeEngine|Wszystkie metryki aparatu debugowania.|
|metrictypePortSupplier|Wszystkie metryki dostawcy portów.|
|metrictypeException|Wszystkie metryki wyjątków.|
|metricttypeEEExtension|Wszystkie rozszerzenia ewaluatora wyrażeń.|

|Właściwości aparatu debugowania|Opis|
|-----------------------------|-----------------|
|metricAddressBP|Ustaw na wartość różną od zera, aby wskazać obsługę punktów przerwania adresu.|
|metricAlwaysLoadLocal|Ustaw na wartość różną od zera, aby zawsze ładować aparat debugowania lokalnie.|
|metricLoadInDebuggeeSession|nieużywane|
|metricLoadedByDebuggee|Ustaw na wartość różną od zera, aby wskazać, że aparat debugowania będzie zawsze ładowany z lub przez debugowany program.|
|metricAttach|Ustaw na wartość różną od zera, aby wskazać obsługę załączników do istniejących programów.|
|metricCallStackBP|Ustaw na wartość różną od zera, aby wskazać obsługę punktów przerwania stosu wywołań.|
|metricConditionalBP|Ustaw na wartość różną od zera, aby wskazać obsługę ustawienia punktów przerwania warunkowego.|
|metricDataBP|Ustaw na wartość różną od zera, aby wskazać obsługę ustawienia punktów przerwania na zmianach danych.|
|metricDisassembly|Ustaw na wartość różną od zera, aby wskazać obsługę produkcji listy deasemblera.|
|metricDumpWriting|Ustaw na wartość różną od zera, aby wskazać obsługę zapisu zrzutu (zrzucanie pamięci do urządzenia wyjściowego).|
|metricENC|Ustaw na wartość różną od zera, aby wskazać obsługę funkcji Edytuj i Kontynuuj. **Uwaga:**  Niestandardowy aparat debugowania nigdy nie powinien go ustawiać lub powinien być zawsze ustawiony na 0.|
|metricExceptions|Ustaw na wartość różną od zera, aby wskazać obsługę wyjątków.|
|metricFunctionBP|Ustaw na wartość różną od zera, aby wskazać obsługę nazwanych punktów przerwań (punkty przerwania, które są przerywane po wywołaniu określonej nazwy funkcji).|
|metricHitCountBP|Ustaw na wartość różną od zera, aby wskazać obsługę ustawienia punktów przerwania (punkty przerwania, które są wyzwalane tylko po osiągnięciu określonej liczby razy).|
|metricJITDebug|Ustaw na wartość różną od zera, aby wskazać obsługę debugowania just-in-Time (debuger jest uruchamiany, gdy wystąpi wyjątek w uruchomionym procesie).|
|metricMemory|nieużywane|
|metricPortSupplier|Ustaw tę wartość na identyfikator CLSID dostawcy portu, jeśli został zaimplementowany.|
|metricRegisters|nieużywane|
|metricSetNextStatement|Ustaw na wartość różną od zera, aby wskazać obsługę ustawiania następnej instrukcji (która pomija wykonywanie instrukcji pośrednich).|
|metricSuspendThread|Ustaw na wartość różną od zera, aby wskazać obsługę wstrzymania wykonywania wątku.|
|metricWarnIfNoSymbols|Ustaw wartość różną od zera, aby wskazać, że użytkownik powinien otrzymywać powiadomienia, jeśli nie ma żadnych symboli.|
|metricProgramProvider|Ustaw tę wartość na identyfikator CLSID dostawcy programu.|
|metricAlwaysLoadProgramProviderLocal|Ustaw tę wartość na wartość różną od zera, aby wskazać, że dostawca programu powinien być zawsze ładowany lokalnie.|
|metricEngineCanWatchProcess|Ustaw tę wartość na wartość różną od zera, aby wskazać, że aparat debugowania będzie obserwować zdarzenia procesu zamiast dostawcy programu.|
|metricRemoteDebugging|Ustaw tę wartość na wartość różną od zera, aby wskazać obsługę zdalnego debugowania.|
|metricEncUseNativeBuilder|Ustaw tę wartość na wartość różną od zera, aby wskazać, że Menedżer Edytuj i Kontynuuj powinien używać encbuild.dll aparatu debugowania do kompilowania w celu edytowania i kontynuowania. **Uwaga:**  Niestandardowy aparat debugowania nigdy nie powinien go ustawiać lub powinien być zawsze ustawiony na 0.|
|metricLoadUnderWOW64|Ustaw tę wartość na wartość różną od zera, aby wskazać, że silnik debugowania powinien zostać załadowany w procesie debugowanego obiektu na platformie WOW podczas debugowania procesu 64-bitowego; w przeciwnym razie aparat debugowania zostanie załadowany w procesie programu Visual Studio (uruchomionym w emulatorze WOW64).|
|metricLoadProgramProviderUnderWOW64|Ustaw tę wartość na wartość różną od zera, aby wskazać, że dostawca programu powinien zostać załadowany w procesie debugowanego obiektu podczas debugowania procesu 64-bitowego w ramach WOW; w przeciwnym razie zostanie załadowana w procesie programu Visual Studio.|
|metricStopOnExceptionCrossingManagedBoundary|Ustaw tę wartość na wartość różną od zera, aby wskazać, że proces ma zostać zatrzymany, jeśli wystąpił nieobsługiwany wyjątek między zarządzanymi i niezarządzanymi granicami kodu.|
|metricAutoSelectPriority|Ustaw ten element na priorytet automatycznego wyboru aparatu debugowania (wyższe wartości są równe wyższym priorytetem).|
|metricAutoSelectIncompatibleList|Klucz rejestru zawierający wpisy określające identyfikatory GUID dla aparatów debugowania do ignorowania w automatycznym zaznaczeniu. Te wpisy są liczbami (0, 1, 2 itd.) przy użyciu identyfikatora GUID wyrażonego jako ciąg.|
|metricIncompatibleList|Klucz rejestru zawierający wpisy określające identyfikatory GUID dla aparatów debugowania, które są niezgodne z tym aparatem debugowania.|
|metricDisableJITOptimization|Ustaw tę wartość na wartość różną od zera, aby wskazać, że optymalizacje just in Time (dla kodu zarządzanego) powinny być wyłączone podczas debugowania.|

|Właściwości ewaluatora wyrażeń|Opis|
|-------------------------------------|-----------------|
|metricEngine|Obejmuje to liczbę aparatów debugowania, które obsługują określoną ewaluatora wyrażeń.|
|metricPreloadModules|Ustaw tę wartość na wartość różną od zera, aby wskazać, że moduły mają być wstępnie załadowane, gdy zostanie uruchomiona ewaluatora wyrażeń dla programu.|
|metricThisObjectName|Ustaw tę wartość na nazwę obiektu "This".|

|Właściwości rozszerzenia ewaluatora wyrażeń|Opis|
| - |-----------------|
|metricExtensionDll|Nazwa biblioteki DLL, która obsługuje to rozszerzenie.|
|metricExtensionRegistersSupported|Lista obsługiwanych rejestrów.|
|metricExtensionRegistersEntryPoint|Punkt wejścia do uzyskiwania dostępu do rejestrów.|
|metricExtensionTypesSupported|Lista obsługiwanych typów.|
|metricExtensionTypesEntryPoint|Punkt wejścia do uzyskiwania dostępu do typów.|

|Właściwości dostawcy portów|Opis|
|------------------------------|-----------------|
|metricPortPickerCLSID|Identyfikator CLSID selektora portów (okno dialogowe, którego użytkownik może użyć do wybrania portów i dodania portów do użycia na potrzeby debugowania).|
|metricDisallowUserEnteredPorts|Niezerowe, jeśli nie można dodać portów wprowadzonych przez użytkownika do dostawcy portów (powoduje to, że okno dialogowe selektora portów jest zasadniczo tylko do odczytu).|
|metricPidBase|Identyfikator procesu podstawowego używany przez dostawcę portu podczas alokowania identyfikatorów procesów.|

|Wstępnie zdefiniowane typy sklepu SP|Opis|
|-------------------------------|-----------------|
|storetypeFile|Symbole są przechowywane w oddzielnym pliku.|
|storetypeMetadata|Symbole są przechowywane jako metadane w zestawie.|

|Różne właściwości|Opis|
|------------------------------|-----------------|
|metricShowNonUserCode|Ustaw na wartość różną od zera, aby pokazać kod nieużytkownika.|
|metricJustMyCodeStepping|Ustaw tę wartość na wartość różną od zera, aby wskazać, że krokowe może wystąpić tylko w kodzie użytkownika.|
|metricCLSID|Identyfikator CLSID dla obiektu określonego typu metryki.|
|metricName|Przyjazna dla użytkownika nazwa obiektu określonego typu metryki.|
|metricLanguage|Nazwa języka.|

## <a name="registry-locations"></a>Lokalizacje w rejestrze
 Metryki są odczytywane i zapisywane w rejestrze, w odróżnieniu od `VisualStudio` podklucza.

> [!NOTE]
> W większości przypadków metryki będą zapisywane w kluczu HKEY_LOCAL_MACHINE. Jednak czasami HKEY_CURRENT_USER będzie kluczem docelowym. Dbgmetric. lib obsługuje oba klucze. Podczas pobierania metryki wyszukuje HKEY_CURRENT_USER najpierw, a następnie HKEY_LOCAL_MACHINE. Podczas ustawiania metryki parametr określa klucz najwyższego poziomu, który ma być używany.

 *[klucz rejestru]*\

 `Software`\

 `Microsoft`\

 `VisualStudio`\

 *[wersja główna]*\

 *[główny Metryka]*\

 *[typ metryki]*\

 *[Metryka] = [wartość metryki]*

 *[Metryka] = [wartość metryki]*

 *[Metryka] = [wartość metryki]*

|Symbol zastępczy|Opis|
|-----------------|-----------------|
|*[klucz rejestru]*|`HKEY_CURRENT_USER` lub `HKEY_LOCAL_MACHINE`.|
|*[wersja główna]*|Wersja programu Visual Studio (na przykład,, `7.0` `7.1` lub `8.0` ). Jednak ten katalog główny można także zmodyfikować przy użyciu przełącznika **/rootsuffix** , aby **devenv.exe**. W przypadku VSIP ten modyfikator zazwyczaj jest przypadany, więc wersja główna powinna mieć **wartość, na** przykład 8.0 EXP.|
|*[główny Metryka]*|Jest to albo `AD7Metrics` lub `AD7Metrics(Debug)` , w zależności od tego, czy jest używana wersja debugowana dbgmetric. lib. **Uwaga:**  Niezależnie od tego, czy dbgmetric. lib jest używana, Konwencja nazewnictwa powinna być przestrzegana w przypadku różnic między wersjami Debug i Release, które muszą być odzwierciedlone w rejestrze.|
|*[typ metryki]*|Typ metryki do zapisania: `Engine` , `ExpressionEvaluator` , `SymbolProvider` itp. Wszystkie te dane są zdefiniowane jako w dbgmetric. h jako `metricTypeXXXX` , gdzie `XXXX` jest nazwą określonego typu.|
|*metryki*|Nazwa wpisu, do którego ma zostać przypisana wartość w celu ustawienia metryki. Rzeczywista organizacja metryk zależy od typu metryki.|
|*[wartość metryki]*|Wartość przypisana do metryki. Typ, który powinien mieć wartość (ciąg, liczba itp.) zależy od metryki.|

> [!NOTE]
> Wszystkie identyfikatory GUID są przechowywane w formacie `{GUID}` . Na przykład `{123D150B-FA18-461C-B218-45B3E4589F9B}`.

### <a name="debug-engines"></a>Aparaty debugowania
 Oto organizacja metryk aparatów debugowania w rejestrze. `Engine` jest nazwą typu metryki dla aparatu debugowania i odpowiada *[typ metryki]* w powyższym poddrzewie rejestru.

 `Engine`\

 *[identyfikator GUID aparatu]*\

 `CLSID` = *[identyfikator GUID klasy]*

 *[Metryka] = [wartość metryki]*

 *[Metryka] = [wartość metryki]*

 *[Metryka] = [wartość metryki]*

 `PortSupplier`\

 `0` = *[identyfikator GUID dostawcy portu]*

 `1` = *[identyfikator GUID dostawcy portu]*

|Symbol zastępczy|Opis|
|-----------------|-----------------|
|*[identyfikator GUID aparatu]*|Identyfikator GUID aparatu debugowania.|
|*[identyfikator GUID klasy]*|Identyfikator GUID klasy implementującej ten aparat debugowania.|
|*[identyfikator GUID dostawcy portu]*|Identyfikator GUID dostawcy portu (jeśli istnieje). Wiele aparatów debugowania korzysta z domyślnego dostawcy portów i w związku z tym nie należy określać własnego dostawcy. W takim przypadku podklucz `PortSupplier` będzie nieobecny.|

### <a name="port-suppliers"></a>Dostawcy portów
 Poniżej znajduje się organizacja metryk dostawcy portów w rejestrze. `PortSupplier` jest nazwą typu metryki dla dostawcy portu i odpowiada *[typ metryki]*.

 `PortSupplier`\

 *[identyfikator GUID dostawcy portu]*\

 `CLSID` = *[identyfikator GUID klasy]*

 *[Metryka] = [wartość metryki]*

 *[Metryka] = [wartość metryki]*

|Symbol zastępczy|Opis|
|-----------------|-----------------|
|*[identyfikator GUID dostawcy portu]*|Identyfikator GUID dostawcy portu|
|*[identyfikator GUID klasy]*|Identyfikator GUID klasy, która implementuje tego dostawcę portu.|

### <a name="symbol-providers"></a>Dostawcy symboli
 Poniżej znajduje się organizacja metryk dostawcy symboli w rejestrze. `SymbolProvider` jest nazwą typu metryki dla dostawcy symboli i odpowiada *[typ metryki]*.

 `SymbolProvider`\

 *[identyfikator GUID dostawcy symboli]*\

 `file`\

 `CLSID` = *[identyfikator GUID klasy]*

 *[Metryka] = [wartość metryki]*

 *[Metryka] = [wartość metryki]*

 `metadata`\

 `CLSID` = *[identyfikator GUID klasy]*

 *[Metryka] = [wartość metryki]*

 *[Metryka] = [wartość metryki]*

|Symbol zastępczy|Opis|
|-----------------|-----------------|
|*[identyfikator GUID dostawcy symboli]*|Identyfikator GUID dostawcy symboli|
|*[identyfikator GUID klasy]*|Identyfikator GUID klasy, która implementuje tego dostawcę symboli|

### <a name="expression-evaluators"></a>Ocenianie wyrażeń
 Poniżej znajduje się organizacja metryk ewaluatora wyrażeń w rejestrze. `ExpressionEvaluator` jest nazwą typu metryki dla ewaluatora wyrażeń i odpowiada *[typ metryki]*.

> [!NOTE]
> Typ metryki dla `ExpressionEvaluator` nie został zdefiniowany w dbgmetric. h, ponieważ zakłada się, że wszystkie zmiany metryk dla ocen wyrażeń przechodzą przez odpowiednie funkcje metryk ewaluatora wyrażeń (układ `ExpressionEvaluator` podklucza jest dość skomplikowany, dlatego szczegóły są ukryte w dbgmetric. lib).

 `ExpressionEvaluator`\

 *[identyfikator GUID języka]*\

 *[identyfikator GUID dostawcy]*\

 `CLSID` = *[identyfikator GUID klasy]*

 *[Metryka] = [wartość metryki]*

 *[Metryka] = [wartość metryki]*

 `Engine`\

 `0` = *[identyfikator GUID aparatu debugowania]*

 `1` = *[identyfikator GUID aparatu debugowania]*

|Symbol zastępczy|Opis|
|-----------------|-----------------|
|*[identyfikator GUID języka]*|Identyfikator GUID języka|
|*[identyfikator GUID dostawcy]*|Identyfikator GUID dostawcy|
|*[identyfikator GUID klasy]*|Identyfikator GUID klasy implementującej tę ewaluatora wyrażeń|
|*[identyfikator GUID aparatu debugowania]*|Identyfikator GUID aparatu debugowania, z którym działa ta ewaluatora wyrażeń|

### <a name="expression-evaluator-extensions"></a>Rozszerzenia ewaluatora wyrażeń
 Poniżej znajduje się organizacja metryk rozszerzenia ewaluatora wyrażeń w rejestrze. `EEExtensions` jest nazwą typu metryki dla rozszerzeń ewaluatora wyrażeń i odpowiada *[typ metryki]*.

 `EEExtensions`\

 *[identyfikator GUID rozszerzenia]*\

 *[Metryka] = [wartość metryki]*

 *[Metryka] = [wartość metryki]*

|Symbol zastępczy|Opis|
|-----------------|-----------------|
|*[identyfikator GUID rozszerzenia]*|Identyfikator GUID rozszerzenia ewaluatora wyrażeń|

### <a name="exceptions"></a>Wyjątki
 Poniżej znajduje się organizacja wyjątków metryk w rejestrze. `Exception` jest nazwą typu metryki dla wyjątków i odpowiada *[typ metryki]*.

 `Exception`\

 *[identyfikator GUID aparatu debugowania]*\

 *[typy wyjątków]*\

 *Oprócz*\

 *[Metryka] = [wartość metryki]*

 *[Metryka] = [wartość metryki]*

 *Oprócz*\

 *[Metryka] = [wartość metryki]*

 *[Metryka] = [wartość metryki]*

|Symbol zastępczy|Opis|
|-----------------|-----------------|
|*[identyfikator GUID aparatu debugowania]*|Identyfikator GUID aparatu debugowania, który obsługuje wyjątki.|
|*[typy wyjątków]*|Ogólny tytuł podklucza identyfikujący klasę wyjątków, które mogą być obsługiwane. Typowe nazwy to **wyjątki języka C++**, **wyjątki Win32**, **wyjątki środowiska uruchomieniowego języka wspólnego** i **natywne testy Run-Time**. Te nazwy są również używane do identyfikowania konkretnej klasy wyjątku dla użytkownika.|
|*Oprócz*|Nazwa wyjątku: na przykład **_com_error** lub **Break**. Te nazwy są również używane do identyfikowania konkretnego wyjątku dla użytkownika.|

## <a name="requirements"></a>Wymagania
 Te pliki znajdują się w [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] katalogu instalacyjnym zestawu SDK (domyślnie *[dysk]* \Program Files\Microsoft Visual Studio 2010 SDK \\ ).

 Nagłówek: includes\dbgmetric.h

 Biblioteka: libs\ad2de.lib, libs\dbgmetric.lib

## <a name="see-also"></a>Zobacz też
- [Dokumentacja interfejsu API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
