---
title: 'Instrukcje: zbieranie danych wydajności dla witryny sieci Web | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
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
ms.assetid: a62d27fd-a966-4065-bebe-6874195a71fb
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3307b5372852d6f3e269264a02fa2c90cb1acd22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64787030"
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Instrukcje: zbieranie danych wydajności dla witryny sieci Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą **Kreatora wydajności** można zbierać dane dotyczące wydajności [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web. Można profilować aplikację sieci Web, która jest otwarta w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , lub można profilować [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] witrynę sieci Web, która znajduje się na komputerze lokalnym, a nie otwarta w środowisku [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE.  
  
> [!NOTE]
> **Kreator wydajności** umożliwia dodawanie danych profilowania, danych dotyczących wydajności JScript lub obu do zebranych danych profilowych. Opcja TIP zbiera dane z procesów po stronie serwera. Profilowanie w języku JScript zbiera dane ze skryptów, które są uruchomione w lokalnej lub zdalnej witrynie sieci Web. W większości przypadków należy wybrać tylko jedną z opcji.  
  
 W zależności od ustawień uprawnień dostępu użytkowników dostępnych dla administratora użytkownik indywidualny może lub nie ma uprawnień zabezpieczeń do tworzenia sesji profilera na komputerze hostującym proces ASP.NET. Poniższe przykłady ilustrują ewentualne różnice między użytkownikami:  
  
- Niektórzy użytkownicy mogą uzyskiwać dostęp do zaawansowanych funkcji profilowania, gdy administrator ustawił sterownik i usługę do uruchomienia.  
  
- Użytkownicy domeny mogą uzyskać dostęp tylko do profilowania przykładowych.  
  
- Niektórzy użytkownicy mają zablokowany dostęp do profilowania wszystkim innym użytkownikom.  
  
  Aby uzyskać więcej informacji, zobacz [profilowanie i zabezpieczenia systemu Windows Vista](../profiling/profiling-and-windows-vista-security.md) oraz opcje administratora w programie [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-profile-a-web-site-project"></a>Aby profilować projekt witryny sieci Web  
  
1. Otwórz [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Projekt sieci Web w [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] lub [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] .  
  
2. W menu **Analizuj** kliknij polecenie **Uruchom Kreatora wydajności**.  
  
3. Na pierwszej stronie kreatora wybierz metodę profilowania, a następnie kliknij przycisk **dalej**. Aby uzyskać więcej informacji na temat metod profilowania, zobacz [Opis metod zbierania danych o wydajności](../profiling/understanding-performance-collection-methods.md). Należy zauważyć, że metoda profilowania wizualizatora współbieżności nie jest dostępna dla aplikacji sieci Web.  
  
4. W **której aplikacji chcesz określić profilowanie?** listę rozwijaną, upewnij się, że bieżący projekt jest wybrany, a następnie kliknij przycisk **dalej**.  
  
5. Na trzeciej stronie kreatora możesz dodać dane dotyczące profilowania interakcji między warstwami (TIP), dane z kodu JavaScript uruchomionego na stronach sieci Web lub oba te elementy.  
  
    - Aby zbierać interakcje warstwy, zaznacz pole wyboru **Włącz profilowanie interakcji między warstwami** .  
  
    - Aby zbierać dane z kodu JavaScript działającego na stronach sieci Web, zaznacz pole wyboru **profil JavaScript** .  
  
6. Kliknij przycisk **Dalej**.  
  
7. Na czwartej stronie kreatora kliknij przycisk **Zakończ**.  
  
8. Tworzona jest sesja wydajności dla [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji, a witryna sieci Web jest uruchamiana w przeglądarce. Należy skorzystać z funkcji, które chcesz profilować, a następnie zamknąć przeglądarkę.  
  
     Profiler generuje plik danych i wyświetla widok podsumowania danych w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oknie głównym.  
  
### <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Aby profilować witrynę sieci Web bez otwierania projektu w programie Visual Studio  
  
1. Otwórz [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] lub [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] .  
  
2. W menu **Analizuj** kliknij polecenie **Uruchom Kreatora wydajności**.  
  
3. Na pierwszej stronie kreatora wybierz metodę profilowania, a następnie kliknij przycisk **dalej**. Aby uzyskać więcej informacji, zobacz [Omówienie metod zbierania danych o wydajności](../profiling/understanding-performance-collection-methods.md).  
  
4. Na drugiej stronie kreatora wybierz opcję **profilu aplikacji ASP.NET lub JavaScript** , a następnie kliknij przycisk **dalej**.  
  
5. W polu **adres URL lub ścieżka spowoduje uruchomienie aplikacji sieci Web** na trzeciej stronie kreatora wprowadź adres URL strony głównej aplikacji, a następnie kliknij przycisk **dalej**.  
  
   - W przypadku witryny sieci Web opartej na serwerze (IIS) wpisz adres URL, taki jak **http://localhost/MySite/default.aspx** . Powoduje to [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] , że aplikacja na komputerze lokalnym w katalogu głównym aplikacji witryny Moja witryna zostanie profilowana, a strona default. aspx w tej witrynie zostanie uruchomiona w programie Internet Explorer w celu uruchomienia sesji.  
  
   - W przypadku witryny sieci Web opartej na plikach wpisz ścieżkę, taką jak File///**c:\WebSites\MySite\default.aspx**. Powoduje to, że [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacja znajdująca się w c:\webSites\MySite ma być profilowana, a strona, http://localhost:nnnn/MySite/default.aspx która ma zostać uruchomiona w programie Internet Explorer, aby uruchomić sesję.  
  
   - W przypadku witryn zewnętrznych, na których mają być zbierane dane JavaScript, wpisz adres URL, na przykład http: \/ /www.contoso.com.  
  
     Aby uzyskać więcej informacji, Wyświetl strony właściwości dla [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] docelowego pliku binarnego.  
  
6. Na trzeciej stronie kreatora możesz dodać dane dotyczące profilowania interakcji między warstwami (TIP), dane z kodu JavaScript uruchomionego na stronach sieci Web lub oba te elementy.  
  
   - Aby zbierać interakcje warstwy, zaznacz pole wyboru **Włącz profilowanie interakcji między warstwami** .  
  
   - Aby zbierać dane z kodu JavaScript działającego na stronach sieci Web, zaznacz pole wyboru **profil JavaScript** .  
  
7. Kliknij przycisk **Dalej**.  
  
8. Na czwartej stronie kreatora kliknij przycisk **Zakończ**.  
  
9. Tworzona jest sesja wydajności dla aplikacji ASP.NET, a witryna sieci Web jest uruchamiana w przeglądarce. Należy skorzystać z funkcji, które chcesz profilować, a następnie zamknąć przeglądarkę.  
  
     Profiler generuje plik danych i wyświetla widok podsumowania danych w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oknie głównym.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie](../profiling/overviews-performance-tools.md)   
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Informacje o danych Instrumentacji](../profiling/understanding-instrumentation-data-values.md)   
 [Omówienie wartości danych próbkowania](../profiling/understanding-sampling-data-values.md)
