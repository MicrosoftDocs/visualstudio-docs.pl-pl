---
title: 'Porady: zbieranie danych dotyczących wydajności dla witryny sieci Web | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vsperf.url.url
- vsperf.chooseurl
- vs.performance.wizard.asppage
- vsperf.url.ok
- vsperf.url.cancel
helpviewer_keywords:
- Profiling Tools,profiling ASP.NET
- web sites, performance profiling
- ASP.NET, performance profilng
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8b5cacba328c48b682fe9069d8ab4a9ee21635db
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410180"
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Porady: zbieranie danych wydajności dotyczących witryny sieci web

Za pomocą **Kreatora wydajności** można zbierać dane wydajności dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web. Możesz profilować aplikację sieci Web, która jest otwarta w programie Visual Studio, lub można profilować [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] witrynę sieci Web, która znajduje się na komputerze lokalnym, a nie otwarta w środowisku IDE programu Visual Studio.

> [!NOTE]
> **Kreator wydajności** umożliwia dodawanie danych profilowania, danych dotyczących wydajności JScript lub obu do zebranych danych profilowych. Opcja Porada zbiera dane z procesów po stronie serwera. Profilowanie JScript zbiera dane ze skryptów, które są uruchomione na lokalnych lub zdalnych witryny sieci Web. W większości przypadków należy wybrać tylko jedną z opcji.

 W zależności od ustawień uprawnień dostępu użytkowników, które administrator udostępnił użytkownik może być lub może nie mieć uprawnień do utworzenia sesji profilera na komputerze, który jest hostem procesu ASP.NET. Poniższe przykłady ilustrują możliwe różnice między użytkowników:

- Niektórzy użytkownicy mogą uzyskiwać dostęp do zaawansowanych funkcji profilowania, gdy Administrator ustawił sterownik i uruchomienie usługi.

- Użytkownicy domeny mogą uzyskiwać dostęp do przykładowej profilowanie tylko.

- Niektórzy użytkownicy mogą uniemożliwić dostęp do profilowania, aby wszyscy inni użytkownicy.

  Aby uzyskać więcej informacji, zobacz [profilowanie i zabezpieczenia systemu Windows Vista](../profiling/profiling-and-windows-vista-security.md) oraz opcje administratora w programie [VSPerfCmd](../profiling/vsperfcmd.md).

## <a name="to-profile-a-web-site-project"></a>Aby przeprowadzić profilowanie projektu witryny sieci web

1. Otwórz projekt sieci Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] w programie Visual Studio.

2. W menu **Analizuj** wybierz pozycję **Profiler wydajności**, wybierz pozycję **Eksplorator wydajności**, a następnie wybierz pozycję **Uruchom**.

3. Na pierwszej stronie kreatora wybierz metodę profilowania, a następnie kliknij przycisk **dalej**. Aby uzyskać więcej informacji na temat metod profilowania, zobacz [Omówienie metod zbierania danych o wydajności](../profiling/understanding-performance-collection-methods.md). Należy zauważyć, że metoda profilowania narzędzie concurrency visualizer nie jest dostępna dla aplikacji sieci web.

4. W **której aplikacji chcesz określić profilowanie?** listę rozwijaną, upewnij się, że bieżący projekt jest wybrany, a następnie kliknij przycisk **dalej**.

5. Na trzeciej stronie kreatora możesz dodać dane interakcji między warstwami profilowania (TIP), dane z języka JavaScript w stronach sieci web i / lub.

    - Aby zbierać interakcje warstwy, zaznacz pole wyboru **Włącz profilowanie interakcji między warstwami** .

    - Aby zbierać dane z kodu JavaScript działającego na stronach sieci Web, zaznacz pole wyboru **profil JavaScript** .

6. Kliknij przycisk **Dalej**.

7. Na czwartej stronie kreatora kliknij przycisk **Zakończ**.

8. Dla aplikacji [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] tworzona jest sesja wydajności, a witryna sieci Web jest uruchamiana w przeglądarce. Przetestuj funkcjonalność, która ma być profilu, a następnie zamknij przeglądarkę.

     Profiler generuje plik danych i wyświetla widok podsumowania danych w oknie głównym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Aby przeprowadzić profilowanie witryny sieci web bez konieczności otwierania projektu w programie Visual Studio

1. Otwórz program Visual Studio.

2. W menu **Analizuj** wybierz pozycję **Profiler wydajności**, wybierz pozycję **Eksplorator wydajności**, a następnie wybierz pozycję **Uruchom**.

3. Na pierwszej stronie kreatora wybierz metodę profilowania, a następnie kliknij przycisk **dalej**. Aby uzyskać więcej informacji, zobacz [Omówienie metod zbierania danych o wydajności](../profiling/understanding-performance-collection-methods.md).

4. Na drugiej stronie kreatora wybierz opcję **profilu aplikacji ASP.NET lub JavaScript** , a następnie kliknij przycisk **dalej**.

5. W polu **adres URL lub ścieżka spowoduje uruchomienie aplikacji sieci Web** na trzeciej stronie kreatora wprowadź adres URL strony głównej aplikacji, a następnie kliknij przycisk **dalej**.

   - W przypadku witryny sieci Web opartej na serwerze (IIS) wpisz adres URL, taki jak **<`http://localhost/MySite/default.aspx`>** . Powoduje to, że aplikacja [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] na komputerze lokalnym w katalogu głównym aplikacji witryny Moja witryna zostanie profilowana, a strona default. aspx w tej witrynie zostanie uruchomiona w programie Internet Explorer w celu uruchomienia sesji.

   - W przypadku witryny sieci Web opartej na plikach wpisz ścieżkę, taką jak File///**c:\WebSites\MySite\default.aspx**. Powoduje to, że aplikacja [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] zlokalizowana w c:\webSites\MySite ma być profilowana, a strona `http://localhost:nnnn/MySite/default.aspx` zostanie uruchomiona w programie Internet Explorer w celu uruchomienia sesji.

   - W przypadku witryn zewnętrznych, na których mają być zbierane dane JavaScript, wpisz adres URL, na przykład `http://www.contoso.com`.

     Aby uzyskać więcej informacji, Wyświetl strony właściwości dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] docelowego pliku binarnego.

6. Na trzeciej stronie kreatora możesz dodać dane interakcji między warstwami profilowania (TIP), dane z języka JavaScript w stronach sieci web i / lub.

    - Aby zbierać interakcje warstwy, zaznacz pole wyboru **Włącz profilowanie interakcji między warstwami** .

    - Aby zbierać dane z kodu JavaScript działającego na stronach sieci Web, zaznacz pole wyboru **profil JavaScript** .

7. Kliknij przycisk **Dalej**.

8. Na czwartej stronie kreatora kliknij przycisk **Zakończ**.

9. Sesja wydajności zostanie utworzony dla aplikacji ASP.NET, i witryny sieci web jest uruchomiony w przeglądarce. Przetestuj funkcjonalność, która ma być profilu, a następnie zamknij przeglądarkę.

     Profiler generuje plik danych i wyświetla widok podsumowania danych w oknie głównym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Zobacz też

[Przeglądy](../profiling/overviews-performance-tools.md)
[konfigurowania sesji wydajności](../profiling/configuring-performance-sessions.md)
[zrozumienia wartości danych Instrumentacji](../profiling/understanding-instrumentation-data-values.md)
[poznać wartości danych próbkowania](../profiling/understanding-sampling-data-values.md)
