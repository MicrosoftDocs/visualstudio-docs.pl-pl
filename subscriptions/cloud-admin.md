---
title: Konfigurowanie administratorów dla subskrypcji chmury | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: lank
ms.date: 07/17/2019
ms.topic: conceptual
description: Konfigurowanie administratorów dla subskrypcji chmury
ms.openlocfilehash: 62a350e6061444e3c75878dfd89739011c4641d5
ms.sourcegitcommit: 57866dd72fd0e15ce61128df70729b427a2d02eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/18/2019
ms.locfileid: "68315203"
---
# <a name="set-up-administrators-for-visual-studio-cloud-subscriptions"></a>Konfigurowanie administratorów dla subskrypcji programu Visual Studio w chmurze

Subskrypcje programu Visual Studio w chmurze są zarządzane przez administratorów. Osoby te mogą przypisywać subskrypcje, edytować przypisania, dodawać i usuwać subskrypcje oraz wykonywać inne zadania związane z zarządzaniem subskrypcjami.

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>Właścicielem subskrypcji platformy Azure jest pierwszy administrator

Gdy kupujesz subskrypcje w chmurze programu Visual Studio, jako właściciel subskrypcji platformy Azure używanej do dokonywania zakupów, zostanie on automatycznie skonfigurowany jako administrator dla tych subskrypcji.

Subskrypcje chmury można zakupić za pomocą [Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions)lub skontaktować się z dostawcą rozwiązań w chmurze. Jeśli kupujesz za pomocą Visual Studio Marketplace, pod koniec korzystania z zakupu będziesz mieć możliwość zarządzania użytkownikami. Wybranie tej opcji spowoduje przejście do portalu administracyjnego subskrypcji programu Visual Studio — [https://manage.visualstudio.com](https://manage.visualstudio.com).

Po zakupieniu subskrypcji możesz w dowolnym momencie odwiedzić [Portal administracyjny](https://manage.visualstudio.com) . Po prostu zaloguj się do portalu i wybierz odpowiednią subskrypcję platformy Azure w lewym górnym rogu.

Jako właściciel subskrypcji platformy Azure używanej do zakupu subskrypcji w chmurze możesz także przypisać dodatkowych administratorów.

## <a name="add-administrators"></a>Dodaj administratorów

Aby dodać administratorów:

1. Połącz się z witryną Azure Portal pod adresem [Portal.Azure.com](https://portal.azure.com).
2. Zaloguj się przy użyciu konta użytego do zakupu subskrypcji programu Visual Studio w chmurze.
3. W lewym okienku nawigacji przewiń w dół do **Cost Management i**rozliczeń.
4. Z listy **Moje subskrypcje** wybierz subskrypcję platformy Azure, która została użyta do dokonania zakupu.
5. Kliknij pozycję **Kontrola dostępu**, która znajduje się w górnej części listy w okienku nawigacji po lewej stronie.
6. Kliknij kartę **Dodaj** w górnej części strony.
7. Kliknij przycisk **Dodaj przypisanie roli**.
8. W okienku po prawej stronie kliknij listę rozwijaną **rola** w górnej części okienka, przewiń w dół i wybierz pozycję **administrator dostępu użytkowników**.
9. Na liście użytkowników przewiń w dół do użytkownika, który ma być administratorem, i wybierz go. 
10. Kliknij polecenie **Zapisz**.
11. Kliknij kartę **przypisania ról** , aby sprawdzić, czy wybrany użytkownik jest teraz widoczny jako administrator dostępu użytkownika.

Nowy administrator może teraz zalogować się do [portalu administracyjnego](https://manage.visualstudio.com), wybrać tę samą subskrypcję platformy Azure, która została użyta do zakupu subskrypcji w chmurze z listy w lewym górnym rogu strony i rozpocząć zarządzanie tymi subskrypcjami.

> [!NOTE]
> Jeśli widzisz użytkowników z dostępem, aby edytować subskrypcje chmury, które nie zostały ustanowione jako administratorzy, mogą oni mieć role w podstawowej subskrypcji platformy Azure, które umożliwiają im zarządzanie subskrypcjami. Role te obejmują: właściciel, współautor, administrator usługi lub współadministrator. Aby uzyskać więcej informacji, odwiedź stronę [Dodawanie menedżerów](/azure/devops/organizations/billing/add-backup-billing-managers?view=vsts)rozliczeń.

Informacje o subskrypcjach programu Visual Studio Cloud można znaleźć w sekcji [Omówienie](vscloud-overview.md) kupowania subskrypcji. Aby kupić subskrypcje programu Visual Studio w chmurze, odwiedź Visual Studio Marketplace [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription)pod adresem.
