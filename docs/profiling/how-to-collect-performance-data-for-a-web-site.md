---
title: 'Jak: Zbieranie danych o wydajności witryny sieci Web | Dokumenty firmy Microsoft'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302904"
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Jak: Zbieranie danych o wydajności witryny sieci Web

Za pomocą **Kreatora wydajności** można zbierać dane o wydajności dla aplikacji [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sieci web. Można profilować aplikację sieci web, która jest otwarta [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] w programie Visual Studio lub można profilować witrynę sieci Web, która znajduje się na komputerze lokalnym i nie jest otwarta w programie Visual Studio IDE.

> [!NOTE]
> **Kreator wydajności** umożliwia dodawanie danych interakcji warstwy (TIP), danych wydajności JScript lub obu tych danych do zebranych danych profilowania. Opcja TIP zbiera dane z procesów po stronie serwera. Profilowanie JScript zbiera dane ze skryptów uruchomionych w lokalnej lub zdalnej witrynie sieci Web. W większości przypadków należy wybrać tylko jedną z opcji.

 W zależności od ustawień uprawnień dostępu użytkownika, które administrator udostępnił, indywidualny użytkownik może lub nie może mieć uprawnień zabezpieczeń do tworzenia sesji profilera na komputerze, na którym znajduje się proces ASP.NET. Poniższe przykłady ilustrują możliwe różnice między użytkownikami:

- Niektórzy użytkownicy mogą uzyskać dostęp do zaawansowanych funkcji profilowania, gdy administrator ustawił sterownik i usługę do uruchomienia.

- Użytkownicy domeny mogą uzyskiwać dostęp tylko do przykładowego profilowania.

- Niektórzy użytkownicy mogą odmówić dostępu do profilowania wszystkim innym użytkownikom.

  Aby uzyskać więcej informacji, zobacz [Profilowanie i zabezpieczenia systemu Windows Vista](../profiling/profiling-and-windows-vista-security.md) oraz opcje ADMIN w programie [VSPerfCmd](../profiling/vsperfcmd.md).

## <a name="to-profile-a-web-site-project"></a>Aby profilować projekt witryny sieci Web

1. Otwórz [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] projekt sieci Web w programie Visual Studio.

2. W menu **Analizuj** wybierz polecenie **Profiler wydajności**, wybierz pozycję **Eksplorator wydajności**, a następnie wybierz polecenie **Start**.

3. Na pierwszej stronie kreatora wybierz metodę profilowania, a następnie kliknij przycisk **Dalej**. Aby uzyskać więcej informacji na temat metod profilowania, zobacz [Opis metod zbierania wydajności.](../profiling/understanding-performance-collection-methods.md) Należy zauważyć, że metoda profilowania wizualizatora współbieżności nie jest dostępna dla aplikacji sieci web.

4. Na liście rozwijanej **Która aplikacja ma być kierowana do profilowania?** **Next**

5. Na trzeciej stronie kreatora można dodać dane profilowania interakcji warstwy (TIP), dane z języka JavaScript uruchomionego na stronach internetowych lub oba te dane.

    - Aby zebrać interakcję warstwy, zaznacz pole wyboru **Włącz profilowanie interakcji warstwy.**

    - Aby zbierać dane z języka JavaScript działającego na stronach sieci Web, zaznacz pole wyboru **Profil JavaScript.**

6. Kliknij przycisk **alej**.

7. Na czwartej stronie kreatora kliknij przycisk **Zakończ**.

8. Dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji tworzona jest sesja wydajności, a witryna sieci Web jest uruchamiana w przeglądarce. Korzystaj z funkcji, które chcesz profilować, a następnie zamknij przeglądarkę.

     Profiler generuje plik danych i wyświetla widok podsumowania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] danych w oknie głównym.

## <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Aby profilować witrynę sieci Web bez otwierania projektu w programie Visual Studio

1. Otwórz program Visual Studio.

2. W menu **Analizuj** wybierz polecenie **Profiler wydajności**, wybierz pozycję **Eksplorator wydajności**, a następnie wybierz polecenie **Start**.

3. Na pierwszej stronie kreatora wybierz metodę profilowania, a następnie kliknij przycisk **Dalej**. Aby uzyskać więcej informacji, zobacz [Opis metod zbierania wydajności](../profiling/understanding-performance-collection-methods.md).

4. Na drugiej stronie kreatora wybierz opcję **Profil ASP.NET lub JavaScript,** a następnie kliknij przycisk **Dalej**.

5. W polu **Jaki adres URL lub Ścieżka uruchomi aplikację internetową** na trzeciej stronie kreatora wprowadź adres URL strony głównej aplikacji, a następnie kliknij przycisk **Dalej**.

   - W przypadku witryny sieci Web opartej na serwerach (IIS) wpisz adres URL, taki jak ** < `http://localhost/MySite/default.aspx` **. Powoduje to, że [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacja na komputerze lokalnym w katalogu głównym aplikacji MySite mają być profilowane i strony default.aspx w tej witrynie, które mają być uruchomione w programie Internet Explorer, aby rozpocząć sesję.

   - W przypadku witryny sieci Web opartej na plikach wpisz ścieżkę, taką jak plik///**c:\WebSites\MySite\default.aspx**. Powoduje to, że aplikacja znajdująca [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] się w c:\webSites\MySite ma być profilowana, a strona `http://localhost:nnnn/MySite/default.aspx` ma zostać uruchomiona w programie Internet Explorer, aby rozpocząć sesję.

   - W przypadku witryn zewnętrznych, na których chcesz zbierać dane `http://www.contoso.com`JavaScript, wpisz adres URL, na przykład .

     Aby uzyskać więcej informacji, wyświetl [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] strony właściwości dla docelowego pliku binarnego.

6. Na trzeciej stronie kreatora można dodać dane profilowania interakcji warstwy (TIP), dane z języka JavaScript uruchomionego na stronach internetowych lub oba te dane.

    - Aby zebrać interakcję warstwy, zaznacz pole wyboru **Włącz profilowanie interakcji warstwy.**

    - Aby zbierać dane z języka JavaScript działającego na stronach internetowych, zaznacz pole wyboru **Profil JavaScript.**

7. Kliknij przycisk **alej**.

8. Na czwartej stronie kreatora kliknij przycisk **Zakończ**.

9. Sesja wydajności jest tworzona dla aplikacji ASP.NET, a witryna sieci web jest uruchamiana w przeglądarce. Korzystaj z funkcji, które chcesz profilować, a następnie zamknij przeglądarkę.

     Profiler generuje plik danych i wyświetla widok podsumowania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] danych w oknie głównym.

## <a name="see-also"></a>Zobacz też

[Przeglądy](../profiling/overviews-performance-tools.md)
[Konfigurowanie sesji](../profiling/configuring-performance-sessions.md)
wydajności[Zrozumienie wartości](../profiling/understanding-instrumentation-data-values.md)
danych instrumentacji Zrozumienie wartości danych[próbkowania](../profiling/understanding-sampling-data-values.md)
