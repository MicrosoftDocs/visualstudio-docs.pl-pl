---
title: VSPerfCLREnv | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command-line tools, VSPerfCLREnv
- command line, tools
- performance tools, VSPerfCLREnv
- profiling tools,VSPerfCLREnv
- VSPerfCLREnv tool
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c063d0df3f874e232f33121dbc8f6015a3c0fc3a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946792"
---
# <a name="vsperfclrenv"></a>VSPerfCLREnv

Vsperfclrenv — narzędzie służy do ustawiania zmiennych środowiskowych, które są wymagane do profilu aplikacji .NET Framework. Używa następującej składni:

```cmd
VsPerfCLREnv [/option]
```

Możesz wybrać opcję zależy od tego, której te trzy rodzaje profilowania, należy użyć: próbkowanie, Instrumentacja, lub globalnego. Osobną opcją jest wymagany do uwzględnienia danych o interakcji między warstwami w danych profilowania. W poniższych tabelach opisano składnię dla każdej opcji.

> [!NOTE]
> Po zakończeniu profilowania, uruchom **VSPerfCLREnv** z **/ off** lub **/globaloff** możliwość usuwanie zmiennych środowiskowych niezbędnych do profilowania. Aby uzyskać więcej informacji zobacz Opcje polecenia VSPerfCLREnv do ustawienia środowiska Usuń pokazano poniżej.

## <a name="vsperfclrenv-options-for-including-tier-interaction-data"></a>Opcje polecenia VSPerfCLREnv, w tym dane interakcji między warstwami

> [!WARNING]
> Profilowanie interakcji między warstwami można zbierać w programach dowolnej wersji programu Visual Studio. Natomiast obejrzeć takie dane można wyświetlać tylko w programie Visual Studio Enterprise.

Profilowanie interakcji pomiędzy warstwami zawiera dodatkowe informacje na temat zapytań ADO.NET w aplikacjach wielowarstwowych. Dane są zbierane tylko w przypadku wywołania funkcji synchronicznej. Dane interakcji między można dodać do dowolnej profilowania przy użyciu dowolnej metody profilowania.

**InteractionOn** i **GlobalInteractionOn** opcje włączyć zbieranie danych o interakcji między warstwami. Opcja interakcji musi być ustawiona, po ustawienie zmiennej środowiskowej VSPerfCLREnv, który jest wymagany do profilu aplikacji.

Poniższy przykład zawiera dane interakcji między warstwami do uruchomienia profilowania, która używa metody pobierania próbek:

```cmd
VSPerfCLREnv /SampleOn
VSPerfCLREnv /InteractionOn
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe
```

Poniższy przykład zawiera dane interakcji między warstwami do uruchomienia profilowania dla usługi Windows:

```cmd
VSPerfCLREnv /GlobalSampleOn
VSPerfCLREnv /GlobalInteractionOn
REM Restart the computer and start the service
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp 
VSPerfCmd /Attach:MyService.exe
```

## <a name="vsperfclrenv-options-for-process-instrumentation-profiling"></a>Opcje polecenia VSPerfCLREnv do profilowania Instrumentacji procesu

W poniższej tabeli opisano opcje polecenia VSPerfCLREnv do profilowania Instrumentacji:

|Opcja|Opis|
|------------|-----------------|
|**TraceOn**|Włącza profilowanie przy użyciu metody instrumentacji. Nie uwzględnia alokacji pamięci profilowania, lub zbieranie danych o okresie istnienia obiektu.|
|**TraceGC**|Włącza profilowanie przydziału pamięci przy użyciu metody instrumentacji. Włącza zbieranie danych o okresie istnienia obiektu.|
|**TraceGCLife**|Umożliwia przydzielanie pamięci, profilowanie i zbieranie danych o okresie istnienia obiektu przy użyciu metody instrumentacji.|

## <a name="vsperfclrenv-options-for-process-sampling-profiling"></a>Opcje polecenia VSPerfCLREnv do procesu pobierania próbek profilowania

W poniższej tabeli opisano opcje polecenia VSPerfCLREnv profilowanie próbkowania:

|Opcja|Opis|
|------------|-----------------|
|**SampleOn**|Włącza profilowanie przy użyciu metody pobierania próbek. Nie uwzględnia alokacji pamięci profilowania, lub zbieranie danych o okresie istnienia obiektu.|
|**SampleGC**|Włącza profilowanie przydziału pamięci przy użyciu metody próbkowania. Włącza zbieranie danych o okresie istnienia obiektu.|
|**SampleGCLife**|Włącza profilowanie przydziału pamięci przy użyciu metody próbkowania. Umożliwia również zbieranie danych o okresie istnienia obiektu.|
|**SampleLineOff**|Wyłącza kolekcję .NET profilowania danych na poziomie wiersza.|

## <a name="vsperfclrenv-options-for-global-profiling"></a>Opcje polecenia VSPerfCLREnv do globalnego profilowania

Profilowanie usług zarządzanych, takich jak i aplikacji sieci web ASP.NET, który jest uruchamiany przez system operacyjny, a nie jest uruchomiony przez użytkownika, należy użyć opcji pod kątem globalnego profilowania opcji polecenia VSPerfCLREnv. W poniższej tabeli opisano globalnego wersje VSPerfCLREnv opcje. Te opcje ustawić odpowiednie zmienne środowiskowe w rejestrze.

|Opcja|Opis|
|------------|-----------------|
|**GlobalTraceOn**|Włącza profilowanie globalnego przy użyciu metody instrumentacji. Zbiera zdarzenia alokacji pamięci ani danych o okresie istnienia obiektu.|
|**GlobalTraceGC**|Włącza profilowanie przydziału pamięci globalnej przy użyciu metody instrumentacji. Włącza zbieranie danych o okresie istnienia obiektu.|
|**GlobalTraceGCLife**|Włącza profilowanie przydziału pamięci globalnej przy użyciu metody instrumentacji. Umożliwia także zbierania danych o okresie istnienia obiektu.|
|**GlobalSampleOn**|Umożliwia globalny profilowania przy użyciu metody próbkowania. Nie umożliwi zbieranie zdarzeń alokacji pamięci lub danych o okresie istnienia obiektu.|
|**GlobalSampleGC**|Włącza profilowanie przydziału pamięci globalnej przy użyciu metody próbkowania. Włącza zbieranie danych o okresie istnienia obiektu.|
|**GlobalSampleGCLife**|Włącza profilowanie przydziału pamięci globalnej przy użyciu metody próbkowania. Umożliwia również zbieranie danych o okresie istnienia obiektu.|

## <a name="vsperfclrenv-options-to-delete-environment-settings"></a>Opcje polecenia VSPerfCLREnv do usunięcia ustawień środowiska

 Po zakończeniu profilowania aplikacji zarządzanej użyj jednej z następujących opcji, aby usunąć zmienne środowiskowe, które zostały dodane przez VSPerfCLREnv. W poniższej tabeli opisano sposób usuwania obu zmiennych środowiskowych standardowe i globalne:

|Opcja|Opis|
|------------|-----------------|
|**Off**|Usuwa zmienne środowiskowe profilowania .NET standard. Użyj tej opcji, gdy nieglobalnych opcje polecenia VSPerfClrEnv były używane do ustawiania zmiennych środowiskowych programu profilującego.|
|**GlobalOff**|Usuwa zmienne środowiskowe globalnego profilowania platformy .NET. Użyj tej opcji podczas uruchomienia aplikacji według systemu operacyjnego i nie profilera.|

## <a name="remarks"></a>Uwagi

Te opcje nie są wymagane do profilowania aplikacji zarządzanej, gdy aplikacja zostanie uruchomiona przy użyciu Eksploratora wydajności w środowisku IDE. Eksplorator wydajności Ustawia wszystkie ustawienia wymagane środowisko dla Ciebie.

Jeśli odpowiednie środowisko nie została ustawiona podczas profilowania, ostrzeżenie jest zgłaszane podczas analizy i funkcji zarządzanej, których nazwy nie będą prawidłowo rozpoznawane.

## <a name="see-also"></a>Zobacz także

[Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)