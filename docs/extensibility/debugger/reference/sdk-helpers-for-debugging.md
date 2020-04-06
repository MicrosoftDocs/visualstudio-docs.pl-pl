---
title: Pomocnicy SDK do debugowania | Dokumenty firmy Microsoft
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9edb7c508fdea6736a71c0f70c0d2ff305d4a399
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713650"
---
# <a name="sdk-helpers-for-debugging"></a>Pomocnicy zestawu SDK do debugowania
Te funkcje i deklaracje są funkcje pomocnika globalnego do implementowania aparatów debugowania, oceniających wyrażenia i dostawców symboli w języku C++.

> [!NOTE]
> Obecnie nie ma żadnych zarządzanych wersji tych funkcji i deklaracji.

## <a name="overview"></a>Omówienie
 Aby aparaty debugowania, oceniający wyrażenia i dostawcy symboli były używane przez program Visual Studio, muszą być zarejestrowane. Odbywa się to przez ustawienie podkluczy rejestru i wpisów, inaczej znany jako "metryki ustawień." Następujące funkcje globalne są przeznaczone do ułatwienia procesu aktualizowania tych metryk. Zobacz sekcję Lokalizacje rejestru, aby dowiedzieć się układ każdego podklucza rejestru, który jest aktualizowany przez te funkcje.

## <a name="general-metric-functions"></a>Ogólne funkcje metryczne
 Są to ogólne funkcje używane przez aparaty debugowania. Wyspecjalizowane funkcje dla oceniających wyrażenia i dostawców symboli są szczegółowe później.

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
|pszMachine|[w] Nazwa ewentualnie zdalnego komputera, którego rejestr`NULL` zostanie zapisany ( oznacza maszynę lokalną).|
|pszType|[w] Jeden z typów metryki.|
|guidSekcja|[w] GUID określonego silnika, oceniającego, wyjątku itp. Określa podsekcję w ramach typu metryki dla określonego elementu.|
|pszMetric (pszmetric)|[w] Metryka, która ma zostać uzyskana. Odpowiada to określonej nazwie wartości.|
|wartość pdwValue|[w] Lokalizacja przechowywania wartości z metryki. Istnieje kilka smaków GetMetric, które mogą zwracać DWORD (jak w tym przykładzie), BSTR, guid lub tablicy identyfikatorów GUID.|
|pszAltRoot|[w] Alternatywny katalog główny rejestru do użycia. Ustaw, `NULL` aby użyć wartości domyślnej.|

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
|pszType|[w] Jeden z typów metryki.|
|guidSekcja|[w] GUID określonego silnika, oceniającego, wyjątku itp. Określa podsekcję w ramach typu metryki dla określonego elementu.|
|pszMetric (pszmetric)|[w] Metryka, która ma zostać uzyskana. Odpowiada to określonej nazwie wartości.|
|dwValue (Wartość dwValue)|[w] Lokalizacja przechowywania wartości w metryki. Istnieje kilka smaków SetMetric, które mogą przechowywać DWORD (w tym przykładzie), BSTR, guid lub tablicy identyfikatorów GUID.|
|fUserSpecific (Specjalista ds.|[w] PRAWDA, jeśli metryka jest specyficzna dla użytkownika i jeśli powinna być zapisywana w gałęzi użytkownika zamiast lokalnego gałęzi komputera.|
|pszAltRoot|[w] Alternatywny katalog główny rejestru do użycia. Ustaw, `NULL` aby użyć wartości domyślnej.|

### <a name="removemetric-method"></a>Metoda usuwania metryki
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
|pszType|[w] Jeden z typów metryki.|
|guidSekcja|[w] GUID określonego silnika, oceniającego, wyjątku itp. Określa podsekcję w ramach typu metryki dla określonego elementu.|
|pszMetric (pszmetric)|[w] Metryka do usunięcia. Odpowiada to określonej nazwie wartości.|
|pszAltRoot|[w] Alternatywny katalog główny rejestru do użycia. Ustaw, `NULL` aby użyć wartości domyślnej.|

### <a name="enummetricsections-method"></a>Metoda wyliczenia
 Wylicza różne sekcje metryki w rejestrze.

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
|pszMachine|[w] Nazwa ewentualnie zdalnego komputera, którego rejestr`NULL` zostanie zapisany ( oznacza maszynę lokalną).|
|pszType|[w] Jeden z typów metryki.|
|rgguidSekcje|[w, na zewnątrz] Wstępnie przydzielona tablica identyfikatorów GUID do wypełnienia.|
|rozmiar pdwSize|[w] Maksymalna liczba identyfikatorów GUID, które `rgguidSections` mogą być przechowywane w tablicy.|
|pszAltRoot|[w] Alternatywny katalog główny rejestru do użycia. Ustaw, `NULL` aby użyć wartości domyślnej.|

## <a name="expression-evaluator-functions"></a>Funkcje oceniającego wyrażenia

|Funkcja|Opis|
|--------------|-----------------|
|GeteeMetric ( GetEEMetric )|Pobiera wartość metryki z rejestru.|
|SetEEMetric (metryk Seteemetric)|Ustawia określoną wartość metryki w rejestrze.|
|Usuńemetryczne|Usuwa określoną metrykę z rejestru.|
|GetEEMetricFile|Pobiera nazwę pliku z określonej metryki i ładuje go, zwracając zawartość pliku jako ciąg.|

## <a name="exception-functions"></a>Funkcje wyjątków

|Funkcja|Opis|
|--------------|-----------------|
|GetExceptionMetric (metryczny getexceptionmetric)|Pobiera wartość metryki z rejestru.|
|SetExceptionMetric (Wskaźnik z wyjątkiem zestawu)|Ustawia określoną wartość metryki w rejestrze.|
|Usuńexceptionmetric|Usuwa określoną metrykę z rejestru.|
|UsuńallExceptionMetrics|Usuwa wszystkie metryki wyjątków z rejestru.|

## <a name="symbol-provider-functions"></a>Funkcje dostawcy symboli

|Funkcja|Opis|
|--------------|-----------------|
|GetSPMetric (GetSPMetric)|Pobiera wartość metryki z rejestru.|
|SetSPMetric (metryk)|Ustawia określoną wartość metryki w rejestrze.|
|Usuńspmetric|Usuwa określoną metrykę z rejestru.|

## <a name="enumeration-functions"></a>Funkcje wyliczenia

|Funkcja|Opis|
|--------------|-----------------|
|Odsyłania wyliczenia|Wylicza wszystkie metryki dla określonego typu metryki.|
|EnumDebugInżyn|Wylicza zarejestrowanych aparatów debugowania.|
|EnumEEs|Wylicza zarejestrowanych oceniających wyrażenie.|
|Metryki wyliczenia|Wylicza wszystkie metryki wyjątków.|

## <a name="metric-definitions"></a>Definicje metryki
 Definicje te mogą być używane dla wstępnie zdefiniowanych nazw metryk. Nazwy odpowiadają różnym kluczom rejestru i nazwom wartości i są zdefiniowane jako szerokie ciągi znaków: na przykład `extern LPCWSTR metrictypeEngine`.

|Wstępnie zdefiniowane typy metryki|Opis: Klucz podstawowy dla....|
|-----------------------------|---------------------------------------|
|metrictypeEngine|Wszystkie metryki aparatu debugowania.|
|metrictypePortSupplier|Wszystkie metryki dostawcy portów.|
|metrykatytywystawa|Wszystkie metryki wyjątków.|
|metricttypeEEExtension|Wszystkie rozszerzenia oceniającego wyrażenie.|

|Właściwości aparatu debugowania|Opis|
|-----------------------------|-----------------|
|metricAddressBP|Ustaw na niezerowe, aby wskazać obsługę punktów przerwania adresu.|
|metricAlwaysLoadLocal (metrykaAlwaysLoadLocal)|Ustaw na nonzero, aby zawsze ładować aparat debugowania lokalnie.|
|metricLoadInDebuggeeSession|NIEUŻYNO|
|metricLoadedByDebuggee|Ustaw opcję nonzero, aby wskazać, że aparat debugowania będzie zawsze ładowany z lub przez program jest debugowany.|
|metrykaPrzyłączyć|Ustaw nonzero, aby wskazać obsługę załącznika do istniejących programów.|
|metrykaCallStackBP|Ustaw na nonzero, aby wskazać obsługę punktów przerwania stosu wywołań.|
|metricConditionalBP|Ustaw na niezerowe, aby wskazać obsługę ustawienia warunkowych punktów przerwania.|
|metrykaDataBP|Ustaw na nonzero, aby wskazać obsługę ustawiania punktów przerwania na zmiany w danych.|
|metricDisassembly|Ustaw nonzero, aby wskazać obsługę dla produkcji listy demontażu.|
|metricDumpSeded|Ustaw nonzero, aby wskazać obsługę zapisywania zrzutu (dumping pamięci do urządzenia wyjściowego).|
|metricENC|Ustaw pozycję niezerowa, aby wskazać obsługę funkcji Edytuj i Kontynuuj. **Uwaga:**  Aparat debugowania niestandardowe nigdy nie należy ustawić to lub zawsze należy ustawić go na 0.|
|metrycznewyjęcia|Ustaw na niezerowe, aby wskazać obsługę wyjątków.|
|metricFunctionBP|Ustaw różną od zera, aby wskazać obsługę nazwanych punktów przerwania (punktów przerwania, które są przerywane, gdy wywoływana jest określona nazwa funkcji).|
|metricHitCountBP|Ustaw nonzero, aby wskazać obsługę dla ustawienia "punkt trafienia" punktów przerwania (punkty przerwania, które są wyzwalane tylko po trafieniu określoną liczbę razy).|
|metrykaJITDebug|Ustaw na nonzero, aby wskazać obsługę debugowania just-in-time (debuger jest uruchamiany, gdy wystąpi wyjątek w uruchomionym procesie).|
|metrykaMemory|NIEUŻYNO|
|metricPortSupplier|Ustaw to na IDENTYFIKATOR CLSID dostawcy portu, jeśli jeden jest zaimplementowany.|
|metryki Rejestry|NIEUŻYNO|
|metricSetNextStatement|Ustaw na nonzero, aby wskazać obsługę ustawiania następnej instrukcji (która pomija wykonywanie instrukcji pośrednich).|
|metrykaSuspendThread|Ustaw nonzero, aby wskazać obsługę zawieszenia wykonywania wątku.|
|metricWarnIfNoSymbols|Ustaw nonzero, aby wskazać, że użytkownik powinien zostać powiadomiony, jeśli nie ma żadnych symboli.|
|metricProgramProvider|Ustaw to na CLSID dostawcy programu.|
|metricAlwaysLoadProgramProviderLocal|Ustaw tę opcję na niezerowe, aby wskazać, że dostawca programu powinien być zawsze ładowany lokalnie.|
|metricEngineCanWatchProcess|Ustaw tę liczbę niezerowej, aby wskazać, że aparat debugowania będzie obserwować zdarzenia procesu zamiast dostawcy programu.|
|metricRemoteDebugging|Ustaw tę ma być niezerowa, aby wskazać obsługę zdalnego debugowania.|
|metricEncUseNativeBuilder|Ustaw tę pozycję na niezerowa, aby wskazać, że Menedżer edycji i continue powinien używać encbuild.dll aparatu debugowania do tworzenia dla edycji i kontynuowania. **Uwaga:**  Aparat debugowania niestandardowe nigdy nie należy ustawić to lub zawsze należy ustawić go na 0.|
|metricLoadUnderWOW64|Ustaw to na nonzero, aby wskazać, że aparat debugowania powinny być ładowane w procesie debugowania w obszarze WOW podczas debugowania procesu 64-bitowego; w przeciwnym razie aparat debugowania zostanie załadowany w procesie programu Visual Studio (który jest uruchomiony w ramach WOW64).|
|metricLoadProgramProviderUnderWOW64|Ustaw to na niezerowe, aby wskazać, że dostawca programu powinien być ładowany w procesie debugowania podczas debugowania 64-bitowego procesu w obszarze WOW; w przeciwnym razie zostanie załadowany w procesie programu Visual Studio.|
|metricStopOnExceptionCrossingManagedBoundary|Ustaw to na nonzero, aby wskazać, że proces powinien zostać przerwany, jeśli nieobsługiowany wyjątek jest zgłaszany przez granice kodu zarządzanego/niezarządzanego.|
|metricAutoSelectPriority|Ustaw to na priorytet dla automatycznego wyboru aparatu debugowania (wyższe wartości są równe wyższej wartości).|
|metricAutoSelectIncompatibleList|Klucz rejestru zawierający wpisy określające identyfikatory GUID dla aparatów debugowania, które mają być ignorowane w automatycznym wyborze. Te wpisy są liczbą (0, 1, 2 i tak dalej) z identyfikatorem GUID wyrażonym jako ciąg.|
|metricIncompatibleList|Klucz rejestru zawierający wpisy określające identyfikatory GUID dla aparatów debugowania, które są niezgodne z tym aparatem debugowania.|
|metricDisableJITOptymalizacja|Ustaw to na nonzero, aby wskazać, że optymalizacje just-in-time (dla kodu zarządzanego) powinny być wyłączone podczas debugowania.|

|Właściwości ewaluatora wyrażeń|Opis|
|-------------------------------------|-----------------|
|metricEngine|Zawiera liczbę aparatów debugowania, które obsługują oceny określonego wyrażenia.|
|metricPreloadModules|Ustaw to na nonzero, aby wskazać, że moduły powinny być wstępnie załadowane, gdy oceniający wyrażenie jest uruchamiany względem programu.|
|metricThisObjectName|Ustaw tę nazwę obiektu "this".|

|Właściwości rozszerzenia ewaluatora wyrażeń|Opis|
| - |-----------------|
|metricExtensionDll|Nazwa biblioteki dll obsługującej to rozszerzenie.|
|metricExtensionRegistersSupportowane|Lista obsługiwanych rejestrów.|
|metricExtensionRegistersEntryPoint|Punkt wejścia do rejestrów.|
|metricExtensionTypesSupported|Lista obsługiwanych typów.|
|metricExtensionTypesEntryPoint|Punkt wejścia do uzyskiwania dostępu do typów.|

|Właściwości dostawcy portów|Opis|
|------------------------------|-----------------|
|metrykaPortPickerCLSID|Identyfikator CLSID selektora portów (okno dialogowe, którego użytkownik może użyć do wybierania portów i dodawania portów do debugowania).|
|metricDisallowUserUżytÓwporty|Nonzero, jeśli nie można dodać portów wprowadzonych przez użytkownika do dostawcy portu (powoduje to, że okno dialogowe selektora portów jest zasadniczo tylko do odczytu).|
|metricPidBase|Identyfikator procesu podstawowego używany przez dostawcę portu podczas przydzielania identyfikatorów procesu.|

|Wstępnie zdefiniowane typy magazynu SP|Opis|
|-------------------------------|-----------------|
|plik sklepu|Symbole są przechowywane w oddzielnym pliku.|
|storetypeMetadata|Symbole są przechowywane jako metadane w zestawie.|

|Różne właściwości|Opis|
|------------------------------|-----------------|
|metrykiShowNonUserCode|Ustaw to na nonzero, aby wyświetlić kod nieużyjący.|
|metrykaJustMyCodeStepping|Ustaw to na nonzero, aby wskazać, że stepping może wystąpić tylko w kodzie użytkownika.|
|metrycznyCLSID|IDENTYFIKATOR CLSID dla obiektu określonego typu metryki.|
|metricName|Przyjazna dla użytkownika nazwa obiektu określonego typu metryki.|
|metricLanguage|Nazwa języka.|

## <a name="registry-locations"></a>Lokalizacje rejestru
 Metryki są odczytywane i zapisywane w rejestrze, w szczególności w podklucz. `VisualStudio`

> [!NOTE]
> W większości przypadków metryki będą zapisywane w kluczu HKEY_LOCAL_MACHINE. Jednak czasami HKEY_CURRENT_USER będzie kluczem docelowym. Dbgmetric.lib obsługuje oba klucze. Podczas uzyskiwania danych, najpierw wyszukuje HKEY_CURRENT_USER, a następnie HKEY_LOCAL_MACHINE. Podczas ustawiania metryki parametr określa, który klucz najwyższego poziomu do użycia.

 *[klucz rejestru]*\

 `Software`\

 `Microsoft`\

 `VisualStudio`\

 *[katalog główny wersji]*\

 *[katalog główny metryki]*\

 *[typ metryki]*\

 *[metryka] = [wartość metryki]*

 *[metryka] = [wartość metryki]*

 *[metryka] = [wartość metryki]*

|Symbol zastępczy|Opis|
|-----------------|-----------------|
|*[klucz rejestru]*|`HKEY_CURRENT_USER` lub `HKEY_LOCAL_MACHINE`.|
|*[katalog główny wersji]*|Wersja programu Visual Studio (na przykład `7.0`, , `7.1`lub `8.0`). Jednak ten korzeń może być również modyfikowany za pomocą **przełącznika /rootsuffix** na **devenv.exe**. W przypadku usługi VSIP ten modyfikator jest zazwyczaj **Exp**, więc katalog główny wersji będzie, na przykład, 8.0Exp.|
|*[katalog główny metryki]*|Jest to `AD7Metrics` albo `AD7Metrics(Debug)`lub , w zależności od tego, czy używana jest wersja debugowania dbgmetric.lib. **Uwaga:**  Niezależnie od tego, czy jest używana dbgmetric.lib, ta konwencja nazewnictwa powinna być przestrzegana, jeśli występują różnice między wersjami debugowania i wersji, które muszą być odzwierciedlone w rejestrze.|
|*[typ metryki]*|Rodzaj metryki, która ma `Engine` `ExpressionEvaluator`być `SymbolProvider`napisana: , , , itp. Wszystkie są zdefiniowane jako w dbgmetric.h as `metricTypeXXXX`, gdzie `XXXX` jest określona nazwa typu.|
|*[metryczny]*|Nazwa wpisu, który ma być przypisany wartość w celu skonfigurowania metryki. Rzeczywista organizacja metryk zależy od typu metryki.|
|*[wartość metryki]*|Wartość przypisana do metryki. Typ, który wartość powinna mieć (ciąg, liczba itp.) zależy od metryki.|

> [!NOTE]
> Wszystkie identyfikatory GUID są `{GUID}`przechowywane w formacie . Na przykład `{123D150B-FA18-461C-B218-45B3E4589F9B}`.

### <a name="debug-engines"></a>Aparaty debugowania
 Poniżej przedstawiono organizację metryk aparatów debugowania w rejestrze. `Engine`jest nazwą typu metryki dla aparatu debugowania i odpowiada *[typ metryki]* w powyższym poddrzewie rejestru.

 `Engine`\

 *[identyfikator silnika]*\

 `CLSID` = *[class guid]*

 *[metryka] = [wartość metryki]*

 *[metryka] = [wartość metryki]*

 *[metryka] = [wartość metryki]*

 `PortSupplier`\

 `0` = *[guid dostawcy portu]*

 `1` = *[guid dostawcy portu]*

|Symbol zastępczy|Opis|
|-----------------|-----------------|
|*[identyfikator silnika]*|Identyfikator GUID aparatu debugowania.|
|*[class guid]*|Identyfikator GUID klasy, która implementuje ten aparat debugowania.|
|*[guid dostawcy portu]*|Identyfikator GUID dostawcy portu, jeśli istnieje. Wiele aparatów debugowania używa domyślnego dostawcy portu i dlatego nie określają własnego dostawcy. W takim przypadku podklucz `PortSupplier` będzie nieobecny.|

### <a name="port-suppliers"></a>Dostawcy portów
 Poniżej przedstawiono organizację metryk dostawcy portu w rejestrze. `PortSupplier`jest nazwą typu metryki dostawcy portu i odpowiada *[typ metryki]*.

 `PortSupplier`\

 *[guid dostawcy portu]*\

 `CLSID` = *[class guid]*

 *[metryka] = [wartość metryki]*

 *[metryka] = [wartość metryki]*

|Symbol zastępczy|Opis|
|-----------------|-----------------|
|*[guid dostawcy portu]*|Identyfikator GUID dostawcy portu|
|*[class guid]*|Identyfikator GUID klasy, która implementuje tego dostawcę portu|

### <a name="symbol-providers"></a>Dostawcy symboli
 Poniżej przedstawiono organizację metryk dostawcy symbolu w rejestrze. `SymbolProvider`jest nazwą typu metryki dla dostawcy symbolu i odpowiada *[typowi metryki]*.

 `SymbolProvider`\

 *[guid dostawcy symbolu]*\

 `file`\

 `CLSID` = *[class guid]*

 *[metryka] = [wartość metryki]*

 *[metryka] = [wartość metryki]*

 `metadata`\

 `CLSID` = *[class guid]*

 *[metryka] = [wartość metryki]*

 *[metryka] = [wartość metryki]*

|Symbol zastępczy|Opis|
|-----------------|-----------------|
|*[guid dostawcy symbolu]*|Identyfikator GUID dostawcy symboli|
|*[class guid]*|Identyfikator GUID klasy implementujejtatora tego symbolu|

### <a name="expression-evaluators"></a>Oceniający wyrażenia
 Poniżej przedstawiono organizację metryki oceniającego wyrażenie w rejestrze. `ExpressionEvaluator`jest nazwą typu metryki dla oceniającego wyrażenie i odpowiada *[typ metryki]*.

> [!NOTE]
> Typ metryki `ExpressionEvaluator` dla nie jest zdefiniowany w dbgmetric.h, ponieważ zakłada się, że wszystkie zmiany metryki dla oceniających wyrażenia przejdzie przez odpowiednie funkcje metryki oceniającego wyrażenie (układ `ExpressionEvaluator` podklucza jest nieco skomplikowany, więc szczegóły są ukryte wewnątrz dbgmetric.lib).

 `ExpressionEvaluator`\

 *[język guid]*\

 *[identyfikator dostawcy]*\

 `CLSID` = *[class guid]*

 *[metryka] = [wartość metryki]*

 *[metryka] = [wartość metryki]*

 `Engine`\

 `0` = *[identyfikator guid aparatu debugowania]*

 `1` = *[identyfikator guid aparatu debugowania]*

|Symbol zastępczy|Opis|
|-----------------|-----------------|
|*[język guid]*|Identyfikator GUID języka|
|*[identyfikator dostawcy]*|Identyfikator GUID dostawcy|
|*[class guid]*|Identyfikator GUID klasy implementująca tego oceniającego wyrażenie|
|*[identyfikator guid aparatu debugowania]*|Identyfikator GUID aparatu debugowania, z którymi działa ten oceniający wyrażenie|

### <a name="expression-evaluator-extensions"></a>Rozszerzenia oceniającego wyrażenia
 Poniżej przedstawiono organizację metryk rozszerzenia oceniającego wyrażenie w rejestrze. `EEExtensions`jest nazwą typu metryki dla rozszerzeń oceniającego wyrażenie i odpowiada *[typowi metryki]*.

 `EEExtensions`\

 *[identyfikator rozszerzenia]*\

 *[metryka] = [wartość metryki]*

 *[metryka] = [wartość metryki]*

|Symbol zastępczy|Opis|
|-----------------|-----------------|
|*[identyfikator rozszerzenia]*|Identyfikator GUID rozszerzenia oceniającego wyrażenie|

### <a name="exceptions"></a>Wyjątki
 Poniżej przedstawiono organizację metryk wyjątków w rejestrze. `Exception`jest nazwą typu metryki dla wyjątków i odpowiada *[typ metryki]*.

 `Exception`\

 *[identyfikator guid aparatu debugowania]*\

 *[typy wyjątków]*\

 *[wyjątek]*\

 *[metryka] = [wartość metryki]*

 *[metryka] = [wartość metryki]*

 *[wyjątek]*\

 *[metryka] = [wartość metryki]*

 *[metryka] = [wartość metryki]*

|Symbol zastępczy|Opis|
|-----------------|-----------------|
|*[identyfikator guid aparatu debugowania]*|Identyfikator GUID aparatu debugowania, który obsługuje wyjątki.|
|*[typy wyjątków]*|Tytuł ogólny podklucza identyfikujący klasę wyjątków, które mogą być obsługiwane. Typowe nazwy to **wyjątki języka C++,** **wyjątki Systemu Win32,** **wyjątki środowiska wykonawczego języka wspólnego**i **natywne kontrole czasu wykonywania.** Nazwy te są również używane do identyfikowania określonej klasy wyjątku dla użytkownika.|
|*[wyjątek]*|Nazwa wyjątku: na przykład **_com_error** lub **Control-Break**. Nazwy te są również używane do identyfikowania określonego wyjątku dla użytkownika.|

## <a name="requirements"></a>Wymagania
 Pliki te znajdują [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] się w katalogu instalacyjnym SDK (domyślnie *[drive]* \Program Files\Microsoft Visual Studio 2010 SDK\\).

 Nagłówek: zawiera\dbgmetric.h

 Biblioteka: libs\ad2de.lib, libs\dbgmetric.lib

## <a name="see-also"></a>Zobacz też
- [Dokumentacja interfejsu API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
