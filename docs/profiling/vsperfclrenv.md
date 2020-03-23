---
title: VSPerfCLREnv | Dokumenty firmy Microsoft
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2163ebb9b363de8ee638998dbe56fd76f5a891c8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779912"
---
# <a name="vsperfclrenv"></a>VSPerfCLREnv

Narzędzie VSPerfCLREnv służy do ustawiania zmiennych środowiskowych, które są wymagane do profilu aplikacji .NET Framework. Używa następującej składni:

```cmd
VsPerfCLREnv [/option]
```

Wybrana opcja zależy od tego, który z trzech typów profilowania jest używany: próbkowanie, instrumentacja lub globalne. Oddzielna opcja jest wymagana do uwzględnienia danych interakcji warstwy w danych profilowania. Składnia dla każdej opcji jest opisana w poniższych tabelach.

> [!NOTE]
> Po zakończeniu profilowania uruchom **program VSPerfCLREnv** z opcją **/off** lub **/globaloff,** aby usunąć zmienne środowiskowe niezbędne do profilowania. Aby uzyskać więcej informacji, zobacz Opcje VSPerfCLREnv, aby usunąć ustawienia środowiska pokazane tutaj.

## <a name="vsperfclrenv-options-for-including-tier-interaction-data"></a>Opcje VSPerfCLREnv obejmujące dane interakcji warstwy

> [!WARNING]
> Profilowanie interakcji warstwy mogą być zbierane przy użyciu dowolnej wersji programu Visual Studio. Jednak dane profilowania interakcji warstwy można wyświetlać tylko w programie Visual Studio Enterprise.

Profilowanie interakcji warstwy zawiera dodatkowe informacje na temat ADO.NET zapytań w aplikacjach wielowarstwowych. Dane są zbierane tylko dla wywołań funkcji synchronicznych. Dane interakcji mogą być dodawane do dowolnego profilowania uruchamiane przy użyciu dowolnej metody profilowania.

Opcje **InteractionOn** i **GlobalInteractionOn** umożliwiają zbieranie danych interakcji warstwy. Opcja interakcji musi być ustawiona po ustawieniu zmiennej środowiskowej VSPerfCLREnv, która jest wymagana do profilu aplikacji.

Poniższy przykład zawiera dane interakcji warstwy w przebiegu profilowania, który używa metody próbkowania:

```cmd
VSPerfCLREnv /SampleOn
VSPerfCLREnv /InteractionOn
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe
```

Poniższy przykład zawiera dane interakcji warstwy w profilowania uruchomić dla usługi systemu Windows:

```cmd
VSPerfCLREnv /GlobalSampleOn
VSPerfCLREnv /GlobalInteractionOn
REM Restart the computer and start the service
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp
VSPerfCmd /Attach:MyService.exe
```

## <a name="vsperfclrenv-options-for-process-instrumentation-profiling"></a>Opcje VSPerfCLREnv do profilowania instrumentacji procesu

W poniższej tabeli opisano opcje VSPerfCLREnv do profilowania instrumentacji:

|Opcja|Opis|
|------------|-----------------|
|**Traceon**|Umożliwia profilowanie przy użyciu metody instrumentacji. Nie włącza profilowania alokacji pamięci lub zbierania danych okresu istnienia obiektu.|
|**TraceGC (WYT.**|Umożliwia profilowanie alokacji pamięci przy użyciu metody instrumentacji. Nie włącza zbierania danych okresu istnienia obiektu.|
|**TraceGCLife (Firma TraceGCLife)**|Umożliwia profilowanie alokacji pamięci i zbieranie danych okresu istnienia obiektu przy użyciu metody instrumentacji.|

## <a name="vsperfclrenv-options-for-process-sampling-profiling"></a>Opcje VSPerfCLREnv do profilowania próbkowania procesów

W poniższej tabeli opisano opcje VSPerfCLREnv do profilowania próbkowania:

|Opcja|Opis|
|------------|-----------------|
|**SampleOn (Przykład)**|Umożliwia profilowanie przy użyciu metody próbkowania. Nie włącza profilowania alokacji pamięci lub zbierania danych okresu istnienia obiektu.|
|**SampleGC (Pobieranie próbek)**|Umożliwia profilowanie alokacji pamięci przy użyciu metody próbkowania. Nie włącza zbierania danych okresu istnienia obiektu.|
|**SampleGCLife**|Umożliwia profilowanie alokacji pamięci przy użyciu metody próbkowania. Umożliwia również zbieranie danych okresu istnienia obiektu.|
|**SampleLineOff (Przykładowy odjazd)**|Wyłącza zbieranie danych profilowania na poziomie wiersza .NET.|

## <a name="vsperfclrenv-options-for-global-profiling"></a>Opcje VSPerfCLREnv dla profilowania globalnego

Aby profilować usługę zarządzaną, taką jak i ASP.NET aplikacji sieci web, która jest uruchamiana przez system operacyjny, a nie uruchamiana przez użytkownika, należy użyć opcji globalnego profilowania opcji VSPerfCLREnv. W poniższej tabeli opisano globalne wersje opcji VSPerfCLREnv. Te opcje ustawiają odpowiednie zmienne środowiskowe w rejestrze.

|Opcja|Opis|
|------------|-----------------|
|**GlobalTraceOn (GlobalTraceOn)**|Umożliwia profilowanie globalne przy użyciu metody instrumentacji. Nie zbiera zdarzeń alokacji pamięci ani danych okresu istnienia obiektu.|
|**GlobalTraceGC**|Umożliwia profilowanie alokacji pamięci globalnej przy użyciu metody instrumentacji. Nie włącza zbierania danych okresu istnienia obiektu.|
|**GlobalTraceGCLife**|Umożliwia profilowanie alokacji pamięci globalnej przy użyciu metody instrumentacji. Umożliwia również zbieranie danych okresu istnienia obiektu.|
|**GlobalSampleOn (GlobalSampleOn)**|Umożliwia profilowanie globalne przy użyciu metody próbkowania. Nie umożliwia zbierania zdarzeń alokacji pamięci lub danych okresu istnienia obiektu.|
|**GlobalSampleGC (GlobalSampleGC)**|Umożliwia profilowanie alokacji pamięci globalnej przy użyciu metody próbkowania. Nie włącza zbierania danych okresu istnienia obiektu.|
|**GlobalSampleGCLife**|Umożliwia profilowanie alokacji pamięci globalnej przy użyciu metody próbkowania. Umożliwia również zbieranie danych okresu istnienia obiektu.|

## <a name="vsperfclrenv-options-to-delete-environment-settings"></a>Opcje VSPerfCLREnv do usuwania ustawień środowiska

 Po zakończeniu profilowania aplikacji zarządzanej użyj jednej z następujących opcji, aby usunąć zmienne środowiskowe, które zostały dodane przez VSPerfCLREnv. W poniższej tabeli opisano sposób usuwania zarówno standardowych, jak i globalnych zmiennych środowiskowych:

|Opcja|Opis|
|------------|-----------------|
|**Wyłączone**|Usuwa zmienne środowiskowe dla standardowego profilowania .NET. Użyj tej opcji, gdy nieglobalne opcje VSPerfClrEnv zostały użyte do ustawienia zmiennych środowiskowych profilera.|
|**Globaloff**|Usuwa zmienne środowiskowe dla globalnego profilowania .NET. Użyj tej opcji, gdy aplikacja została uruchomiona przez system operacyjny, a nie profiler.|

## <a name="remarks"></a>Uwagi

Te opcje nie są wymagane do profilowania aplikacji zarządzanej, jeśli aplikacja jest uruchomiona przy użyciu Eksploratora wydajności w IDE. Eksplorator wydajności ustawia wszystkie wymagane ustawienia środowiska.

Jeśli podczas profilowania nie ustawiono prawidłowego środowiska, podczas analizy jest zgłaszane ostrzeżenie, a nazwy funkcji zarządzanych nie zostaną poprawnie rozpoznane.

## <a name="see-also"></a>Zobacz też

[Profil z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)
