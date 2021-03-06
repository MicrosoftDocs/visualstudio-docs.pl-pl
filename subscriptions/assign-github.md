---
title: Przypisywanie subskrypcji programu Visual Studio za pomocą usługi GitHub Enterprise | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: f271d623-dcde-442a-865c-4dca5ad8a9c5
ms.date: 03/03/2021
ms.topic: conceptual
description: Zarządzanie subskrypcjami w subskrypcjach programu Visual Studio za pomocą usługi GitHub Enterprise
ms.openlocfilehash: 5837ec33e6f17f0970178a0f1b306960e9c42668
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249694"
---
# <a name="manage-visual-studio-subscriptions-with-github-enterprise"></a>Zarządzanie subskrypcjami programu Visual Studio za pomocą usługi GitHub Enterprise
Klienci, którzy mają umowę Enterprise Agreement (EA) z firmą Microsoft, mogą zakupić nową ofertę subskrypcji, która wiąże się z subskrypcjami programu Visual Studio w wersji Standard i usługi GitHub. Jest to prosty i ekonomiczny sposób, w jaki Subskrybenci programu Visual Studio mogą uzyskać przedsiębiorstwo w serwisie GitHub. 

Gdy organizacja kupuje subskrypcje programu Visual Studio za pomocą usługi GitHub Enterprise, są one obsługiwane i zarządzane w dwóch częściach.

## <a name="manage-visual-studio-subscriptions"></a>Zarządzanie subskrypcjami programu Visual Studio
Gdy organizacja kupuje subskrypcje programu Visual Studio za pomocą usługi GitHub Enterprise, część subskrypcji programu Visual Studio jest inicjowana natychmiast, a subskrypcje są dostępne do przypisywania i zarządzania w portalu [administracyjnym subskrypcji](https://manage.visualstudio.com) programu Visual Studio. Po przypisaniu subskrypcji programu Visual Studio za pomocą usługi GitHub Enterprise subskrybent otrzyma wiadomość e-mail z informacją o tym, że użytkownicy będą mogli uzyskać dostęp do swojej subskrypcji programu Visual Studio pod adresem <https://my.visualstudio.com/subscriptions> .

Aby uzyskać więcej informacji na temat zarządzania subskrypcjami programu Visual Studio, zapoznaj się z następującymi tematami:
- [Korzystanie z portalu administracyjnego](using-admin-portal.md)
- [Przypisywanie subskrypcji](assign-license.md)
- [Edytuj subskrypcje](edit-license.md)
- [Usuwanie subskrypcji](delete-license.md)
- [Nadmierne alokacje](handle-overclaimed-license.md)

> [!Important]
> Jeśli subskrypcje programu Visual Studio z usługą GitHub Enterprise są przypisane przez administratorów subskrypcji programu Visual Studio bez konieczności uprzedniego zakupu, usługi GitHub nie będą powiadamiane o konieczności utworzenia konta w witrynie GitHub Enterprise.  **Zakup co najmniej jednego** Subskrypcję programu Visual Studio z usługą GitHub Enterprise należy wykonać przed przypisaniem subskrypcji.

## <a name="moving-to-visual-studio-with-github-enterprise"></a>Przechodzenie do programu Visual Studio za pomocą usługi GitHub Enterprise
Jeśli Twoja organizacja kupuje subskrypcje programu Visual Studio z pakietami dla przedsiębiorstw w witrynie GitHub po przypisaniu standardowych Visual Studio Enterprise i Visual Studio Professional subskrypcje, Portal administracyjny zawiera funkcję ułatwiającą przeniesienie istniejących subskrybentów do odpowiedniej Visual Studio Enterprise z subskrypcją GitHub Enterprise i/lub Visual Studio Professional z subskrypcjami w witrynie GitHub Enterprise.  Na przykład Subskrybenci z subskrypcjami Visual Studio Professional zostaną przeniesieni do Visual Studio Professional za pomocą subskrypcji usługi GitHub Enterprise. Na pasku po lewej stronie panelu "przegląd" zobaczysz następujący kafelek:

   > [!div class="mx-imgBorder"]
   > ![Przycisk Przenieś teraz](_img/assign-github/move-now.png "Kliknij przycisk "Przenieś teraz", aby uaktualnić subskrypcje do programu Visual Studio z subskrypcjami w witrynie GitHub Enterprise")

> [!IMPORTANT]
> Jak wspomniano powyżej, istniejące dane subskrybenta, historia i Identyfikator subskrypcji zostaną zachowane, a wszelkie aktywowane korzyści nie będą przerywane z powodu tego przeniesienia.  
>
> Ta funkcja jest wdrażana w fazach i może nie być natychmiast dostępna dla Twoich umów.

Po kliknięciu przycisku Przenieś teraz zostanie wyprowadzony panel **przechodzenia** z zaleceniami dotyczącymi przenoszenia subskrypcji przedsiębiorstwa i/lub profesjonalnego:

   > [!div class="mx-imgBorder"]
   > ![Panel wylotu](_img/assign-github/fly-out.png)

Na tym kafelku można przejrzeć ewentualnych subskrybentów i określić, czy chcesz powiadomić ich o otrzymaniu powiadomienia e-mail po zakończeniu przenoszenia.  Ta wiadomość e-mail informuje subskrybentów, że ich korzyści pozostają niezmienione i zachęca je do rozpoczęcia konfigurowania obecności w serwisie GitHub.  

Po kliknięciu przycisku **Przenieś wszystkich subskrybentów** Potwierdź wybrane opcje i poczekaj kilka sekund, aż subskrypcja zostanie zakończona.  Jeśli ma to zastosowanie, należy wykonać te kroki dla wersji Professional i Enterprise osobno.  


## <a name="what-is-the-visual-studio-with-github-enterprise-setup-process"></a>Jaki jest proces konfiguracji programu Visual Studio z usługą GitHub Enterprise?
Usługa GitHub Enterprise jest konfigurowana i zarządzana niezależnie od subskrypcji programu Visual Studio. Po rozpoczęciu subskrypcji programu Visual Studio z zakupem w serwisie GitHub Enterprise proces instalacji konta przedsiębiorstwa w witrynie GitHub jest inicjowany równolegle z (ale oddzielony od), który ustanawia umowę w [manage.VisualStudio.com](https://manage.visualstudio.com). Ustanowienie tego konta usługi GitHub Enterprise może trochę potrwać. 

Gdy firma skonfiguruje konto usługi GitHub Enterprise, subskrybenci, którym przypisano subskrypcje programu Visual Studio z usługą GitHub Enterprise, otrzymają wiadomość e-mail od usługi GitHub z powiadomieniem o połączeniu ich subskrypcji programu Visual Studio. Po otrzymaniu tej wiadomości e-mail Subskrybenci mogą skontaktować się z administratorem organizacji usługi GitHub w celu otrzymania zaproszenia do odpowiedniej organizacji.

Aby uzyskać szczegółowe informacje na temat konfiguracji Enterprise w witrynie GitHub, zapoznaj się z [dokumentacją subskrybenta](access-github.md).   

## <a name="manage-github-enterprise-subscriptions"></a>Zarządzanie subskrypcjami w witrynie GitHub Enterprise
W przypadku zakupu subskrypcji usługi GitHub przedsiębiorstwa partnerzy usługi GitHub z klientami mogą pomóc w tworzeniu i konfigurowaniu organizacji, które będą uzyskiwać dostęp do usługi GitHub i identyfikowania administratorów.  Ci Administratorzy otrzymają powiadomienie, że zostały skonfigurowane jako administratorzy.  

Ponieważ ten proces jest bardziej skomplikowany, może upłynąć kilka dni od zakupu subskrypcji dla organizacji i administratorów w pełni skonfigurowany.

Usługa GitHub jest dostępna zarówno jako GitHub.com w chmurze, jak i na lokalnym serwerze usługi GitHub dla przedsiębiorstw.  Procesy zarządzania dwiema wersjami różnią się.  W usłudze GitHub dostępne są różne tematy pomocy i przewodniki administratora ułatwiające zarządzanie subskrypcjami w przedsiębiorstwie usługi GitHub.  Podano linki do wybranych tematów poniżej.  

## <a name="support-resources"></a>Zasoby pomocy technicznej

- Dowiedz się więcej o przypisaniu usługi GitHub w witrynie [GitHub](https://docs.github.com/en/github/setting-up-and-managing-your-enterprise-account/managing-licenses-for-the-github-enterprise-and-visual-studio-bundle)
- Znajdź odpowiedzi na pytania dotyczące szerokiej gamy tematów w witrynie GitHub w [pomocy usługi GitHub](https://help.github.com/en).
- Uzyskaj pomoc od innych użytkowników usługi GitHub na [forum społeczności usługi GitHub](https://github.community/).
- Aby uzyskać pomoc dotyczącą sprzedaży, subskrypcji, kont i rozliczeń dla subskrypcji programu Visual Studio, skontaktuj się z [pomocą techniczną subskrypcji](https://visualstudio.microsoft.com/subscriptions/support/).
- Masz pytanie dotyczące środowiska IDE programu Visual Studio, Azure DevOps Services lub innych produktów lub usług Visual Studio?  Odwiedź stronę [pomocy technicznej programu Visual Studio](https://visualstudio.microsoft.com/support/).
- Uzyskaj [Pomoc techniczną](https://support.microsoft.com/supportforbusiness/productselection?sapId=b77fe80f-5417-80bd-4b2a-275cf0018c24) dla przedsiębiorstw w witrynie GitHub.   

## <a name="see-also"></a>Zobacz też

- [Dokumentacja programu Visual Studio](/visualstudio/)
- [Azure DevOps documentation (Dokumentacja usługi Azure DevOps)](/azure/devops/)
- [Dokumentacja platformy Azure](/azure/)
- [Dokumentacja Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej o zarządzaniu subskrypcjami programu Visual Studio.
- [Przypisywanie pojedynczych subskrypcji](assign-license.md)
- [Przypisywanie wielu subskrypcji](assign-license-bulk.md)
- [Edytowanie subskrypcji](edit-license.md)
- [Usuwanie subskrypcji](delete-license.md)
- [Określanie maksymalnego użycia](maximum-usage.md)

Aby uzyskać więcej informacji na temat zarządzania subskrypcjami programu Visual Studio za pomocą usługi GitHub Enterprise, zapoznaj się z [portalem administracyjnym subskrypcji](https://visualstudio.microsoft.com/subscriptions-administration/)programu Visual Studio.