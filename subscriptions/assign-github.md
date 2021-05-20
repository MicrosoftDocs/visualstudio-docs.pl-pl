---
title: Przypisywanie Visual Studio subskrypcji za pomocą GitHub Enterprise | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: f271d623-dcde-442a-865c-4dca5ad8a9c5
ms.date: 03/03/2021
ms.topic: conceptual
description: Zarządzanie subskrypcjami w Visual Studio subskrypcji za pomocą GitHub Enterprise
ms.openlocfilehash: a1ece92990bf54d85140b1d3548ebf811913fae4
ms.sourcegitcommit: 0088835f22334b8fee89f8c07bb12bcdfdef1639
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2021
ms.locfileid: "110188113"
---
# <a name="manage-visual-studio-subscriptions-with-github-enterprise"></a>Zarządzanie Visual Studio subskrypcjami za pomocą GitHub Enterprise
Klienci, którzy mają umowy Enterprise (EA) z firmą Microsoft, są uprawnieni do zakupu nowej oferty subskrypcji, która łączy Visual Studio standardowe subskrypcje i GitHub Enterprise. Jest to prosty i ekonomiczny sposób, w jaki subskrybenci Visual Studio mogą uzyskać GitHub Enterprise. 

Gdy organizacja kupuje subskrypcje Visual Studio usługą GitHub Enterprise, są one aprowowane i zarządzane w dwóch częściach.

## <a name="manage-visual-studio-subscriptions"></a>Zarządzanie Visual Studio subskrypcji
Gdy Organizacja kupuje subskrypcje Visual Studio za pomocą usługi GitHub Enterprise, część subskrypcji usługi Visual Studio jest natychmiast aprowizowana, a subskrypcje są dostępne [](https://manage.visualstudio.com) do przypisania i zarządzania w portalu witrynie administracyjnej subskrypcji usługi Visual Studio. Po przypisaniu subskrypcji Visual Studio za pomocą usługi GitHub Enterprise subskrybent otrzyma wiadomość e-mail z powiadomieniem o tym, że może uzyskać dostęp Visual Studio subskrypcji pod adresem <https://my.visualstudio.com/subscriptions> .

Aby uzyskać więcej informacji na temat Visual Studio subskrypcji, zapoznaj się z tymi tematami:
- [Korzystanie z portalu administracyjnego](using-admin-portal.md)
- [Przypisywanie subskrypcji](assign-license.md)
- [Edytowanie subskrypcji](edit-license.md)
- [Usuwanie subskrypcji](delete-license.md)
- [Nadmierne alokacje](handle-overclaimed-license.md)

> [!Important]
> Jeśli Visual Studio z usługą GitHub Enterprise są przypisywane przez administratorów subskrypcji usługi Visual Studio bez wcześniejszego zakupu, usługa GitHub nie zostanie powiadomiona, że chcesz utworzyć GitHub Enterprise konto.  **Zakup co najmniej jednego** Visual Studio subskrypcję z GitHub Enterprise należy przed przypisaniem subskrypcji.

## <a name="moving-to-visual-studio-with-github-enterprise"></a>Przechodzenie do Visual Studio za pomocą GitHub Enterprise
</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWEAsv]

Jeśli Twoja organizacja zakupi subskrypcje usługi Visual Studio za pomocą pakietów GitHub Enterprise po przypisaniu standardowych subskrypcji usług Visual Studio Enterprise i Visual Studio Professional, portal administracyjny zawiera funkcję, która pomaga przenieść istniejących subskrybentów do odpowiednich Visual Studio Enterprise przy użyciu usług GitHub Enterprise i/lub Visual Studio Professional z subskrypcjami GitHub Enterprise.  Na przykład subskrybenci z subskrypcjami Visual Studio Professional zostaną przeniesieni do Visual Studio Professional z GitHub Enterprise subskrypcji. Na lewym pasku panelu "Przegląd" zostanie wyświetlony następujący kafelek:

   > [!div class="mx-imgBorder"]
   > ![Przycisk Przenieś teraz](_img/assign-github/move-now.png "Kliknij pozycję &quot;Przenieś teraz&quot;, aby uaktualnić subskrypcje do Visual Studio z GitHub Enterprise subskrypcji")

> [!IMPORTANT]
> Jak wspomniano powyżej, istniejące dane subskrybenta, historia i identyfikator subskrypcji będą zachowywane, a wszelkie aktywowane przez nich korzyści nie zostaną przerwane z powodu tego przeniesienia.  


Po kliknięciu przycisku **Przenieś teraz** na wysuwanych panelach będą dostępne zalecenia dotyczące przenoszenia subskrypcji Enterprise i/lub Professional:

   > [!div class="mx-imgBorder"]
   > ![Panel wysuwu](_img/assign-github/fly-out.png)

Na tym kafelku możesz przejrzeć subskrybentów, których dotyczy ten błąd, i określić, czy chcesz powiadomić ich o otrzymaniu powiadomienia e-mail po zakończeniu przenoszenia.  Ta wiadomość e-mail informuje subskrybentów, że ich korzyści pozostają niezmienione, i zachęca ich do rozpoczęcia konfigurowania obecności w usłudze GitHub.  

Kliknięcie **przycisku Przenieś subskrybentów** umożliwi przeniesienie wszystkich zalecanych subskrybentów   lub wybranie osób z listy.  Po potwierdzeniu wybranych opcji ukończenie subskrypcji potrwa kilka sekund. Jeśli ma to zastosowanie, należy wykonać te kroki dla wersji Professional i Enterprise oddzielnie.  

## <a name="what-is-the-visual-studio-with-github-enterprise-setup-process"></a>Jaki jest proces konfiguracji programu Visual Studio z usługą GitHub Enterprise?
Usługa GitHub Enterprise jest konfigurowana i zarządzana niezależnie od subskrypcji programu Visual Studio. Po zakończeniu Visual Studio z zakupem GitHub Enterprise proces konfiguracji konta usługi GitHub Enterprise jest inicjowany równolegle (ale oddzielnie od) podczas ustanawiania umowy w manage.visualstudio.com [.](https://manage.visualstudio.com) Ustanowienie tego konta usługi GitHub Enterprise może trochę potrwać. 

Gdy firma skonfiguruje konto usługi GitHub Enterprise, subskrybenci, którym przypisano subskrypcje programu Visual Studio z usługą GitHub Enterprise, otrzymają wiadomość e-mail od usługi GitHub z powiadomieniem o połączeniu ich subskrypcji programu Visual Studio. Gdy subskrybenci otrzymają tę wiadomość e-mail, mogą się snąć do administratora organizacji usługi GitHub w celu otrzymania zaproszenia do odpowiedniej organizacji.

Aby uzyskać szczegółowe informacje GitHub Enterprise konfiguracji, zapoznaj się z dokumentacją [dla subskrybentów.](access-github.md)   

## <a name="manage-github-enterprise-subscriptions"></a>Zarządzanie GitHub Enterprise subskrypcji
Po GitHub Enterprise subskrypcji usługi GitHub współpracuje z klientami, aby ułatwić tworzenie i konfigurowanie organizacji, które będą korzystać z usługi GitHub i identyfikować administratorów.  Administratorzy ci otrzymają powiadomienie, że zostali skonfigurowani jako administratorzy.  

Ponieważ ten proces jest bardziej złożony, pełne skonfigurowanie subskrypcji dla organizacji i administratorów może potrwać kilka dni.

Usługa GitHub jest dostępna jako chmurowa usługa GitHub.com lub lokalna usługa GitHub Enterprise Server.  Procesy zarządzania tymi dwiema wersjami różnią się.  Usługa GitHub udostępnia różne tematy pomocy i przewodniki dla administratorów, które ułatwiają GitHub Enterprise subskrypcji.  Poniżej podano linki do wybranych tematów.  

## <a name="support-resources"></a>Zasoby pomocy technicznej
- Dowiedz się więcej o przypisaniu w usłudze GitHub w [witrynie GitHub Docs](https://docs.github.com/en/github/setting-up-and-managing-your-enterprise-account/managing-licenses-for-the-github-enterprise-and-visual-studio-bundle)
- Odpowiedzi na pytania dotyczące szerokiej gamy tematów dotyczących usługi GitHub można znaleźć na stronie [GitHub Help (Pomoc usługi GitHub).](https://help.github.com/en)
- Uzyskaj pomoc od innych użytkowników usługi GitHub na [forum społeczności usługi GitHub.](https://github.community/)
- Aby uzyskać pomoc w administrowaniu subskrypcjami Visual Studio, skontaktuj się [z Visual Studio pomocą techniczną subskrypcji usługi](https://aka.ms/vsadminhelp).
- Masz pytanie dotyczące Visual Studio IDE, Azure DevOps Services lub innych Visual Studio produktów lub usług?  Odwiedź [Visual Studio pomocy technicznej](https://visualstudio.microsoft.com/support/).
- Uzyskaj [pomoc techniczną GitHub Enterprise.](https://support.microsoft.com/supportforbusiness/productselection?sapId=b77fe80f-5417-80bd-4b2a-275cf0018c24)   

## <a name="see-also"></a>Zobacz też
- [Visual Studio dokumentacji](/visualstudio/)
- [Azure DevOps documentation (Dokumentacja usługi Azure DevOps)](/azure/devops/)
- [Dokumentacja platformy Azure](/azure/)
- [Microsoft 365 dokumentacji](/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
Dowiedz się więcej o zarządzaniu Visual Studio subskrypcji.
- [Przypisywanie poszczególnych subskrypcji](assign-license.md)
- [Przypisywanie wielu subskrypcji](assign-license-bulk.md)
- [Edytowanie subskrypcji](edit-license.md)
- [Usuwanie subskrypcji](delete-license.md)
- [Określanie maksymalnego użycia](maximum-usage.md)

Aby uzyskać więcej informacji na temat zarządzania Visual Studio subskrypcjami za pomocą GitHub Enterprise, zapoznaj się z portalem administracyjnym Visual Studio [subskrypcji.](https://visualstudio.microsoft.com/subscriptions-administration/)