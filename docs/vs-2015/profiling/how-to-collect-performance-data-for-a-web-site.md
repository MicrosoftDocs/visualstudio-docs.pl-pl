---
title: 'Porady: zbieranie danych dotyczących wydajności dla witryny sieci Web | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.assetid: a62d27fd-a966-4065-bebe-6874195a71fb
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 646d5a59dee68123e478da074901c9d6f98c2763
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783912"
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Porady: zbieranie danych dotyczących wydajności dla witryny sieci Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz użyć **kreatora wydajności** do zbierania danych wydajności dla [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web. Można profilować aplikację internetową, która jest otwarta w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], lub można profilować [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] witryny sieci Web, który jest zlokalizowany na komputerze lokalnym i nie jest otwarty w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE.  
  
> [!NOTE]
>  **Kreatora wydajności** umożliwia dodawanie danych interakcji (TIP) i/lub JScript danych wydajności zebranych danych profilowania. Opcja Porada zbiera dane z procesów po stronie serwera. Profilowanie JScript zbiera dane ze skryptów, które są uruchomione na lokalnych lub zdalnych witryny sieci Web. W większości przypadków należy wybrać tylko jedną z opcji.  
  
 W zależności od ustawień uprawnień dostępu użytkowników, które administrator udostępnił użytkownik może być lub może nie mieć uprawnień do utworzenia sesji profilera na komputerze, który jest hostem procesu ASP.NET. Poniższe przykłady ilustrują możliwe różnice między użytkowników:  
  
- Niektórzy użytkownicy mogą uzyskiwać dostęp do zaawansowanych funkcji profilowania, gdy Administrator ustawił sterownik i uruchomienie usługi.  
  
- Użytkownicy domeny mogą uzyskiwać dostęp do przykładowej profilowanie tylko.  
  
- Niektórzy użytkownicy Moje Odmów dostępu do profilowania, aby wszyscy inni użytkownicy.  
  
  Aby uzyskać więcej informacji, zobacz [profilowania i Windows Vista zabezpieczeń](../profiling/profiling-and-windows-vista-security.md) i opcje administratora w [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-profile-a-web-site-project"></a>Aby przeprowadzić profilowanie projektu witryny sieci Web  
  
1.  Otwórz [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] projektu sieci Web w [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] lub [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].  
  
2.  Na **analizy** menu, kliknij przycisk **Uruchom Kreatora wydajności**.  
  
3.  Na pierwszej stronie kreatora, wybierz metody profilowania, a następnie kliknij przycisk **dalej**. Aby uzyskać więcej informacji na temat metod profilowania, zobacz [metodami zbierania danych wydajności opis](../profiling/understanding-performance-collection-methods.md). Należy zauważyć, że metoda profilowania narzędzie concurrency visualizer nie jest dostępna dla aplikacji sieci web.  
  
4.  W **aplikacji, które chcesz docelowe dla profilowania?** listy rozwijanej, upewnij się, że bieżący projekt jest wybrany, a następnie kliknij przycisk **dalej**.  
  
5.  Na trzeciej stronie kreatora możesz dodać dane interakcji między warstwami profilowania (TIP), dane z języka JavaScript w stronach sieci Web i / lub.  
  
    -   Aby zebrać interakcje między warstwami, zaznacz **Włącz profilowanie interakcji pomiędzy warstwami** pole wyboru.  
  
    -   Aby zebrać dane z kod JavaScript na stronach sieci Web, wybierz pozycję **Profiluj kod JavaScript** pole wyboru.  
  
6.  Kliknij przycisk **Dalej**.  
  
7.  Na czwartej stronie kreatora kliknij **Zakończ**.  
  
8.  Sesja wydajności jest tworzona dla [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji i witrynę sieci Web jest uruchomiony w przeglądarce. Przetestuj funkcjonalność, która ma być profilu, a następnie zamknij przeglądarkę.  
  
     Program profilujący generuje plik danych i wyświetla widok podsumowania danych w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] głównego okna.  
  
### <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Aby przeprowadzić profilowanie witryny sieci Web bez konieczności otwierania projektu w programie Visual Studio  
  
1. Otwórz [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] lub [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].  
  
2. Na **analizy** menu, kliknij przycisk **Uruchom Kreatora wydajności**.  
  
3. Na pierwszej stronie kreatora, wybierz metody profilowania, a następnie kliknij przycisk **dalej**. Aby uzyskać więcej informacji, zobacz [metodami zbierania danych wydajności opis](../profiling/understanding-performance-collection-methods.md).  
  
4. Na drugiej stronie kreatora wybierz **profil aplikacji ASP.NET lub JavaScript** opcji, a następnie kliknij przycisk **dalej**.  
  
5. W **jakim adresem URL lub ścieżką będzie działała aplikacja sieci web** na trzeciej stronie kreatora, wprowadź adres URL do strony głównej aplikacji, a następnie kliknij **dalej**.  
  
   - Dla witryny sieci Web oparte na serwerze (IIS), wpisz adres URL, taki jak **http://localhost/MySite/default.aspx**. Powoduje to, że [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji na komputerze lokalnym w katalogu głównym aplikacji MySite do profilowania i default.aspx strony w danej lokacji można uruchomić w przeglądarce Internet Explorer, aby rozpocząć sesję.  
  
   - Dla witryny sieci Web opartą na plikach, wpisz ścieżkę, taką jak pliku / / /**c:\WebSites\MySite\default.aspx**. Powoduje to, że [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji znajdującym się w c:\webSites\MySite do profilowania i strony http://localhost:nnnn/MySite/default.aspx mają być uruchamiane w programie Internet Explorer, aby rozpocząć sesję.  
  
   - Dla zewnętrznych witryn, które chcesz zbierać danych dotyczących JavaScript, wpisz adres URL, na przykład http://www.contoso.com.  
  
     Aby uzyskać więcej informacji, Wyświetl strony właściwości dla [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] docelowy plik binarny.  
  
6. Na trzeciej stronie kreatora możesz dodać dane interakcji między warstwami profilowania (TIP), dane z języka JavaScript w stronach sieci Web i / lub.  
  
   -   Aby zebrać interakcje między warstwami, zaznacz **Włącz profilowanie interakcji pomiędzy warstwami** pole wyboru.  
  
   -   Aby zebrać dane z kod JavaScript na stronach sieci Web, wybierz pozycję **Profiluj kod JavaScript** pole wyboru.  
  
7. Kliknij przycisk **Dalej**.  
  
8. Na czwartej stronie kreatora kliknij **Zakończ**.  
  
9. Sesja wydajności zostanie utworzony dla aplikacji ASP.NET, i witryny sieci Web jest uruchomiony w przeglądarce. Przetestuj funkcjonalność, która ma być profilu, a następnie zamknij przeglądarkę.  
  
     Program profilujący generuje plik danych i wyświetla widok podsumowania danych w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] głównego okna.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie](../profiling/overviews-performance-tools.md)   
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Zapoznanie z wartościami danych Instrumentacji](../profiling/understanding-instrumentation-data-values.md)   
 [Zapoznanie z wartościami danych próbkowania](../profiling/understanding-sampling-data-values.md)



