---
title: Konfigurowanie administratorów dla subskrypcji miesięcznych | Dokumenty firmy Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 8b30e2bc-2ac3-4fcc-b296-128731471032
ms.date: 03/03/2020
ms.topic: conceptual
description: Konfigurowanie administratorów dla miesięcznych subskrypcji
ms.openlocfilehash: c9a1303d4111f0ec4a0c1249a25e49fc40cf26de
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232656"
---
# <a name="set-up-administrators-for-visual-studio-monthly-subscriptions"></a>Konfigurowanie administratorów miesięcznych subskrypcji programu Visual Studio

Miesięczne subskrypcje programu Visual Studio są zarządzane przez administratorów. Osoby te mogą przypisywać subskrypcje, edytować przypisania, dodawać lub usuwać subskrypcje oraz wykonywać inne zadania zarządzania subskrypcjami.

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>Właściciel subskrypcji platformy Azure jest pierwszym administratorem

Podczas zakupu miesięcznych subskrypcji programu Visual Studio, jako właściciel subskrypcji platformy Azure używane do dokonywania zakupów, są automatycznie skonfigurowane jako administrator dla tych subskrypcji.

Miesięczne subskrypcje można kupić za pośrednictwem [portalu Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions)lub kontaktując się z dostawcą rozwiązań w chmurze. W przypadku zakupu za pośrednictwem portalu Visual Studio Marketplace, po zakończeniu zakupu, otrzymasz możliwość zarządzania użytkownikami. Wybranie tej opcji spowoduje przesunie Cię [https://manage.visualstudio.com](https://manage.visualstudio.com)do portalu administracyjnego subskrypcji programu Visual Studio — .

Po zakupie subskrypcji możesz odwiedzić [portal administracyjny](https://manage.visualstudio.com) w dowolnym momencie. Wystarczy zalogować się do portalu i wybrać odpowiednią subskrypcję platformy Azure w lewym górnym rogu.

Jako właściciel subskrypcji platformy Azure używanej do zakupu miesięcznych subskrypcji, można również przypisać dodatkowych administratorów.

## <a name="add-administrators"></a>Dodawanie administratorów

Aby dodać administratorów:

1. Połącz się z portalem Azure w [portal.azure.com](https://portal.azure.com).
2. Zaloguj się przy użyciu konta używanego do zakupu miesięcznych subskrypcji programu Visual Studio.
3. W obszarze **Usługi platformy Azure**wybierz pozycję Zarządzanie **kosztami + Rozliczenia**.
   > [!div class="mx-imgBorder"]
   > ![Wybieranie opcji Zarządzanie kosztami + Rozliczenia w ramach usług platformy Azure](_img/cloud-admin/azure-cost-billing.png)
4. Na liście **Moje subskrypcje** wybierz subskrypcję platformy Azure, która została użyta do dokonania zakupu.
   > [!div class="mx-imgBorder"]
   > ![Wybierz subskrypcję](_img/cloud-admin/subscription-list.png)
5. Kliknij **pozycję Kontrola dostępu (IAM)**, która znajduje się w górnej części listy w lewym okienku nawigacji.
6. Kliknij kartę **Dodaj** u góry strony.
7. Kliknij **pozycję Dodaj przypisanie roli**.
   > [!div class="mx-imgBorder"]
   > ![Wybieranie opcji Kontrola dostępu, dodawanie, dodawanie przypisania roli](_img/cloud-admin/access-control-add.png)
8. W okienku wysunięcia po prawej stronie kliknij pozycję rozwijaną **Rola** u góry okienka, przewiń w dół i wybierz pozycję **Administrator dostępu użytkownika**.
9. Na liście użytkowników przewiń w dół do użytkownika, którego chcesz ustanowić administratora, i wybierz ich. 
   > [!div class="mx-imgBorder"]
   > ![Wybierz rolę, administrator dostępu użytkownika](_img/cloud-admin/add-role-user-access-admin.png)
10. Kliknij przycisk **Zapisz**.
11. Kliknij kartę **Przypisania ról,** aby sprawdzić, czy wybrany użytkownik jest teraz wyświetlany jako administrator dostępu do użytkownika.

Nowy administrator może teraz zalogować się do [portalu administracyjnego](https://manage.visualstudio.com), wybierz tę samą subskrypcję platformy Azure, która została użyta do zakupu miesięcznych subskrypcji z listy w lewym górnym rogu strony i rozpocząć zarządzanie tymi subskrypcjami.

> [!NOTE]
> Jeśli widzisz użytkowników z dostępem do edytowania miesięcznych subskrypcji, które nie zostały ustanowione jako administratorzy, mogą one mieć role w podstawowej subskrypcji platformy Azure, które umożliwiają im zarządzanie subskrypcjami. Te role obejmują: właściciela, współautora, administratora usługi lub współadministratora. Aby uzyskać więcej informacji, odwiedź stronę [Dodaj menedżerów rozliczeń](/azure/devops/organizations/billing/add-backup-billing-managers?view=vsts).

Aby uzyskać informacje na temat miesięcznych subskrypcji programu Visual Studio, zobacz [Omówienie](vscloud-overview.md) w obszarze Kupowanie subskrypcji. Aby kupić miesięczne subskrypcje programu Visual [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription)Studio, odwiedź witrynę Visual Studio Marketplace pod adresem .

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja usługi Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
Dowiedz się więcej o zarządzaniu subskrypcjami programu Visual Studio.
- [Przypisywanie poszczególnych subskrypcji](assign-license.md)
- [Przypisywanie wielu subskrypcji](assign-license-bulk.md)
- [Edytowanie subskrypcji](edit-license.md)
- [Określanie maksymalnego użycia](maximum-usage.md)



