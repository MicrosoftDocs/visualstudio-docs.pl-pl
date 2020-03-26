---
title: Przypisywanie licencji grupom użytkowników w ramach subskrypcji programu Visual Studio | Dokumenty firmy Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: c2853359-18fd-4be4-97a6-02230c862f92
ms.date: 03/02/2020
ms.topic: conceptual
description: Dowiedz się, jak administratorzy mogą przypisywać licencje wielu subskrybentom za pomocą funkcji dodawania zbiorczego lub grup usługi Microsoft Azure Active Directory
ms.openlocfilehash: 5a1327e497a48b6173afd4a7ad095dfcabacd098
ms.sourcegitcommit: dfa9476b69851c28b684ece66980bee735fef8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2020
ms.locfileid: "80274066"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Przypisywanie subskrypcji wielu użytkownikom
Portal administracyjny subskrypcji umożliwia dodawanie użytkowników jeden na raz lub w dużych grupach.  Aby dodać poszczególnych użytkowników, zobacz [Dodawanie pojedynczych użytkowników](assign-license.md).

Aby dodać duże grupy użytkowników, można użyć funkcji dodawania zbiorczego lub jeśli twoja organizacja korzysta z usługi Microsoft Azure Active Directory (Azure AD), możesz użyć grup usługi Azure AD. W tym artykule wyjaśniono proces dla obu opcji. 

## <a name="use-bulk-add-to-assign-subscriptions"></a>Przypisywanie subskrypcji za pomocą zbiorczego dodawania subskrypcji
1. Zaloguj się do portalu administracyjnego https://manage.visualstudio.comsubskrypcji programu Visual Studio pod adresem .

2. Aby dodać wielu subskrybentów jednocześnie, przejdź do **Add** karty **Zarządzaj subskrybentami.** **Bulk add**  

2. Dodawanie zbiorcze używa szablonu programu Microsoft Excel do przekazywania informacji o subskrybentach. W oknie dialogowym Przekazywanie wielu subskrybentów kliknij pozycję **Pobierz,** aby pobrać szablon.
   > [!div class="mx-imgBorder"]
   > ![Pobieranie szablonu programu Excel w celu przekazania wielu subskrybentów](media/download-template-upload-subscribers.png)
   >
   > [!NOTE]
   > Zawsze pobieraj najnowszą wersję tego szablonu. Jeśli używasz starszej wersji, przesyłanie zbiorcze może zakończyć się niepowodzeniem.

3. W arkuszu kalkulacyjnym programu Excel wypełnij pola informacjami dla osób, do których chcesz przypisać subskrypcje. *(Odwołanie* jest polem opcjonalnym). Zapisz plik lokalnie po zakończeniu.

   Aby zapewnić płynne przesyłanie, należy przestrzegać następujących sprawdzonych rozwiązań:

    - Upewnij się, że żadne z pól formularza nie zawiera przecinków.
    - Usuń spacje przed i po polach formularza.
    - Upewnij się, że nazwy użytkowników nie zawierają dodatkowych spacji między dwuczęściowymi imionami lub nazwiskami (na przykład, jeśli dana osoba ma dwuczęściowe imię, takie jak "Maggie May", powinna być wpisana jako "MaggieMay", ponieważ system nie przycina dodatkowego miejsca).
    - Upewnij się, że wszystkie wymagane pola zostały ukończone. 
    - Sprawdź **kolumnę Komunikat o błędzie.**  Jeśli na liście znajdują się błędy, rozwiąż je przed próbą przekazania pliku. 

4. Wróć do portalu administracji subskrypcjami programu Visual Studio. W oknie dialogowym **Przekazywanie wielu subskrybentów** kliknij pozycję **Przeglądaj**.
   > [!div class="mx-imgBorder"]
   > ![Przejdź do zapisanego szablonu, aby przesłać wielu subskrybentów](media/bulk-add-browse-saved-template.png)

5. Przejdź do zapisanego pliku programu Excel, a następnie kliknij przycisk **OK**.
   > [!div class="mx-imgBorder"]
   > ![Przekazywanie szablonu programu Excel w celu przekazania wielu subskrybentów](media/bulk-upload-subscribers.png)

    Zostanie wyświetlone okno dialogowe postępu przekazywania.

    Jeśli szablon zawiera błędy, przekazywanie zakończy się niepowodzeniem i zostaną wyświetlone błędy, dzięki czemu można poprawić szablon i spróbować ponownie przesłać zbiorczo.
   > [!div class="mx-imgBorder"]
   > ![Komunikat o błędzie, jeśli przekazywanie wielu subskrybentów nie powiedzie się](_img/assign-license-bulk/bulk-add-upload-failure.png)

   Jeśli wystąpi błąd, wykonaj następujące kroki:
   1. Otwórz utworzony plik programu Excel, rozwiążesz problemy i zapisz plik.
   0. Wróć do portalu administracyjnego i wybierz pozycję **Dodaj**.
   0. Wybierz **opcję Dodaj zbiorczo .**
   0. Ponieważ masz już zapisany plik programu Excel, nie trzeba pobierać szablonu.  Kliknij **przycisk Przeglądaj**, znajdź właśnie zapisany plik i kliknij przycisk **Otwórz**.
   0. Kliknij przycisk **OK**.


    Gdy przesyłanie zakończy się pomyślnie, zobaczysz listę subskrybentów i komunikat z potwierdzeniem.
   > [!div class="mx-imgBorder"]
   > ![Komunikat potwierdzający, jeśli przesłanie wielu subskrybentów zakończy się pomyślnie](_img/assign-license-bulk/bulk-add-upload-success.png)

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>Przypisywanie subskrypcji za pomocą grup usługi Azure Active Directory 
Korzystanie z tej funkcji ułatwia utrzymanie się na szczycie przypisań subskrypcji. Grupy zabezpieczeń usługi Azure Active Directory można dodać w portalu administracyjnym subskrypcji, który zapewni, że wszystkim osobom w grupie zostanie przypisana subskrypcja. Aby ułatwić, gdy osoby opuszczają organizację i są usuwane z usługi Azure Active Directory, ich dostęp do subskrypcji jest również usuwany. 


> [!IMPORTANT]
>
> Korzystanie z grup usługi Azure AD jest włączone w fazach.  Możesz nie od razu zobaczyć funkcji włączonej dla twoich umów.
>
> Następujące ograniczenia dotyczą korzystania z grup usługi Azure AD do dodawania subskrybentów:
> - Grupy muszą zawierać co najmniej jednego członka.  Puste grupy nie są obsługiwane.
> - Grupy muszą mieć mniej niż 1000 użytkowników 
> - Wszyscy użytkownicy muszą znajdować się na najwyższym poziomie grupy.  Grupy zagnieżdżone nie są obsługiwane
> - Obsługiwane są tylko zaufane umowy
> - Wszyscy członkowie grupy muszą mieć adres e-mail skojarzony z ich kontem usługi Azure AD
> - Oddzielne adresy e-mail dla powiadomień nie są obsługiwane dla subskrypcji dodanych przy użyciu grup usługi Azure AD.  

1. Zaloguj się do portalu administracyjnego [https://manage.visualstudio.com](https://manage.visualstudio.com)subskrypcji programu Visual Studio pod adresem .

2. Aby dodać wielu subskrybentów jednocześnie, przejdź do karty **Zarządzaj subskrybentami.**

3. Wybierz kartę **Dodaj,** a następnie wybierz **grupę usługi Azure Active Directory** w rozwijanej.  

   > [!div class="mx-imgBorder"]
   > ![Wybieranie zbiorczego dodawania przy użyciu usługi Azure AD](_img/assign-license-bulk/bulk-add-aad.png)

4. Rozpocznij wprowadzanie nazwy grupy usługi Azure AD, którą chcesz dodać do pola formularza. Spowoduje to przeszukanie dostępnych grup usługi Azure AD w organizacji. 

5. Po wybraniu grupy pole zostanie automatycznie wypełnione nazwą grupy. Przed dodaniem ich można wyświetlić użytkowników w tej grupie. Następnie możesz wybrać poziom subskrypcji, prawa do pobierania i preferencje komunikacji dla grupy. Jeśli chcesz, możesz dodać szczegóły do pola odniesienia. 

   > [!div class="mx-imgBorder"]
   > ![Wybieranie zbiorczego dodawania przy użyciu usługi Azure AD](_img/assign-license-bulk/bulk-add-aad-details.png)

6. Kliknij **pozycję Dodaj,** a następnie **potwierdź**. 

7. Aby wyświetlić dodaną grupę, przewiń do dolnej części listy użytkowników.  

8. Wybierz **pozycję Wyświetl subskrybentów,** aby wyświetlić członków grupy. Można wyświetlić szczegółowe informacje o subskrybentów w grupie, ale nie można wprowadzać żadnych zmian do subskrybentów lub subskrypcji, które są przypisane.    

> [!NOTE]
> Jeśli subskrypcje zostały już przypisane indywidualnie do użytkowników, którzy są następnie dodawane jako część grupy usługi Azure AD, zostaną one dodane jako część grupy i nie będą już wyświetlane indywidualnie. Jednak jeśli poszczególne subskrypcje jest dla innego poziomu subskrypcji, będą one miały dwie subskrypcje.  Przykład: Jeśli użytkownik ma indywidualną subskrypcję programu Visual Studio Professional i jest członkiem grupy, do której można przypisać subskrypcje programu Visual Studio Enterprise, będzie miał obie.  


> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4rvvW]

## <a name="frequently-asked-questions"></a>Często zadawane pytania
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>Pyt.: Czy mogę wybrać wiele poziomów subskrypcji, które mają być przypisane w grupie usługi Azure AD? 
O: Nie - wszyscy w grupie otrzymują tę samą subskrypcję. 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>Pyt.: Czy mogę edytować szczegóły subskrybenta osób dodanych w grupie usługi Azure AD?  
Odp.: Nie — aby zmodyfikować informacje dla poszczególnych subskrybentów, należy usunąć je z grupy zabezpieczeń usługi Azure AD i przypisać im subskrypcję indywidualnie.  

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-added-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>P: Dodałem kogoś do mojej grupy zabezpieczeń usługi Azure AD, ale nie widzę, aby zostały dodane w portalu administracyjnym subskrypcji i nie mają subskrypcji. Dlaczego nie?  
Odp.: W zależności od tego, jak twoja organizacja skonfigurowała usługę Azure AD, mogą wystąpić opóźnienia do 24 godzin przed dodaniem użytkownika. Jeśli trwa dłużej niż 24 godziny, [skontaktuj się z pomocą techniczną](https://visualstudio.microsoft.com/support/support-overview-vs).  

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja usługi Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
- Masz tylko jednego lub dwóch subskrybentów, aby dodać?  [Wyewidencjonuj Dodaj pojedynczych użytkowników](assign-license.md)
- Potrzebujesz pomocy? Skontaktuj się z [pomocą techniczną administracji i subskrypcji](https://visualstudio.microsoft.com/support/support-overview-vs)programu Visual Studio .
