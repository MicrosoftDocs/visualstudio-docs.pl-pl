---
title: Przypisywanie licencji do subskrypcji programu Visual Studio | Dokumenty firmy Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 4e529a43-7aed-4eee-895d-862a631952df
ms.date: 03/02/2020
ms.topic: conceptual
description: Dowiedz się, jak administratorzy mogą przypisywać licencje subskrybentom
ms.openlocfilehash: 87334251532dbaa127d4def8c33a9814c28d42e1
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232703"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Przypisywanie licencji w portalu administracyjnym subskrypcji programu Visual Studio
Jako administrator subskrypcji programu Visual Studio można użyć portalu administracyjnego do przypisywania subskrypcji poszczególnym użytkownikom i grupom użytkowników.

W przypadku grup użytkowników masz możliwość wyboru sposobu przypisywania subskrypcji.  
- Subskrypcje można przypisywać po jednym naraz.
- Możesz również szybko i łatwo przesyłać listy subskrybentów i ich informacje o subskrypcji za pomocą funkcji [zbiorczego dodawania.](assign-license-bulk.md)
- Jeśli twoja organizacja korzysta z usługi Microsoft Azure Active Directory (Azure AD), możesz użyć grup usługi Azure AD do przypisywania subskrypcji grupom użytkowników.  (Ta funkcja jest wdrażana w fazach i może nie być natychmiast dostępna dla twojej organizacji).


## <a name="add-a-single-subscriber"></a>Dodawanie jednego subskrybenta
Poniżej opisano, jak przypisać subskrypcję programu Visual Studio do nowego użytkownika, aby mógł uzyskać dostęp do korzyści subskrypcji.

1. Zaloguj się do [portalu administracyjnego](https://manage.visualstudio.com).
2. Aby przypisać licencję jednemu subskrybentowi programu Visual Studio, u góry tabeli wybierz pozycję **Dodaj**, a następnie wybierz pozycję **Indywidualny subskrybent**.
   > [!div class="mx-imgBorder"]
   > ![Dodawanie jednego subskrybenta](_img/assign-license-add/add-subscriber-individual.png)
3. Wprowadź informacje w polach formularza dla nowego subskrybenta. Jeśli twoja organizacja korzysta z usługi Azure Active Directory, pole **Nazwa** działa jako funkcja wyszukiwania, aby znaleźć osoby w bieżącym katalogu, dzięki czemu można wybrać właściwego użytkownika z wyników wyszukiwania. Po wybraniu tej osoby e-mail logowania i powiadomienia zostaną automatycznie wypełnione.
   > [!div class="mx-imgBorder"]
   > ![Szczegóły subskrybenta](_img/assign-license-add/subscriber-details.png)

    Jeśli chcesz, aby ten subskrybent miał dostęp do pobierania oprogramowania po zalogowaniu się do [portalu subskrypcji programu Visual Studio,](https://my.visualstudio.com?wt.mc_id=o~msft~docs)upewnij się, że przełącznik pobierania został włączony w sekcji Ustawienia **pobierania.** Jeśli użytkownik zdecyduje się wyłączyć pobieranie, nie będzie miał dostępu do pobierania oprogramowania, ale nadal będzie miał dostęp do wszystkich innych korzyści zawartych w subskrypcji.
   > [!div class="mx-imgBorder"]
   > ![Dostęp do plików do pobrania](media/access-to-downloads.png)

    Jeśli chcesz dodać własne uwagi dotyczące odwołań do subskrypcji, możesz to zrobić w sekcji **Dodaj odwołanie.**
   > [!div class="mx-imgBorder"]
   > ![Dodawanie własnych notatek referencyjnych do każdej subskrypcji](media/add-subscriber-reference-notes.png)

    Po zakończeniu wybierania opcji i wprowadzania danych dla subskrybenta wybierz pozycję **Dodaj** u dołu wysuwania opcji **Dodaj subskrybenta.**
   > [!div class="mx-imgBorder"]
   > ![Wybieranie przycisku Dodaj](media/add-button.png)

## <a name="resend-assignment-emails"></a>Ponowne wysyłanie wiadomości e-mail z przypisaniami
Po dodaniu subskrybenta wiadomość e-mail z przydziałem zostanie automatycznie wysłana do nowego subskrybenta wraz z dalszymi instrukcjami. Możesz wysłać wiadomość e-mail z przydziałem ponownie w dowolnym momencie, wybierając subskrybenta i klikając przycisk **Wyślij ponownie** w górnym menu.  Aby ponownie wysłać wiadomości e-mail do wielu użytkowników, przytrzymaj naciśnięty klawisz **Ctrl** podczas wybierania subskrybentów.  Po kliknięciu przycisku **Prześlij ponownie** zobaczysz okno dialogowe z prośbą o potwierdzenie, że chcesz ponownie wysłać je do tych subskrybentów.  

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja usługi Microsoft 365](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>Następne kroki
- Masz wielu użytkowników do dodania?  Dowiedz się, jak przypisać subskrypcje [wielu subskrybentom](assign-license-bulk.md).
- Potrzebujesz pomocy?  Skontaktuj się z [pomocą techniczną administracji i subskrypcji](https://visualstudio.microsoft.com/support/support-overview-vs)programu Visual Studio .


