---
title: Dodaj nowe subskrypcje miesięczne do portalu administracyjnego subskrypcji | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 36f0d9f1-fe28-469f-a54c-dc46638270a8
ms.date: 03/19/2021
ms.topic: how-to
description: Dowiedz się, jak nowo zakupione miesięczne subskrypcje programu Visual Studio w portalu administracyjnym subskrypcji
ms.openlocfilehash: 931f297a650926e4da5c13271a58091c9f00ddd3
ms.sourcegitcommit: d8d230791890cda532c263d04288dc13d2261c7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2021
ms.locfileid: "104757649"
---
# <a name="add-new-monthly-visual-studio-subscriptions-to-the-subscriptions-administration-portal"></a>Dodawanie nowych miesięcznych subskrypcji programu Visual Studio do portalu administracyjnego subskrypcji
Gdy kupisz nowe miesięczne subskrypcje programu Visual Studio przy użyciu subskrypcji platformy Azure, możesz dodać je do portalu administracyjnego subskrypcji, aby przypisać je do użytkowników.  

## <a name="how-do-i-know-if-i-need-to-add-my-subscriptions"></a>Jak mogę wiedzieć, czy muszę dodać Moje subskrypcje?
Kroki umożliwiające dodanie subskrypcji miesięcznych zależą od tego, jakiego rodzaju subskrypcje już posiadasz, i od tego, czy jesteś nowym administratorem.
- Jeśli jesteś nowym administratorem, sprawdzimy subskrypcje platformy Azure, na których masz uprawnienia administratora dostępu użytkownika po pierwszym zalogowaniu się do portalu administratora subskrypcji.  Jeśli wyszukasz miesięczne subskrypcje, dodamy je automatycznie. 
- Jeśli wcześniej dodano lub administrowano subskrypcje comiesięczne, Sprawdzamy nowe miesięczne subskrypcje przy każdym logowaniu. 
- Jeśli jesteś już administratorem subskrypcji uzyskanymi za pośrednictwem licencjonowania zbiorowego, ale nie dodano wcześniej ani nie zarządzasz subskrypcjami miesięcznymi, musisz dodać je, korzystając z poniższych kroków.

## <a name="how-to-add-monthly-subscriptions"></a>Jak dodać subskrypcje miesięczne
1. Zaloguj się do portalu administracyjnego subskrypcji na stronie <https://manage.visualstudio.com>
1. Na karcie **Zarządzanie subskrybentami** wybierz listę rozwijaną **Dodaj umowę** . 
1. Wybierz pozycję **nowe subskrypcje miesięczne** na liście rozwijanej
   > [!div class="mx-imgBorder"]
   > ![Lista rozwijana Dodaj nowe subskrypcje miesięczne](_img/add-monthly-subs/add-subs-drop-down.png "Wybierz pozycję Dodaj umowę, a następnie pozycję "nowe subskrypcje miesięczne".")
1. System będzie wyszukiwać dowolne subskrypcje platformy Azure, na których masz uprawnienia administratora dostępu użytkownika i zaimportowali wszystkie subskrypcje programu Visual Studio zakupione w ramach tych subskrypcji platformy Azure.
1. Jeśli nie znaleziono żadnych subskrypcji platformy Azure, na których masz uprawnienia administratora dostępu użytkowników, lub jeśli nie znaleziono żadnych subskrypcji programu Visual Studio, zostanie wyświetlony następujący komunikat:
   > [!div class="mx-imgBorder"]
   > ![Nie znaleziono nowych subskrypcji miesięcznych](_img/add-monthly-subs/no-subs-found.png "Komunikat o błędzie informujący o braku dostępności subskrypcji platformy Azure lub subskrypcji programu Visual Studio.")
1. Jeśli zostaną znalezione nowe subskrypcje miesięczne, zostanie wyświetlony komunikat z potwierdzeniem
   > [!div class="mx-imgBorder"]
   > ![Komunikat potwierdzający dodanie subskrypcji](_img/add-monthly-subs/subs-added-confirmation.png "Zostanie wyświetlony komunikat potwierdzający, że dodano subskrypcje.")

## <a name="things-to-keep-in-mind"></a>Rzeczy, o których należy pamiętać
- Opcja dodawania nowych subskrypcji miesięcznych będzie dostępna tylko podczas pierwszego zakupu.  Po dodaniu comiesięcznych subskrypcji sprawdzimy nowe subskrypcje za każdym razem, gdy zalogujesz się do portalu. 
- Gdy zostaną znalezione nowe subskrypcje, możesz zobaczyć, że są już przypisane do subskrybentów.  Wynika to z faktu, że istnieją inne Administratorzy z dostępem do subskrypcji platformy Azure, które mają już przypisane do użytkowników nowe subskrypcje programu Visual Studio.  Teraz, po dodaniu ich do portalu, można administrować tymi subskrypcjami. 

## <a name="support-resources"></a>Zasoby pomocy technicznej
- Aby uzyskać pomoc dotyczącą administrowania subskrypcjami programu Visual Studio, skontaktuj się z [pomocą techniczną subskrypcji programu Visual Studio](https://aka.ms/vsadminhelp).

## <a name="next-steps"></a>Następne kroki
Po dodaniu subskrypcji możesz przystąpić do ich przypisywania do użytkowników.  Można to zrobić na kilka sposobów:
- [Przypisywanie subskrypcji pojedynczo](assign-license.md)
- [Przypisywanie subskrypcji wielu użytkownikom](assign-license-bulk.md)
- [Przypisywanie określonych subskrypcji do określonych użytkowników](assign-guid.md)

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](/visualstudio/)
- [Azure DevOps documentation (Dokumentacja usługi Azure DevOps)](/azure/devops/)
- [Dokumentacja platformy Azure](/azure/)
- [Dokumentacja Microsoft 365](/microsoft-365/)