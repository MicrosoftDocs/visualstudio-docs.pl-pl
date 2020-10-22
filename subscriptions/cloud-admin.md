---
title: Konfigurowanie administratorów dla subskrypcji miesięcznych | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 8b30e2bc-2ac3-4fcc-b296-128731471032
ms.date: 03/03/2020
ms.topic: how-to
description: Konfigurowanie administratorów dla miesięcznych subskrypcji
ms.openlocfilehash: fbb8d1f7a1519950e84c6f6fe726dd8f52ff29c5
ms.sourcegitcommit: d3bca34f82de03fa34ecdd72233676c17fb3cb14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2020
ms.locfileid: "91006114"
---
# <a name="set-up-administrators-for-visual-studio-monthly-subscriptions"></a>Konfigurowanie administratorów dla miesięcznych subskrypcji programu Visual Studio

Subskrypcje miesięczne programu Visual Studio są zarządzane przez administratorów. Osoby te mogą przypisywać subskrypcje, edytować przypisania, dodawać i usuwać subskrypcje oraz wykonywać inne zadania związane z zarządzaniem subskrypcjami.

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>Właścicielem subskrypcji platformy Azure jest pierwszy administrator

Gdy kupujesz subskrypcje miesięczne programu Visual Studio, jako właściciel subskrypcji platformy Azure używanej do zakupów, zostanie on automatycznie skonfigurowany jako administrator dla tych subskrypcji.

Miesięczne subskrypcje można zakupić za pomocą [Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions)lub skontaktować się z dostawcą rozwiązań w chmurze. Jeśli kupujesz za pomocą Visual Studio Marketplace, pod koniec korzystania z zakupu będziesz mieć możliwość zarządzania użytkownikami. Wybranie tej opcji spowoduje przejście do portalu administracyjnego subskrypcji programu Visual Studio — [https://manage.visualstudio.com](https://manage.visualstudio.com) .

Po zakupieniu subskrypcji możesz w dowolnym momencie odwiedzić [Portal administracyjny](https://manage.visualstudio.com) . Po prostu zaloguj się do portalu i wybierz odpowiednią subskrypcję platformy Azure w lewym górnym rogu.

Jako właściciel subskrypcji platformy Azure używany do zakupu miesięcznych subskrypcji możesz także przypisać dodatkowych administratorów.

## <a name="add-administrators"></a>Dodaj administratorów

Aby dodać administratorów:

1. Połącz się z witryną Azure Portal pod adresem [Portal.Azure.com](https://portal.azure.com).
2. Zaloguj się przy użyciu konta użytego do zakupu miesięcznych subskrypcji programu Visual Studio.
3. W obszarze **usługi platformy Azure**wybierz pozycję **Cost Management + rozliczenia**.
   > [!div class="mx-imgBorder"]
   > ![Wybieranie Cost Management i rozliczeń w ramach usług platformy Azure](_img/cloud-admin/azure-cost-billing.png "Wybierz Cost Management z grupy usług platformy Azure")
4. Z listy **Moje subskrypcje** wybierz subskrypcję platformy Azure, która została użyta do dokonania zakupu.
   > [!div class="mx-imgBorder"]
   > ![Wybierz subskrypcję](_img/cloud-admin/subscription-list.png "Wybierz subskrypcję platformy Azure, której chcesz użyć do dokonania zakupu.")
5. Kliknij pozycję **Kontrola dostępu (IAM)**, która znajduje się w górnej części listy w okienku nawigacji po lewej stronie.
6. Kliknij kartę **Dodaj** w górnej części strony.
7. Kliknij pozycję **Dodaj przypisanie roli**.
   > [!div class="mx-imgBorder"]
   > ![Wybieranie kontroli dostępu, Dodawanie, Dodawanie przypisania roli](_img/cloud-admin/access-control-add.png "Z listy po lewej stronie wybierz pozycję Kontrola dostępu, a następnie wybierz pozycję Dodaj.")
8. W okienku po prawej stronie kliknij listę rozwijaną **rola** w górnej części okienka, przewiń w dół i wybierz pozycję **administrator dostępu użytkowników**.
9. Na liście użytkowników przewiń w dół do użytkownika, który ma być administratorem, i wybierz go. 
   > [!div class="mx-imgBorder"]
   > ![Wybieranie roli, administrator dostępu użytkowników](_img/cloud-admin/add-role-user-access-admin.png "Wybierz pozycję rola, wybierz pozycję Administrator dostępu użytkowników, a następnie wybierz nazwę użytkownika, który ma być administratorem.")
10. Kliknij pozycję **Zapisz**.
11. Kliknij kartę **przypisania ról** , aby sprawdzić, czy wybrany użytkownik jest teraz widoczny jako administrator dostępu użytkownika.

Nowy administrator może teraz zalogować się do [portalu administracyjnego](https://manage.visualstudio.com), wybrać tę samą subskrypcję platformy Azure, która została użyta do zakupu miesięcznych subskrypcji z listy w lewym górnym rogu strony i rozpocząć zarządzanie tymi subskrypcjami.

> [!NOTE]
> Jeśli widzisz użytkowników z dostępem, aby edytować subskrypcje miesięczne, które nie zostały ustanowione jako administratorzy, mogą oni mieć role w podstawowej subskrypcji platformy Azure, które umożliwiają im zarządzanie subskrypcjami. Role te obejmują: właściciel, współautor, administrator usługi lub współadministrator. Aby uzyskać więcej informacji, odwiedź stronę [Dodawanie menedżerów rozliczeń](/azure/devops/organizations/billing/add-backup-billing-managers?view=vsts).

Informacje o subskrypcjach miesięcznych programu Visual Studio można znaleźć w sekcji [Omówienie](vscloud-overview.md) kupowania subskrypcji. Aby kupić miesięczne subskrypcje programu Visual Studio, odwiedź Visual Studio Marketplace pod adresem [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription) .

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](/visualstudio/)
- [Dokumentacja usługi Azure DevOps](/azure/devops/)
- [Dokumentacja platformy Azure](/azure/)
- [Dokumentacja Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
Dowiedz się więcej o zarządzaniu subskrypcjami programu Visual Studio.
- [Przypisywanie pojedynczych subskrypcji](assign-license.md)
- [Przypisywanie wielu subskrypcji](assign-license-bulk.md)
- [Edytowanie subskrypcji](edit-license.md)
- [Określanie maksymalnego użycia](maximum-usage.md)