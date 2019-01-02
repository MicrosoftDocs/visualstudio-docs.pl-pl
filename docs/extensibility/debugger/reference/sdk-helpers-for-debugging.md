---
title: Pomocnicy zestawu SDK do debugowania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6655b96ed51cd7cce5e94ce96cedf97517f1872a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53942414"
---
# <a name="sdk-helpers-for-debugging"></a>Pomocnicy zestawu SDK do debugowania
Te funkcje i deklaracji są funkcje pomocnicze globalnego dotyczące implementowania silniki debugowania, ewaluatory wyrażeń i dostawców symboli w języku C++.  
  
> [!NOTE]
>  W tej chwili istnieje nie zarządzanych wersje tych funkcji i deklaracji.  
  
## <a name="overview"></a>Omówienie  
 Aby silniki debugowania, ewaluatory wyrażeń i dostawców symbol ma być używany przez program Visual Studio musi zostać zarejestrowany. Jest to realizowane przez ustawienie podklucze i wpisy, znanych także jako "ustawienie metryki". Następujące funkcje globalne są przeznaczone do jej obsługi ułatwiają realizację procesu aktualizacji tych metryk. Zobacz sekcję dotyczącą lokalizacji rejestru, aby dowiedzieć się, układ każdej podklucza rejestru, która jest aktualizowana przez te funkcje.  
  
## <a name="general-metric-functions"></a>Ogólne metryki funkcji  
 Są to ogólne funkcje używane przez aparaty debugowania. Wyspecjalizowane funkcje dla ewaluatory wyrażeń i dostawców symboli są szczegółowo opisane później.  
  
### <a name="getmetric-method"></a>Metoda GetMetric  
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
|pszMachine|[in] Nazwa komputera prawdopodobnie zdalnego, w których rejestru zostanie zapisany (`NULL` oznacza, że komputer lokalny).|  
|pszType|[in] Jeden z typów metryki.|  
|guidSection|[in] Identyfikator GUID konkretnego aparatu ewaluatora, wyjątków, itp. To ustawienie określa podsekcji w ramach typu metryki dla określonego elementu.|  
|pszMetric|[in] Metryki, które mają zostać uzyskane. Odpowiada nazwie określonej wartości.|  
|pdwValue|[in] Lokalizacja magazynu wartość metryki. Istnieje kilka odmian systemu GetMetric, która może zwracać wartość typu DWORD (jak w poniższym przykładzie), ciąg BSTR, identyfikator GUID lub tablicę identyfikatorów GUID.|  
|pszAltRoot|[in] Rejestr alternatywny katalog główny. Ustaw `NULL` Aby użyć domyślnej.|  
  
### <a name="setmetric-method"></a>Metoda SetMetric  
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
|pszType|[in] Jeden z typów metryki.|  
|guidSection|[in] Identyfikator GUID konkretnego aparatu ewaluatora, wyjątków, itp. To ustawienie określa podsekcji w ramach typu metryki dla określonego elementu.|  
|pszMetric|[in] Metryki, które mają zostać uzyskane. Odpowiada nazwie określonej wartości.|  
|dwValue|[in] Lokalizacja magazynu wartość metryki. Istnieje kilka odmian systemu SetMetric, które mogą być przechowywane DWORD (w tym przykładzie), ciąg BSTR, identyfikator GUID lub tablicę identyfikatorów GUID.|  
|fUserSpecific|[in] Wartość TRUE, jeśli metryka jest specyficzne dla użytkownika, a jeśli będą zapisywane w gałęzi użytkownika zamiast hive komputera lokalnego.|  
|pszAltRoot|[in] Rejestr alternatywny katalog główny. Ustaw `NULL` Aby użyć domyślnej.|  
  
### <a name="removemetric-method"></a>Metoda RemoveMetric  
 Usuwa określony metryki z rejestru.  
  
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
|pszType|[in] Jeden z typów metryki.|  
|guidSection|[in] Identyfikator GUID konkretnego aparatu ewaluatora, wyjątków, itp. To ustawienie określa podsekcji w ramach typu metryki dla określonego elementu.|  
|pszMetric|[in] Metryki, które ma zostać usunięty. Odpowiada nazwie określonej wartości.|  
|pszAltRoot|[in] Rejestr alternatywny katalog główny. Ustaw `NULL` Aby użyć domyślnej.|  
  
### <a name="enummetricsections-method"></a>Metoda EnumMetricSections  
 Wylicza różnych sekcji metryki w rejestrze.  
  
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
|pszMachine|[in] Nazwa komputera prawdopodobnie zdalnego, w których rejestru zostanie zapisany (`NULL` oznacza, że komputer lokalny).|  
|pszType|[in] Jeden z typów metryki.|  
|rgguidSections|[out w] Przydzielony wstępnie tablicę identyfikatorów GUID do wypełnienia.|  
|pdwSize|[in] Maksymalna liczba identyfikatorów GUID, które mogą być przechowywane w `rgguidSections` tablicy.|  
|pszAltRoot|[in] Rejestr alternatywny katalog główny. Ustaw `NULL` Aby użyć domyślnej.|  
  
## <a name="expression-evaluator-functions"></a>Funkcje ewaluatora wyrażeń  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|GetEEMetric|Pobiera wartość metryki z rejestru.|  
|SetEEMetric|Ustawia określoną wartość metryki w rejestrze.|  
|RemoveEEMetric|Usuwa określony metryki z rejestru.|  
|GetEEMetricFile|Pobiera nazwę pliku z określonej metryki i ładuje, zwraca zawartość pliku jako ciąg.|  
  
## <a name="exception-functions"></a>Wyjątek funkcji  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|GetExceptionMetric|Pobiera wartość metryki z rejestru.|  
|SetExceptionMetric|Ustawia określoną wartość metryki w rejestrze.|  
|RemoveExceptionMetric|Usuwa określony metryki z rejestru.|  
|RemoveAllExceptionMetrics|Usuwa wszystkie metryki wyjątek z rejestru.|  
  
## <a name="symbol-provider-functions"></a>Funkcje dostawcy symboli  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|GetSPMetric|Pobiera wartość metryki z rejestru.|  
|SetSPMetric|Ustawia określoną wartość metryki w rejestrze.|  
|RemoveSPMetric|Usuwa określony metryki z rejestru.|  
  
## <a name="enumeration-functions"></a>Wyliczenie funkcji  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|EnumMetricSections|Wylicza wszystkie metryki dla określonego typu metryki.|  
|EnumDebugEngine|Wylicza aparaty debugowania zarejestrowane.|  
|EnumEEs|Wylicza ewaluatory wyrażeń zarejestrowane.|  
|EnumExceptionMetrics|Wylicza wszystkie metryki wyjątku.|  
  
## <a name="metric-definitions"></a>Definicje metryk  
 Te definicje mogą służyć do wstępnie zdefiniowanych nazw metryki. Nazwy odpowiadają różne klucze rejestru i wartości nazwy i są definiowane jako ciągi znaków dwubajtowych: na przykład `extern LPCWSTR metrictypeEngine`.  
  
|Wstępnie zdefiniowanych typów metryki|Opis: Podstawowy klucz dla...|  
|-----------------------------|---------------------------------------|  
|metrictypeEngine|Debuguj wszystkie metryki aparatu.|  
|metrictypePortSupplier|Wszystkie metryki dostawcy portu.|  
|metrictypeException|Wszystkie metryki wyjątku.|  
|metricttypeEEExtension|Wszystkie rozszerzenia ewaluatora wyrażenia.|  
  
|Właściwości aparatu debugowania|Opis|  
|-----------------------------|-----------------|  
|metricAddressBP|Ustaw wartość różną od zera, aby wskazać obsługi punktów przerwania adresu.|  
|metricAlwaysLoadLocal|Ustaw wartość różną od zera, aby można było zawsze Ładuj lokalnie za pomocą aparatu debugowania.|  
|metricLoadInDebuggeeSession|NIE JEST UŻYWANY|  
|metricLoadedByDebuggee|Ustaw wartość różną od zera, aby wskazać, że aparat debugowania zostaną zawsze załadowane z lub debugowanego programu.|  
|metricAttach|Ustaw wartość różną od zera, aby wskazać, obsługa załącznika do istniejących programów.|  
|metricCallStackBP|Ustaw wartość różną od zera, aby wskazać obsługi punktów przerwania stosu wywołań.|  
|metricConditionalBP|Ustaw wartość różną od zera, aby wskazać, obsługę ustawień warunkowe punkty przerwania.|  
|metricDataBP|Ustaw wartość różną od zera, aby wskazać, obsługa ustawienie punktów przerwania na zmiany w danych.|  
|metricDisassembly|Ustaw na różną od zera, aby wskazać, wsparcie dla wersji produkcyjnej, lista dezasemblacji.|  
|metricDumpWriting|Ustaw wartość różną od zera, aby wskazać, obsługa zrzutu zapisywania (zrzucania pamięci na urządzeniach).|  
|metricENC|Ustaw na różną od zera, aby wskazać, pomocy technicznej na potrzeby operacji Edytuj i Kontynuuj. **Uwaga:**  Niestandardowego aparatu debugowania nigdy nie ustawiać lub zawsze należy ustawić na wartość 0.|  
|metricExceptions|Ustaw wartość różną od zera, aby wskazać, obsługa wyjątków.|  
|metricFunctionBP|Ustaw wartość różną od zera, aby wskazać, Obsługa nazwanych punkty przerwania (punktów przerwania podziału, gdy wywoływana jest nazwą funkcji).|  
|metricHitCountBP|Ustaw wartość różną od zera, aby wskazać, pomocy technicznej dla ustawienia "Traf punkt" punkty przerwania (punktów przerwania, które są wyzwalane tylko wtedy, gdy trafienia określonej liczby razy).|  
|metricJITDebug|Ustaw na różną od zera, aby wskazać, obsługę debugowania just in time, (debuger jest uruchamiany, gdy wystąpi wyjątek w procesie uruchomione).|  
|metricMemory|NIE JEST UŻYWANY|  
|metricPortSupplier|Ustaw tę opcję na identyfikator CLSID dostawcy portu, jeśli jeden jest zaimplementowana.|  
|metricRegisters|NIE JEST UŻYWANY|  
|metricSetNextStatement|Ustaw wartość różną od zera, aby wskazać, obsługa ustawienie następnej instrukcji, (które pomija wykonanie pośrednich instrukcji).|  
|metricSuspendThread|Ustaw wartość różną od zera, aby wskazać obsługę wstrzymywania wykonanie wątku.|  
|metricWarnIfNoSymbols|Ustaw wartość różną od zera, aby wskazać, że użytkownik powinien otrzymywać powiadomienia, gdy istnieją żadnych symboli.|  
|metricProgramProvider|Ustaw tę pozycję na identyfikator CLSID dostawcy program.|  
|metricAlwaysLoadProgramProviderLocal|Ustaw tę pozycję do różną od zera, aby wskazać, że dostawca programu powinna zawsze być załadowane lokalnie.|  
|metricEngineCanWatchProcess|Ustaw tę opcję na wartość różną od zera do wskazania, że aparat debugowania będzie oczekiwał na przetwarzanie zdarzeń, a nie dostawcy programu.|  
|metricRemoteDebugging|Ustaw tę opcję na wartość różną od zera do wskazania obsługę zdalnego debugowania.|  
|metricEncUseNativeBuilder|Ustaw tę pozycję do różną od zera, aby wskazać, że Edytuj i Kontynuuj Manager powinien używać encbuild.dll aparat debugowania do kompilacji na potrzeby operacji Edytuj i Kontynuuj. **Uwaga:**  Niestandardowego aparatu debugowania nigdy nie ustawiać lub zawsze należy ustawić na wartość 0.|  
|metricLoadUnderWOW64|Ustaw tę opcję na wartość różną od zera do wskazania, że aparat debugowania powinny być załadowane w procesie debugowanego obiektu w środowisku WOW podczas debugowania procesu 64-bitowego; w przeciwnym razie aparat debugowania zostanie załadowany w procesie programu Visual Studio (który działa w emulatorze WOW64).|  
|metricLoadProgramProviderUnderWOW64|Ustaw tę opcję na wartość różną od zera do wskazania, że dostawcy programu powinny być załadowane w procesie debugowanego obiektu podczas debugowania procesu 64-bitowego, w środowisku WOW; w przeciwnym razie zostanie załadowany w procesie programu Visual Studio.|  
|metricStopOnExceptionCrossingManagedBoundary|Ustaw tę opcję na wartość różną od zera do wskazania, że proces ma zostać zatrzymana, jeśli wystąpił nieobsługiwany wyjątek jest zgłaszany w granicach zarządzanych/niezarządzanych kodu.|  
|metricAutoSelectPriority|Wartość priorytetu do automatycznego wybierania aparat debugowania (wyższe wartości equals wyższy priorytet).|  
|metricAutoSelectIncompatibleList|Klucz rejestru zawierające wpisy, które są określone identyfikatory GUID silniki debugowania mają być ignorowane w wybieranego automatycznie. Te wpisy są liczbą (0, 1, 2 i tak dalej) z identyfikatorem GUID wyrażone jako ciąg.|  
|metricIncompatibleList|Klucz rejestru zawierające wpisy, które określają identyfikatorów GUID dla aparaty debugowania, które są niezgodne z tym aparat debugowania.|  
|metricDisableJITOptimization|Ustaw tę opcję na wartość różną od zera do wskazania, że podczas debugowania powinny być wyłączone optymalizacje just-in-time (dla kodu zarządzanego).|  
  
|Właściwości ewaluatora wyrażenia|Opis|  
|-------------------------------------|-----------------|  
|metricEngine|To przechowuje liczbę aparatów debugowania, które obsługują Ewaluator wyrażeń określony.|  
|metricPreloadModules|Ustaw tę opcję na wartość różną od zera do wskazania, że moduły powinny zostać wstępnie załadowane po uruchomieniu ewaluatora wyrażeń względem programu.|  
|metricThisObjectName|Wartość "to" Nazwa obiektu.|  
  
|Właściwości rozszerzenia ewaluatora wyrażeń|Opis|  
| - |-----------------|  
|metricExtensionDll|Nazwa biblioteki dll, która obsługuje tego rozszerzenia.|  
|metricExtensionRegistersSupported|Lista rejestrów obsługiwane.|  
|metricExtensionRegistersEntryPoint|Punkt wejścia do uzyskiwania dostępu do rejestrów.|  
|metricExtensionTypesSupported|Lista obsługiwanych typów.|  
|metricExtensionTypesEntryPoint|Punkt wejścia do uzyskiwania dostępu do typów.|  
  
|Właściwości dostawcy portu|Opis|  
|------------------------------|-----------------|  
|metricPortPickerCLSID|Identyfikator CLSID selektora portu (okno dialogowe użytkownika umożliwia wybierz porty, a następnie dodać porty używane do debugowania).|  
|metricDisallowUserEnteredPorts|Wartość różną od zera, jeśli użytkownik wprowadził portów nie można dodać do dostawcy portu (sprawia to, że okno dialogowe selektora portu zasadniczo tylko do odczytu).|  
|metricPidBase|Identyfikator podstawowy proces używany przez dostawcę portu podczas przydzielania identyfikatorów procesów.|  
  
|SP wstępnie zdefiniowanych typów Store|Opis|  
|-------------------------------|-----------------|  
|storetypeFile|Symbole są przechowywane w oddzielnym pliku.|  
|storetypeMetadata|Symbole są przechowywane jako metadane w zestawie.|  
  
|Różne właściwości|Opis|  
|------------------------------|-----------------|  
|metricShowNonUserCode|Ustaw tę opcję na wartość różną od zera do wyświetlenia nonuser kodu.|  
|metricJustMyCodeStepping|Ustaw tę opcję na wartość różną od zera do wskazania, że przechodzenie krok po kroku może wystąpić tylko w kodzie użytkownika.|  
|metricCLSID|Identyfikator klasy obiektu określonego typu metryki.|  
|MetricName|Przyjazna nazwa dla obiektu określonego typu metryki.|  
|metricLanguage|Nazwa języka.|  
  
## <a name="registry-locations"></a>W lokalizacji rejestru  
 Metryki są odczytywane i zapisywane w rejestrze, w szczególności w `VisualStudio` podklucza.  
  
> [!NOTE]
>  W większości przypadków, metryki będą zapisywane w kluczu HKEY_LOCAL_MACHINE. Jednak czasami HKEY_CURRENT_USER będzie klucz miejsca docelowego. Dbgmetric.lib obsługuje oba klucze. Podczas pobierania metrykę, przeszukuje HKEY_CURRENT_USER pierwszy, a następnie HKEY_LOCAL_MACHINE. Podczas metrykę, parametr określa, które klucz najwyższego poziomu do użycia.  
  
 *[klucz rejestru]*\  
  
 `Software`\  
  
 `Microsoft`\  
  
 `VisualStudio`\  
  
 *[wersja główny]*\  
  
 *[metryki główny]*\  
  
 *[type metryki]*\  
  
 *[Metryka] = [wartość metryki]*  
  
 *[Metryka] = [wartość metryki]*  
  
 *[Metryka] = [wartość metryki]*  
  
|Symbol zastępczy|Opis|  
|-----------------|-----------------|  
|*[klucz rejestru]*|`HKEY_CURRENT_USER` lub `HKEY_LOCAL_MACHINE`.|  
|*[wersja główny]*|Wersja programu Visual Studio (na przykład `7.0`, `7.1`, lub `8.0`). Jednak ten główny można także modyfikować za pomocą **/rootsuffix** przełączyć się do **devenv.exe**. W przypadku VSIP, ten modyfikator, jest zwykle **Exp**, więc głównej wersji może być na przykład 8.0Exp.|  
|*[metryki główny]*|Jest to `AD7Metrics` lub `AD7Metrics(Debug)`, w zależności od tego, czy wersja debugowania dbgmetric.lib jest używana. **Uwaga:**  Czy dbgmetric.lib jest używany, następująca Konwencja nazewnictwa powinien należy przestrzegać w przypadku różnic między debugowaniem i wydawaniem wersje, które musi mieć odzwierciedlenie w rejestrze.|  
|*[type metryki]*|Typ metryki, które ma zostać zapisany: `Engine`, `ExpressionEvaluator`, `SymbolProvider`itp. Są one wszystkie zdefiniowane tak jak dbgmetric.h jako `metricTypeXXXX`, gdzie `XXXX` jest nazwą określonego typu.|  
|*[Metryka]*|Nazwa wpisu do przypisania wartości, aby można było ustawić wartość metryki. Rzeczywiste organizacji metryk zależy od typu metryki.|  
|*[wartość metryki]*|Wartość przypisana do metrykę. Metryka zależy od typu wartości powinny mieć (ciąg, liczba itp.).|  
  
> [!NOTE]
>  Wszystkie identyfikatory GUID są przechowywane w formacie `{GUID}`. Na przykład `{123D150B-FA18-461C-B218-45B3E4589F9B}`.  
  
### <a name="debug-engines"></a>Aparaty debugowania  
 Poniżej znajduje się organizacja metryki aparaty debugowania w rejestrze. `Engine` jest to nazwa typu metryki dla aparatu debugowania i odpowiada *[type metryki]* w zainstalowanym poddrzewie rejestru powyżej.  
  
 `Engine`\  
  
 *[identyfikator guid aparatu]*\  
  
 `CLSID` = *[identyfikator guid klasy]*  
  
 *[Metryka] = [wartość metryki]*  
  
 *[Metryka] = [wartość metryki]*  
  
 *[Metryka] = [wartość metryki]*  
  
 `PortSupplier`\  
  
 `0` = *[guid dostawcy portu]*  
  
 `1` = *[guid dostawcy portu]*  
  
|Symbol zastępczy|Opis|  
|-----------------|-----------------|  
|*[identyfikator guid aparatu]*|Identyfikator GUID aparatu debugowania.|  
|*[identyfikator guid klasy]*|Identyfikator GUID klasy, która implementuje ten aparat debugowania.|  
|*[guid dostawcy portu]*|Identyfikator GUID dostawcy portu, jeśli istnieje. Wiele aparaty debugowania Użyj dostawcy portu domyślnego i w związku z tym nie należy określać ich własnego dostawcy. W tym przypadku podklucz `PortSupplier` będą nieobecne.|  
  
### <a name="port-suppliers"></a>Dostawcy portów  
 Poniżej znajduje się organizacja metryki dostawcy portu w rejestrze. `PortSupplier` jest to nazwa typu metryki dla dostawcy portu i odpowiada *[type metryki]*.  
  
 `PortSupplier`\  
  
 *[guid dostawcy portu]*\  
  
 `CLSID` = *[identyfikator guid klasy]*  
  
 *[Metryka] = [wartość metryki]*  
  
 *[Metryka] = [wartość metryki]*  
  
|Symbol zastępczy|Opis|  
|-----------------|-----------------|  
|*[guid dostawcy portu]*|Identyfikator GUID dostawcy portu|  
|*[identyfikator guid klasy]*|Identyfikator GUID klasy, która implementuje ten dostawcy portu|  
  
### <a name="symbol-providers"></a>Symbol dostawców  
 Poniżej znajduje się organizacja metryki dostawca symboli w rejestrze. `SymbolProvider` jest nazwą typu metryki dla dostawcy symboli i odpowiada *[type metryki]*.  
  
 `SymbolProvider`\  
  
 *[identyfikator guid dostawcy symbol]*\  
  
 `file`\  
  
 `CLSID` = *[identyfikator guid klasy]*  
  
 *[Metryka] = [wartość metryki]*  
  
 *[Metryka] = [wartość metryki]*  
  
 `metadata`\  
  
 `CLSID` = *[identyfikator guid klasy]*  
  
 *[Metryka] = [wartość metryki]*  
  
 *[Metryka] = [wartość metryki]*  
  
|Symbol zastępczy|Opis|  
|-----------------|-----------------|  
|*[identyfikator guid dostawcy symbol]*|Identyfikator GUID dostawcy symboli|  
|*[identyfikator guid klasy]*|Identyfikator GUID klasy, która implementuje ten dostawca symboli|  
  
### <a name="expression-evaluators"></a>Ewaluatory wyrażeń  
 Poniżej znajduje się organizacja metryki ewaluatora wyrażeń w rejestrze. `ExpressionEvaluator` jest to nazwa typu metryki dla Ewaluator wyrażeń i odpowiada *[type metryki]*.  
  
> [!NOTE]
>  Typ metryki `ExpressionEvaluator` nie jest zdefiniowany w dbgmetric.h, ponieważ zakłada się, że wszystkie zmiany metryki dla ewaluatory wyrażeń zostanie wysłany za pomocą funkcji metryki ewaluatora wyrażeń odpowiednie (układ `ExpressionEvaluator` podklucz jest nieco skomplikowane, dzięki czemu szczegółowe informacje są ukryte wewnątrz dbgmetric.lib).  
  
 `ExpressionEvaluator`\  
  
 *[identyfikator guid języka]*\  
  
 *[identyfikator guid dostawcy]*\  
  
 `CLSID` = *[identyfikator guid klasy]*  
  
 *[Metryka] = [wartość metryki]*  
  
 *[Metryka] = [wartość metryki]*  
  
 `Engine`\  
  
 `0` = *[guid aparatu debugowania]*  
  
 `1` = *[guid aparatu debugowania]*  
  
|Symbol zastępczy|Opis|  
|-----------------|-----------------|  
|*[identyfikator guid języka]*|Identyfikator GUID języka|  
|*[identyfikator guid dostawcy]*|Identyfikator GUID dostawcy|  
|*[identyfikator guid klasy]*|Identyfikator GUID klasy, która implementuje ten Ewaluator wyrażeń|  
|*[guid aparatu debugowania]*|Identyfikator GUID działającego w tym ewaluatora wyrażenia z aparatu debugowania|  
  
### <a name="expression-evaluator-extensions"></a>Rozszerzenia ewaluatora wyrażeń  
 Poniżej znajduje się organizacja metryki rozszerzenia ewaluatora wyrażenia, w rejestrze. `EEExtensions` jest nazwą typu metryki dla wyrażenia rozszerzenia ewaluatora i odpowiada *[type metryki]*.  
  
 `EEExtensions`\  
  
 *[identyfikator guid rozszerzenie]*\  
  
 *[Metryka] = [wartość metryki]*  
  
 *[Metryka] = [wartość metryki]*  
  
|Symbol zastępczy|Opis|  
|-----------------|-----------------|  
|*[identyfikator guid rozszerzenie]*|Identyfikator GUID rozszerzenie ewaluatora wyrażeń|  
  
### <a name="exceptions"></a>Wyjątki  
 Poniżej znajduje się organizacja metryki wyjątki w rejestrze. `Exception` jest to nazwa typu metryki dla wyjątków i odpowiada *[type metryki]*.  
  
 `Exception`\  
  
 *[guid aparatu debugowania]*\  
  
 *[typów wyjątków]*\  
  
 *[wyjątek]*\  
  
 *[Metryka] = [wartość metryki]*  
  
 *[Metryka] = [wartość metryki]*  
  
 *[wyjątek]*\  
  
 *[Metryka] = [wartość metryki]*  
  
 *[Metryka] = [wartość metryki]*  
  
|Symbol zastępczy|Opis|  
|-----------------|-----------------|  
|*[guid aparatu debugowania]*|Identyfikator GUID aparatu debugowania, który obsługuje wyjątki.|  
|*[typów wyjątków]*|Ogólny tytuł podklucza który identyfikuje klasy wyjątków, które są obsługiwane. Typowe nazwy są **wyjątki C++**, **wyjątki Win32**, **wyjątki środowiska uruchomieniowego języka wspólnego**, i **macierzystego sprawdzania w trakcie wykonywania**. Te nazwy są również używane do identyfikowania konkretnej klasy wyjątku dla użytkownika.|  
|*[wyjątek]*|Nazwa, dla wyjątku: na przykład **_com_error** lub **klawisze CTRL + Break**. Te nazwy są również używane do identyfikować określony wyjątek dla użytkownika.|  
  
## <a name="requirements"></a>Wymagania  
 Te pliki znajdują się w [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] katalogu instalacji zestawu SDK (domyślnie *[dysk]* \Program Files\Microsoft programu Visual Studio 2010 SDK\\).  
  
 Nagłówek: includes\dbgmetric.h  
  
 Biblioteki: libs\ad2de.lib, libs\dbgmetric.lib  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsu API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)