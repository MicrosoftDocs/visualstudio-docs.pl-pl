---
title: 'Instrukcje: Zbieranie danych dotyczących wydajności dla witryny sieci Web | Dokumentacja firmy Microsoft'
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
ms.workload:
- multiple
ms.openlocfilehash: f91646575fba2df1f48c08adc7a9233bb63f27df
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630487"
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Instrukcje: Zbieranie danych wydajności dotyczących witryny sieci web

Możesz użyć **kreatora wydajności** do zbierania danych wydajności dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web. Można profilować aplikacji sieci web, która jest otwarta w programie Visual Studio lub można profilować [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] witryny sieci Web, który znajduje się na komputerze lokalnym i nie jest otwarty w programie Visual Studio IDE.

> [!NOTE]
> **Kreatora wydajności** umożliwia dodawanie danych interakcji (TIP) i/lub JScript danych wydajności zebranych danych profilowania. Opcja Porada zbiera dane z procesów po stronie serwera. Profilowanie JScript zbiera dane ze skryptów, które są uruchomione na lokalnych lub zdalnych witryny sieci Web. W większości przypadków należy wybrać tylko jedną z opcji.

 W zależności od ustawień uprawnień dostępu użytkowników, które administrator udostępnił użytkownik może być lub może nie mieć uprawnień do utworzenia sesji profilera na komputerze, który jest hostem procesu ASP.NET. Poniższe przykłady ilustrują możliwe różnice między użytkowników:

- Niektórzy użytkownicy mogą uzyskiwać dostęp do zaawansowanych funkcji profilowania, gdy Administrator ustawił sterownik i uruchomienie usługi.

- Użytkownicy domeny mogą uzyskiwać dostęp do przykładowej profilowanie tylko.

- Niektórzy użytkownicy mogą uniemożliwić dostęp do profilowania, aby wszyscy inni użytkownicy.

  Aby uzyskać więcej informacji, zobacz [zabezpieczeń profilowania i Windows Vista](../profiling/profiling-and-windows-vista-security.md) i opcje administratora w [VSPerfCmd](../profiling/vsperfcmd.md).

## <a name="to-profile-a-web-site-project"></a>Aby przeprowadzić profilowanie projektu witryny sieci web

1. Otwórz [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] projektu sieci Web w programie Visual Studio.

2. Na **analizy** menu, wybierz opcję **Profiler wydajności**, wybierz opcję **Eksplorator wydajności**, a następnie wybierz pozycję **Start**.

3. Na pierwszej stronie kreatora, wybierz metody profilowania, a następnie kliknij przycisk **dalej**. Aby uzyskać więcej informacji na temat metod profilowania, zobacz [zrozumieć metodami zbierania danych wydajności](../profiling/understanding-performance-collection-methods.md). Należy zauważyć, że metoda profilowania narzędzie concurrency visualizer nie jest dostępna dla aplikacji sieci web.

4. W **aplikacji, które chcesz docelowe dla profilowania?** listy rozwijanej, upewnij się, że bieżący projekt jest wybrany, a następnie kliknij przycisk **dalej**.

5. Na trzeciej stronie kreatora możesz dodać dane interakcji między warstwami profilowania (TIP), dane z języka JavaScript w stronach sieci web i / lub.

    - Aby zebrać interakcje między warstwami, zaznacz **Włącz profilowanie interakcji pomiędzy warstwami** pole wyboru.

    - Aby zebrać dane z kod JavaScript na stronach sieci Web, wybierz pozycję **Profiluj kod JavaScript** pole wyboru.

6. Kliknij przycisk **Dalej**.

7. Na czwartej stronie kreatora kliknij **Zakończ**.

8. Sesja wydajności jest tworzona dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji i witrynę sieci web jest uruchomiony w przeglądarce. Przetestuj funkcjonalność, która ma być profilu, a następnie zamknij przeglądarkę.

     Program profilujący generuje plik danych i wyświetla widok podsumowania danych w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] głównego okna.

## <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Aby przeprowadzić profilowanie witryny sieci web bez konieczności otwierania projektu w programie Visual Studio

1. Otwórz program Visual Studio.

2. Na **analizy** menu, wybierz opcję **Profiler wydajności**, wybierz opcję **Eksplorator wydajności**, a następnie wybierz pozycję **Start**.

3. Na pierwszej stronie kreatora, wybierz metody profilowania, a następnie kliknij przycisk **dalej**. Aby uzyskać więcej informacji, zobacz [metodami zbierania danych wydajności opis](../profiling/understanding-performance-collection-methods.md).

4. Na drugiej stronie kreatora wybierz **profil aplikacji ASP.NET lub JavaScript** opcji, a następnie kliknij przycisk **dalej**.

5. W **jakim adresem URL lub ścieżką będzie działała aplikacja sieci web** na trzeciej stronie kreatora, wprowadź adres URL do strony głównej aplikacji, a następnie kliknij **dalej**.

   - Dla witryny sieci Web oparte na serwerze (IIS), wpisz adres URL, taki jak **< `http://localhost/MySite/default.aspx` >**. Powoduje to, że [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji na komputerze lokalnym w katalogu głównym aplikacji MySite do profilowania i default.aspx strony w danej lokacji można uruchomić w przeglądarce Internet Explorer, aby rozpocząć sesję.

   - Dla witryny sieci Web opartą na plikach, wpisz ścieżkę, taką jak pliku / / /**c:\WebSites\MySite\default.aspx**. Powoduje to, że [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji znajdującym się w c:\webSites\MySite do profilowania i strony `http://localhost:nnnn/MySite/default.aspx` mają być uruchamiane w programie Internet Explorer, aby rozpocząć sesję.

   - Dla zewnętrznych witryn, które chcesz zbierać danych dotyczących JavaScript, wpisz adres URL, na przykład `http://www.contoso.com`.

     Aby uzyskać więcej informacji, Wyświetl strony właściwości dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] docelowy plik binarny.

6. Na trzeciej stronie kreatora możesz dodać dane interakcji między warstwami profilowania (TIP), dane z języka JavaScript w stronach sieci web i / lub.

    - Aby zebrać interakcje między warstwami, zaznacz **Włącz profilowanie interakcji pomiędzy warstwami** pole wyboru.

    - Aby zebrać dane z kod JavaScript na stronach sieci web, wybierz pozycję **Profiluj kod JavaScript** pole wyboru.

7. Kliknij przycisk **Dalej**.

8. Na czwartej stronie kreatora kliknij **Zakończ**.

9. Sesja wydajności zostanie utworzony dla aplikacji ASP.NET, i witryny sieci web jest uruchomiony w przeglądarce. Przetestuj funkcjonalność, która ma być profilu, a następnie zamknij przeglądarkę.

     Program profilujący generuje plik danych i wyświetla widok podsumowania danych w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] głównego okna.

## <a name="see-also"></a>Zobacz także

[Omówienie](../profiling/overviews-performance-tools.md)
[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
[zrozumieć wartościami danych Instrumentacji](../profiling/understanding-instrumentation-data-values.md)
[omówienie z wartościami danych próbkowania](../profiling/understanding-sampling-data-values.md)
