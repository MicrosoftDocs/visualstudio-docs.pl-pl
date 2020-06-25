---
title: Dodawanie nowych miesięcznych subskrypcji programu Visual Studio do portalu administracyjnego subskrypcji | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 36f0d9f1-fe28-469f-a54c-dc46638270a8
ms.date: 06/23/2020
ms.topic: conceptual
description: Dowiedz się, jak nowo zakupione miesięczne subskrypcje programu Visual Studio w portalu administracyjnym subskrypcji
ms.openlocfilehash: abe0b7a84f0979de4bc1f59b6f82144c804c8c7e
ms.sourcegitcommit: 60315ba949aca1ff06fe431dbcbcfb0fedc1e8d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85307028"
---
# <a name="add-new-monthly-visual-studio-subscriptions-to-the-subscriptions-administration-portal"></a>Dodawanie nowych miesięcznych subskrypcji programu Visual Studio do portalu administracyjnego subskrypcji
Gdy kupisz nowe miesięczne subskrypcje programu Visual Studio przy użyciu subskrypcji platformy Azure, możesz dodać je do portalu administracyjnego subskrypcji, aby przypisać je do użytkowników.  

## <a name="how-do-i-know-if-i-need-to-add-my-subscriptions"></a>Jak mogę wiedzieć, czy muszę dodać Moje subskrypcje?
Kroki umożliwiające dodanie subskrypcji miesięcznych zależą od tego, jakiego rodzaju subskrypcje już posiadasz, i od tego, czy jesteś nowym administratorem.
- Jeśli jesteś nowym administratorem, sprawdzimy subskrypcje platformy Azure, na których masz uprawnienia administratora dostępu użytkownika po pierwszym zalogowaniu się do portalu administratora subskrypcji.  Jeśli wyszukasz miesięczne subskrypcje, dodamy je automatycznie. 
- Jeśli wcześniej dodano lub administrowano subskrypcje comiesięczne, Sprawdzamy nowe miesięczne subskrypcje przy każdym logowaniu. 
- Jeśli jesteś już administratorem subskrypcji nabytych za pośrednictwem licencjonowania zbiorowego, ale nie dodano wcześniej ani nie zarządzasz subskrypcjami miesięcznymi, musisz dodać je, korzystając z poniższych kroków.

## <a name="how-to-add-monthly-subscriptions"></a>Jak dodać subskrypcje miesięczne
1. Zaloguj się do portalu administracyjnego subskrypcji na stronie<https://manage.visualstudio.com>
1. Na karcie **Zarządzanie subskrybentami** wybierz listę rozwijaną **Nowa Umowa** . 
1. Wybierz pozycję **nowe subskrypcje miesięczne** na liście rozwijanej
   > [!div class="mx-imgBorder"]
   > ![Lista rozwijana Dodaj nowe subskrypcje miesięczne](_img/add-monthly-subs/add-subs-drop-down.png)
1. System będzie wyszukiwać dowolne subskrypcje platformy Azure, na których masz uprawnienia administratora dostępu użytkownika i zaimportowali wszystkie subskrypcje programu Visual Studio zakupione w ramach tych subskrypcji platformy Azure.
1. Jeśli nie znaleziono żadnych subskrypcji platformy Azure, na których masz uprawnienia administratora dostępu użytkowników, lub jeśli nie znaleziono żadnych subskrypcji programu Visual Studio, zostanie wyświetlony następujący komunikat:
   > [!div class="mx-imgBorder"]
   > ![Nie znaleziono nowych subskrypcji miesięcznych](_img/add-monthly-subs/no-subs-found.png)
1. Jeśli zostaną znalezione nowe subskrypcje miesięczne, zostanie wyświetlony komunikat z potwierdzeniem
   > [!div class="mx-imgBorder"]
   > ![Komunikat potwierdzający dodanie subskrypcji](_img/add-monthly-subs/subs-added-confirmation.png)

## <a name="things-to-keep-in-mind"></a>Rzeczy, o których należy pamiętać
- Opcja dodawania nowych subskrypcji miesięcznych będzie dostępna tylko podczas pierwszego zakupu.  Po dodaniu comiesięcznych subskrypcji sprawdzimy nowe subskrypcje za każdym razem, gdy zalogujesz się do portalu. 
- Gdy zostaną znalezione nowe subskrypcje, możesz zobaczyć, że są już przypisane do subskrybentów.  Wynika to z faktu, że istnieją inne administratorów z dostępem do subskrypcji platformy Azure, które mają już przypisane do użytkowników nowe subskrypcje programu Visual Studio.  Teraz, po dodaniu ich do portalu, można administrować tymi subskrypcjami. 

## <a name="next-steps"></a>Następne kroki
Po dodaniu subskrypcji możesz przystąpić do ich przypisywania do użytkowników.  Można to zrobić na kilka sposobów:
- [Przypisywanie subskrypcji pojedynczo](assign-license.md)
- [Przypisywanie subskrypcji wielu użytkownikom](assign-license-bulk.md)
- [Przypisywanie określonych subskrypcji do określonych użytkowników](assign-guid.md)

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja Microsoft 365](https://docs.microsoft.com/microsoft-365/)
