---
title: Konfigurowanie administratorów dla subskrypcji w chmurze | Dokumentacja firmy Microsoft
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/28/2018
ms.topic: conceptual
description: Konfigurowanie administratorów w przypadku subskrypcji chmury
ms.openlocfilehash: 85371dd77b99fc5013843bb815082cc0f84cff33
ms.sourcegitcommit: f369ff7e84b0216f01570a486c7be80ca6d0e61a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68250690"
---
# <a name="set-up-administrators-for-visual-studio-cloud-subscriptions"></a>Skonfiguruj administratorów w przypadku subskrypcji chmury programu Visual Studio

Subskrypcje programu Visual Studio Cloud są zarządzane przez administratorów. Osoby te mogą przypisywanie subskrypcji, edytować przypisania, Dodaj lub usuń subskrypcje i wykonywać inne zadania zarządzania subskrypcją.

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>Właściciel subskrypcji platformy Azure jest pierwszą administratora

Po zakupie subskrypcji chmury programu Visual Studio, jako właściciel subskrypcji platformy Azure, używany do robienia zakupów, są automatycznie konfigurujesz jako administrator dla tych subskrypcji.

Możesz kupić subskrypcje w chmurze za pośrednictwem [Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions), kontaktując się dostawca rozwiązań w chmurze. Jeśli kupujesz za pośrednictwem programu Visual Studio Marketplace, na końcu doświadczenia podczas zakupu, użytkownik będzie miał możliwość zarządzania użytkownikami. Wybranie, czy opcja spowoduje przejście do portalu zarządzania subskrypcjami programu Visual Studio — [ https://manage.visualstudio.com ](https://manage.visualstudio.com).

Po dokonaniu zakupu subskrypcji, możesz odwiedzić stronę [portalu zarządzania](https://manage.visualstudio.com) w dowolnym momencie. Tak. wystarczy zalogować się do portalu i wybierz odpowiednią subskrypcję platformy Azure w lewym górnym rogu i rogu.

Jako właściciel subskrypcji platformy Azure używane do zakupu subskrypcji w chmurze można także przypisać administratorów.

## <a name="add-administrators"></a>Dodaj administratorów

Aby dodać administratorów:

1. Nawiązać połączenie z witryny Azure Portal pod [portal.azure.com](https://portal.azure.com).
2. Zaloguj się przy użyciu konta, którego użyto do zakupu subskrypcji chmury programu Visual Studio.
3. W okienku nawigacji po lewej stronie, przewiń w dół do **Zarządzanie kosztami i rozliczenia**.
4. W **Moje subskrypcje** , wybierz subskrypcję platformy Azure, którego użyto w celu dokonania zakupu.
5. Kliknij przycisk **kontroli dostępu**, który znajduje się w górnej części listy w okienku nawigacji po lewej stronie.
6. Kliknij przycisk **Dodaj** kartę w górnej części strony.
7. W okienku staną się po prawej stronie kliknij nazwę subskrybenta, którego chcesz dokonać administrator.
8. Kliknij pozycję **roli** listy rozwijanej w górnej części okienka, przewiń w dół i wybierz **Administrator dostępu użytkowników**.
9. Kliknij polecenie **Zapisz**.

Subskrybent wyznaczonych pojawia się w środku strony, a ich rolą jest wyświetlany jako "Administrator dostępu użytkowników".

Nowy administrator może teraz zalogować do [portalu zarządzania](https://manage.visualstudio.com), wybrać tej samej subskrypcji platformy Azure, którego użyto do zakupu subskrypcji chmury z listy w górnym lewym rogu strony i rozpocząć zarządzanie tymi Subskrypcje.

> [!NOTE]
> Jeśli użytkownicy z dostępem do edycji Twoje subskrypcje w chmurze, które nie nawiązują jako Administratorzy, mogą mieć role w podstawowym subskrypcji platformy Azure, umożliwiające zarządzanie subskrypcjami. Te role obejmują: właścicielem, współautorem, administrator usługi lub współadministratora. Aby uzyskać więcej informacji, odwiedź stronę [dodać menedżerów rozliczeń](/azure/devops/organizations/billing/add-backup-billing-managers?view=vsts).

Aby uzyskać informacje dotyczące subskrypcji chmury programu Visual Studio, zobacz [Przegląd](vscloud-overview.md) w ramach zakupu subskrypcji w chmurze. Aby kupić subskrypcje chmury programu Visual Studio, odwiedź Visual Studio Marketplace na [ https://marketplace.visualstudio.com/subscriptions ](https://marketplace.visualstudio.com/subscription).
