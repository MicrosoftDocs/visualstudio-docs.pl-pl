---
title: Konfigurowanie administratorów dla subskrypcji miesięcznych | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/03/2020
ms.topic: conceptual
description: Konfigurowanie administratorów dla miesięcznych subskrypcji
ms.openlocfilehash: a5d7c6e9442efd70ea3e7c2b7e7da4239e226aa2
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78289844"
---
# <a name="set-up-administrators-for-visual-studio-monthly-subscriptions"></a>Konfigurowanie administratorów dla miesięcznych subskrypcji programu Visual Studio

Subskrypcje miesięczne programu Visual Studio są zarządzane przez administratorów. Osoby te mogą przypisywać subskrypcje, edytować przypisania, dodawać i usuwać subskrypcje oraz wykonywać inne zadania związane z zarządzaniem subskrypcjami.

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>Właścicielem subskrypcji platformy Azure jest pierwszy administrator

Gdy kupujesz subskrypcje miesięczne programu Visual Studio, jako właściciel subskrypcji platformy Azure używanej do zakupów, zostanie on automatycznie skonfigurowany jako administrator dla tych subskrypcji.

Miesięczne subskrypcje można zakupić za pomocą [Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions)lub skontaktować się z dostawcą rozwiązań w chmurze. Jeśli kupujesz za pomocą Visual Studio Marketplace, pod koniec korzystania z zakupu będziesz mieć możliwość zarządzania użytkownikami. Wybranie tej opcji spowoduje przejście do portalu administracyjnego subskrypcji programu Visual Studio — [https://manage.visualstudio.com](https://manage.visualstudio.com).

Po zakupieniu subskrypcji możesz w dowolnym momencie odwiedzić [Portal administracyjny](https://manage.visualstudio.com) . Po prostu zaloguj się do portalu i wybierz odpowiednią subskrypcję platformy Azure w lewym górnym rogu.

Jako właściciel subskrypcji platformy Azure używany do zakupu miesięcznych subskrypcji możesz także przypisać dodatkowych administratorów.

## <a name="add-administrators"></a>Dodaj administratorów

Aby dodać administratorów:

1. Połącz się z witryną Azure Portal pod adresem [Portal.Azure.com](https://portal.azure.com).
2. Zaloguj się przy użyciu konta użytego do zakupu miesięcznych subskrypcji programu Visual Studio.
3. W obszarze **usługi platformy Azure**wybierz pozycję **Cost Management + rozliczenia**.
   > [!div class="mx-imgBorder"]
   > ![wybrać Cost Management i rozliczeń w ramach usług platformy Azure](_img/cloud-admin/azure-cost-billing.png)
4. Z listy **Moje subskrypcje** wybierz subskrypcję platformy Azure, która została użyta do dokonania zakupu.
   > [!div class="mx-imgBorder"]
   > ![wybierz subskrypcję](_img/cloud-admin/subscription-list.png)
5. Kliknij pozycję **Kontrola dostępu (IAM)** , która znajduje się w górnej części listy w okienku nawigacji po lewej stronie.
6. Kliknij kartę **Dodaj** w górnej części strony.
7. Kliknij pozycję **Dodaj przypisanie roli**.
   > [!div class="mx-imgBorder"]
   > ![wybierz pozycję Kontrola dostępu, Dodaj, Dodaj przypisanie roli](_img/cloud-admin/access-control-add.png)
8. W okienku po prawej stronie kliknij listę rozwijaną **rola** w górnej części okienka, przewiń w dół i wybierz pozycję **administrator dostępu użytkowników**.
9. Na liście użytkowników przewiń w dół do użytkownika, który ma być administratorem, i wybierz go. 
   > [!div class="mx-imgBorder"]
   > ![wybierz rolę, administrator dostępu użytkowników](_img/cloud-admin/add-role-user-access-admin.png)
10. Kliknij przycisk **Save** (Zapisz).
11. Kliknij kartę **przypisania ról** , aby sprawdzić, czy wybrany użytkownik jest teraz widoczny jako administrator dostępu użytkownika.

Nowy administrator może teraz zalogować się do [portalu administracyjnego](https://manage.visualstudio.com), wybrać tę samą subskrypcję platformy Azure, która została użyta do zakupu miesięcznych subskrypcji z listy w lewym górnym rogu strony i rozpocząć zarządzanie tymi subskrypcjami.

> [!NOTE]
> Jeśli widzisz użytkowników z dostępem, aby edytować subskrypcje miesięczne, które nie zostały ustanowione jako administratorzy, mogą oni mieć role w podstawowej subskrypcji platformy Azure, które umożliwiają im zarządzanie subskrypcjami. Role te obejmują: właściciel, współautor, administrator usługi lub współadministrator. Aby uzyskać więcej informacji, odwiedź stronę [Dodawanie menedżerów rozliczeń](/azure/devops/organizations/billing/add-backup-billing-managers?view=vsts).

Informacje o subskrypcjach miesięcznych programu Visual Studio można znaleźć w sekcji [Omówienie](vscloud-overview.md) kupowania subskrypcji. Aby kupić miesięczne subskrypcje programu Visual Studio, odwiedź Visual Studio Marketplace w [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription).

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
Dowiedz się więcej o zarządzaniu subskrypcjami programu Visual Studio.
- [Przypisywanie pojedynczych subskrypcji](assign-license.md)
- [Przypisywanie wielu subskrypcji](assign-license-bulk.md)
- [Edytowanie subskrypcji](edit-license.md)
- [Określanie maksymalnego użycia](maximum-usage.md)



