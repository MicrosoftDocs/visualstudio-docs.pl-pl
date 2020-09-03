---
title: VSPerfCLREnv | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command-line tools, VSPerfCLREnv
- command line, tools
- performance tools, VSPerfCLREnv
- profiling tools,VSPerfCLREnv
- VSPerfCLREnv tool
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 828768b59e4ab465e4723d399d406b994fa8c8ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330430"
---
# <a name="vsperfclrenv"></a>VSPerfCLREnv

Narzędzie VSPerfCLREnv służy do ustawiania zmiennych środowiskowych, które są wymagane do profilowania aplikacji .NET Framework. Używa następującej składni:

```cmd
VsPerfCLREnv [/option]
```

Wybrana opcja zależy od tego, które z trzech typów profilowania są używane: próbkowanie, Instrumentacja lub globalne. Aby uwzględnić dane interakcji warstwy w danych profilowania, wymagana jest osobna opcja. Składnia dla każdej opcji jest opisana w poniższych tabelach.

> [!NOTE]
> Po zakończeniu profilowania Uruchom polecenie **VSPerfCLREnv** z opcją **/off** lub **/GlobalOff** , aby usunąć zmienne środowiskowe niezbędne do profilowania. Aby uzyskać więcej informacji, zobacz Opcje VSPerfCLREnv, aby usunąć ustawienia środowiska pokazane w tym miejscu.

## <a name="vsperfclrenv-options-for-including-tier-interaction-data"></a>Opcje VSPerfCLREnv do dołączania danych interakcji między warstwami

> [!WARNING]
> Profilowanie interakcji między warstwami można zbierać przy użyciu dowolnej wersji programu Visual Studio. Jednak dane profilowania interakcji między warstwami mogą być wyświetlane tylko w Visual Studio Enterprise.

Profilowanie interakcji między warstwami zawiera dodatkowe informacje na temat zapytań ADO.NET w aplikacjach wielowarstwowych. Dane są zbierane tylko dla wywołań funkcji synchronicznych. Dane interakcji można dodać do dowolnego przebiegu profilowania przy użyciu dowolnej metody profilowania.

Opcje **InteractionOn** i **GlobalInteractionOn** umożliwiają zbieranie danych o interakcji między warstwami. Opcja interakcji musi być ustawiona po ustawieniu zmiennej środowiskowej VSPerfCLREnv, która jest wymagana do profilowania aplikacji.

Poniższy przykład obejmuje dane interakcji warstwy w przebiegu profilowania, który używa metody próbkowania:

```cmd
VSPerfCLREnv /SampleOn
VSPerfCLREnv /InteractionOn
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe
```

Poniższy przykład obejmuje dane interakcji warstwy w przebiegu profilowania dla usługi systemu Windows:

```cmd
VSPerfCLREnv /GlobalSampleOn
VSPerfCLREnv /GlobalInteractionOn
REM Restart the computer and start the service
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp
VSPerfCmd /Attach:MyService.exe
```

## <a name="vsperfclrenv-options-for-process-instrumentation-profiling"></a>Opcje VSPerfCLREnv dla profilowania Instrumentacji procesów

W poniższej tabeli opisano opcje VSPerfCLREnv dla profilowania Instrumentacji:

|Opcja|Opis|
|------------|-----------------|
|**TraceOn**|Włącza profilowanie przy użyciu metody instrumentacji. Nie włącza profilowania alokacji pamięci ani nie zbiera danych o okresie istnienia obiektu.|
|**TraceGC**|Włącza profilowanie alokacji pamięci za pomocą metody instrumentacji. Nie włącza zbierania danych o okresie istnienia obiektu.|
|**TraceGCLife**|Włącza profilowanie alokacji pamięci i gromadzenie danych o okresie istnienia obiektów przy użyciu metody instrumentacji.|

## <a name="vsperfclrenv-options-for-process-sampling-profiling"></a>Opcje VSPerfCLREnv dla profilowania próbkowania procesu

W poniższej tabeli opisano opcje VSPerfCLREnv na potrzeby profilowania próbkowania:

|Opcja|Opis|
|------------|-----------------|
|**SampleOn**|Włącza profilowanie przy użyciu metody próbkowania. Nie włącza profilowania alokacji pamięci ani nie zbiera danych o okresie istnienia obiektu.|
|**SampleGC**|Włącza profilowanie alokacji pamięci przy użyciu metody próbkowania. Nie włącza zbierania danych o okresie istnienia obiektu.|
|**SampleGCLife**|Włącza profilowanie alokacji pamięci przy użyciu metody próbkowania. Umożliwia również zbieranie danych o okresie istnienia obiektu.|
|**SampleLineOff**|Wyłącza zbieranie danych profilowania na poziomie wiersza platformy .NET.|

## <a name="vsperfclrenv-options-for-global-profiling"></a>Opcje VSPerfCLREnv dla profilowania globalnego

Aby profilować usługę zarządzaną, taką jak i ASP.NET aplikację sieci Web, która jest uruchamiana przez system operacyjny zamiast uruchamiania przez użytkownika, należy użyć opcji globalnego profilowania opcji VSPerfCLREnv. W poniższej tabeli opisano globalne wersje opcji VSPerfCLREnv. Te opcje ustawiają odpowiednie zmienne środowiskowe w rejestrze.

|Opcja|Opis|
|------------|-----------------|
|**GlobalTraceOn**|Włącza profilowanie globalne przy użyciu metody instrumentacji. Nie zbiera zdarzeń alokacji pamięci lub danych o okresie istnienia obiektu.|
|**GlobalTraceGC**|Włącza profilowanie alokacji pamięci globalnej przy użyciu metody instrumentacji. Nie włącza zbierania danych o okresie istnienia obiektu.|
|**GlobalTraceGCLife**|Włącza profilowanie alokacji pamięci globalnej przy użyciu metody instrumentacji. Umożliwia również zbieranie danych o okresie istnienia obiektu.|
|**GlobalSampleOn**|Włącza profilowanie globalne przy użyciu metody próbkowania. Nie włącza zbierania danych o zdarzeniach alokacji pamięci lub okresie istnienia obiektu.|
|**GlobalSampleGC**|Włącza profilowanie alokacji pamięci globalnej przy użyciu metody próbkowania. Nie włącza zbierania danych o okresie istnienia obiektu.|
|**GlobalSampleGCLife**|Włącza profilowanie alokacji pamięci globalnej przy użyciu metody próbkowania. Umożliwia również zbieranie danych o okresie istnienia obiektu.|

## <a name="vsperfclrenv-options-to-delete-environment-settings"></a>VSPerfCLREnv opcje usuwania ustawień środowiska

 Po zakończeniu profilowania aplikacji zarządzanej Użyj jednej z następujących opcji, aby usunąć zmienne środowiskowe, które zostały dodane przez VSPerfCLREnv. W poniższej tabeli opisano, jak usunąć standardowe i globalne zmienne środowiskowe:

|Opcja|Opis|
|------------|-----------------|
|**Wyłączone**|Usuwa zmienne środowiskowe dla standardowego profilowania platformy .NET. Użyj tej opcji, jeśli opcje VSPerfClrEnv inne niż globalne zostały użyte do ustawienia zmiennych środowiskowych profilera.|
|**GlobalOff**|Usuwa zmienne środowiskowe dla globalnego profilowania platformy .NET. Użyj tej opcji, jeśli aplikacja została uruchomiona przez system operacyjny, a nie Profiler.|

## <a name="remarks"></a>Uwagi

Te opcje nie są wymagane do profilowania aplikacji zarządzanej, jeśli aplikacja jest uruchomiona przy użyciu Eksplorator wydajności w IDE. Eksplorator wydajności ustawia wszystkie wymagane ustawienia środowiska.

Jeśli podczas profilowania nie zostało ustawione prawidłowe środowisko, podczas analizy zostanie zgłoszone ostrzeżenie, a nazwy funkcji zarządzanych nie zostaną prawidłowo rozwiązane.

## <a name="see-also"></a>Zobacz też

[Profil z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)
