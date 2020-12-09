---
title: Przypisywanie subskrypcji programu Visual Studio użytkownikom | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 4e529a43-7aed-4eee-895d-862a631952df
ms.date: 09/21/2020
ms.topic: conceptual
description: Dowiedz się, jak Administratorzy mogą przypisywać licencje do subskrybentów
ms.openlocfilehash: dd80a14a3ff57100f210fd7ae1b882c0ab7a9faf
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915417"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Przypisywanie licencji w portalu administratora subskrypcji programu Visual Studio
Jako administrator subskrypcji programu Visual Studio można używać portalu administracyjnego do przypisywania subskrypcji do poszczególnych użytkowników i grup użytkowników.

W przypadku grup użytkowników można wybrać sposób przypisywania subskrypcji.  
- Subskrypcje można przypisywać pojedynczo.
- Możesz również szybko i łatwo przekazywać listy subskrybentów i ich informacje o subskrypcji za pomocą funkcji [zbiorczego dodawania](assign-license-bulk.md) .
- Jeśli Twoja organizacja korzysta z usługi Microsoft Azure Active Directory (Azure AD), możesz [użyć grup usługi Azure AD do przypisywania subskrypcji](./assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) do grup użytkowników.  


## <a name="add-a-single-subscriber"></a>Dodaj pojedynczego abonenta
Obejrzyj wideo lub przeczytaj, aby dowiedzieć się, jak przypisać subskrypcję programu Visual Studio do nowego użytkownika, aby mogli uzyskać dostęp do korzyści z subskrypcji.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vpPh]


1. Zaloguj się do [portalu administracyjnego](https://manage.visualstudio.com).
2. Aby przypisać licencję do pojedynczego subskrybenta programu Visual Studio, w górnej części tabeli wybierz pozycję **Dodaj**, a następnie wybierz opcję **indywidualny subskrybent**.
   > [!div class="mx-imgBorder"]
   > ![Dodaj pojedynczego abonenta](_img/assign-license-add/add-subscriber-individual.png "Wybierz pozycję Dodaj, a następnie wybierz opcję indywidualny subskrybent, aby przypisać pojedynczą subskrypcję.")
3. Wprowadź informacje w polach formularza dla nowego subskrybenta. Jeśli Twoja organizacja używa Azure Active Directory, pole **name** działa jako funkcja wyszukiwania, aby znaleźć osoby w bieżącym katalogu, dzięki czemu można wybrać odpowiedniego użytkownika z wyników wyszukiwania. Po wybraniu tej osoby wiadomość e-mail z logowaniem i wiadomości e-mail z powiadomieniem będą automatycznie wypełniane.  Jeśli subskrybent nie zostanie znaleziony w organizacji, wiadomość e-mail z powiadomieniem nie zostanie automatycznie wypełniona, ale będzie można ręcznie dodać inny adres e-mail, na który będą wysyłane wiadomości e-mail powiązane z subskrypcją.  Jeśli usługa poczty e-mail blokuje przychodzące wiadomości e-mail na adresy e-mail logowania, ważne jest, aby określić inny adres e-mail z powiadomieniem, aby Subskrybenci i Administratorzy otrzymywali ważne wiadomości e-mail powiązane z subskrypcją firmy Microsoft.
   > [!div class="mx-imgBorder"]
   > ![Szczegóły subskrybenta](_img/assign-license-add/subscriber-details.png "Wprowadź nazwę abonenta i inne szczegóły lub wybierz spośród członków dzierżawy.")

    > [!NOTE]
    > Aby elementy członkowskie dzierżawy Azure Active Directory były widoczne po wprowadzeniu nazwy abonenta, administrator musi być członkiem dzierżawy. 


    Jeśli chcesz, aby ten subskrybent miał dostęp do pobierania oprogramowania po zalogowaniu się do [portalu subskrypcji programu Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), upewnij się, że włączono przełącznik pobierania w sekcji **ustawienia pobierania** . Jeśli zdecydujesz się wyłączyć pobieranie, użytkownik nie będzie miał dostępu do pobierania oprogramowania.  Dostęp do kluczy produktów również zostanie wyłączony.  Subskrybenci nadal będą mieć dostęp do wszystkich innych korzyści uwzględnionych w subskrypcji.
   > [!div class="mx-imgBorder"]
   > ![Dostęp do plików do pobrania](media/access-to-downloads.png "Wybierz opcję "Zezwól", aby zapewnić subskrybentowi dostęp do pobierania oprogramowania.")

    Jeśli chcesz dodać własne informacje referencyjne do subskrypcji, możesz to zrobić w sekcji **Dodaj odwołanie** .
   > [!div class="mx-imgBorder"]
   > ![Dodawanie własnych notatek referencyjnych do każdej subskrypcji](media/add-subscriber-reference-notes.png "Użyj pola odwołanie, aby zarejestrować wszelkie uwagi dotyczące tej subskrypcji.")

    Po zakończeniu wybierania opcji i wprowadzaniu danych dla subskrybenta wybierz pozycję **Dodaj** w dolnej części okna **Dodawanie subskrybenta** .
   > [!div class="mx-imgBorder"]
   > ![Wybierz przycisk Dodaj](media/add-button.png "Wybierz pozycję Dodaj, aby zapisać informacje i przypisać subskrypcję do subskrybenta.")

## <a name="why-use-a-different-notification-email-address"></a>Dlaczego warto używać innego adresu e-mail powiadomienia?
Niektóre organizacje konfigurują swoje usługi poczty e-mail, aby blokować przychodzące wiadomości e-mail z innych domen.  Zablokowanie przychodzących wiadomości e-mail oznacza, że Subskrybenci i Administratorzy nie będą mieć ważnej komunikacji:
- Subskrybenci nie otrzymają powiadomienia o przypisaniu do nich subskrypcji.  Uniemożliwi to również aktywację niektórych z uwzględnionych korzyści.  
- Subskrybenci, którym przypisano subskrypcje programu Visual Studio z usługą GitHub Enterprise, nie otrzymają zaproszenia do wzięcia udziału w organizacji GitHub, co oznacza, że nie będą w stanie zaakceptować zaproszenia. Aby uzyskać dostęp do organizacji usługi GitHub **, należy zaakceptować zaproszenie wysłane pocztą e-mail** . 
- Administratorzy nie będą powiadamiani, gdy zostaną dodani do umowy, otrzymują comiesięczne instrukcje administratora lub powiadomienia o zmianach funkcji, które mają wpływ na sposób zarządzania subskrypcjami.

Przy użyciu adresu e-mail z powiadomieniem można zezwolić subskrybentom na otrzymywanie ważnych informacji o ich subskrypcjach bez zmiany ich adresów e-mail logowania.  

## <a name="resend-assignment-emails"></a>Wyślij ponownie wiadomości e-mail z przypisaniem
Po dodaniu subskrybenta wiadomość e-mail z przypisaniem zostanie automatycznie wysłana do nowego subskrybenta z dodatkowymi instrukcjami. W dowolnym momencie możesz wysłać wiadomość e-mail z przypisaniem, wybierając subskrybenta, a następnie wybierając przycisk **Wyślij ponownie** w górnym menu.  Aby ponownie wysyłać wiadomości e-mail do wielu użytkowników, przytrzymaj wciśnięty klawisz **Ctrl** podczas wybierania subskrybentów.  Po wybraniu przycisku **Wyślij ponownie** zobaczysz okno dialogowe z prośbą o potwierdzenie, że chcesz ponownie wysłać do tych subskrybentów.  



## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](/visualstudio/)
- [Azure DevOps documentation (Dokumentacja usługi Azure DevOps)](/azure/devops/)
- [Dokumentacja platformy Azure](/azure/)
- [Dokumentacja Microsoft 365](/microsoft-365/)


## <a name="next-steps"></a>Następne kroki
- Masz dużo użytkowników do dodania?  Dowiedz się, jak przypisać subskrypcje do [wielu subskrybentów](assign-license-bulk.md).
- Potrzebujesz pomocy?  Skontaktuj się z [pomocą techniczną programu Visual Studio Administration i subscriptions](https://visualstudio.microsoft.com/support/support-overview-vs).