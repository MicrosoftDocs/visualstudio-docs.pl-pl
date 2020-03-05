---
title: Przypisywanie licencji do subskrypcji programu Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/02/2020
ms.topic: conceptual
description: Dowiedz się, jak Administratorzy mogą przypisywać licencje do subskrybentów
ms.openlocfilehash: 3d444f930d1fab166d437911b5609caf75cad09e
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263317"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Przypisywanie licencji w portalu administratora subskrypcji programu Visual Studio
Jako administrator subskrypcji programu Visual Studio można używać portalu administracyjnego do przypisywania subskrypcji do poszczególnych użytkowników i grup użytkowników.

W przypadku grup użytkowników można wybrać sposób przypisywania subskrypcji.  
- Subskrypcje można przypisywać pojedynczo.
- Możesz również szybko i łatwo przekazywać listy subskrybentów i ich informacje o subskrypcji za pomocą funkcji [zbiorczego dodawania](assign-license-bulk.md) .
- Jeśli Twoja organizacja korzysta z usługi Microsoft Azure Active Directory (Azure AD), możesz użyć grup usługi Azure AD do przypisywania subskrypcji do grup użytkowników.  (Ta funkcja jest wdrażana w fazach i może nie być natychmiast dostępna dla Twojej organizacji).


## <a name="add-a-single-subscriber"></a>Dodaj pojedynczego abonenta
Poniżej przedstawiono sposób przypisywania subskrypcji programu Visual Studio do nowego użytkownika w celu uzyskania dostępu do korzyści z subskrypcji.

1. Zaloguj się do [portalu administracyjnego](https://manage.visualstudio.com).
2. Aby przypisać licencję do pojedynczego subskrybenta programu Visual Studio, w górnej części tabeli wybierz pozycję **Dodaj**, a następnie wybierz opcję **indywidualny subskrybent**.
   > [!div class="mx-imgBorder"]
   > ![dodać jednego abonenta](_img/assign-license-add/add-subscriber-individual.png)
3. Wprowadź informacje w polach formularza dla nowego subskrybenta. Jeśli Twoja organizacja używa Azure Active Directory, pole **name** działa jako funkcja wyszukiwania, aby znaleźć osoby w bieżącym katalogu, dzięki czemu można wybrać odpowiedniego użytkownika z wyników wyszukiwania. Po wybraniu tej osoby wiadomość e-mail z logowaniem i wiadomości e-mail z powiadomieniem będą automatycznie wypełniane.
   > [!div class="mx-imgBorder"]
   > ![szczegóły subskrybenta](_img/assign-license-add/subscriber-details.png)

    Jeśli chcesz, aby ten subskrybent miał dostęp do pobierania oprogramowania po zalogowaniu się do [portalu subskrypcji programu Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), upewnij się, że włączono przełącznik pobierania w sekcji **ustawienia pobierania** . Jeśli zdecydujesz się wyłączyć pobieranie, użytkownik nie będzie miał dostępu do pobierania oprogramowania, ale nadal będzie miał dostęp do wszystkich innych korzyści uwzględnionych w subskrypcji.
   > [!div class="mx-imgBorder"]
   > ![dostęp do plików do pobrania](media/access-to-downloads.png)

    Jeśli chcesz dodać własne informacje referencyjne do subskrypcji, możesz to zrobić w sekcji **Dodaj odwołanie** .
   > [!div class="mx-imgBorder"]
   > ![dodać własne informacje o odwołaniach do każdej subskrypcji](media/add-subscriber-reference-notes.png)

    Po zakończeniu wybierania opcji i wprowadzaniu danych dla subskrybenta wybierz pozycję **Dodaj** w dolnej części okna **Dodawanie subskrybenta** .
   > [!div class="mx-imgBorder"]
   > ![wybierz przycisk Dodaj](media/add-button.png)

## <a name="resend-assignment-emails"></a>Wyślij ponownie wiadomości e-mail z przypisaniem
Po dodaniu subskrybenta wiadomość e-mail z przypisaniem zostanie automatycznie wysłana do nowego subskrybenta z dodatkowymi instrukcjami. W dowolnym momencie możesz wysłać wiadomość e-mail z przypisaniem, wybierając abonenta i klikając przycisk **Wyślij ponownie** w górnym menu.  Aby ponownie wysyłać wiadomości e-mail do wielu użytkowników, przytrzymaj wciśnięty klawisz **Ctrl** podczas wybierania subskrybentów.  Po kliknięciu przycisku **Wyślij ponownie** zobaczysz okno dialogowe z prośbą o potwierdzenie, że chcesz ponownie wysłać do tych subskrybentów.  

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja Microsoft 365](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>Następne kroki
- Masz dużo użytkowników do dodania?  Dowiedz się, jak przypisać subskrypcje do [wielu subskrybentów](assign-license-bulk.md).
- Potrzebujesz pomocy?  Skontaktuj się z [pomocą techniczną programu Visual Studio Administration i subscriptions](https://visualstudio.microsoft.com/support/support-overview-vs).


