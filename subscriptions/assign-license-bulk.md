---
title: Przypisywanie licencji do grup użytkowników dla Visual Studio subskrypcji | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: c2853359-18fd-4be4-97a6-02230c862f92
ms.date: 03/21/2021
ms.topic: how-to
description: Dowiedz się, jak administratorzy mogą przypisywać licencje do wielu subskrybentów przy użyciu funkcji dodawania zbiorczego lub Microsoft Azure Active Directory grup
ms.openlocfilehash: 389eb3a578b0b025995c0cd60613d5bcce2e1a9f
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2021
ms.locfileid: "108641000"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Przypisywanie subskrypcji do wielu użytkowników
Portal administracyjny subskrypcji umożliwia dodawanie użytkowników jeden na raz lub w dużych grupach.  Aby dodać poszczególnych użytkowników, zobacz [Dodawanie pojedynczych użytkowników.](assign-license.md)

Aby dodać duże grupy użytkowników, możesz użyć funkcji dodawania zbiorczego, a jeśli Twoja organizacja korzysta z usługi Microsoft Azure Active Directory (Azure AD), możesz użyć grup usługi Azure AD. W tym artykule wyjaśniono proces dla obu opcji.  Obejrzyj ten film lub czytaj dalej, aby dowiedzieć się więcej na temat funkcji dodawania zbiorczego. 

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vxNq]

## <a name="use-bulk-add-to-assign-subscriptions"></a>Przypisywanie subskrypcji za pomocą dodawania zbiorczego
1. Zaloguj się do portalu administracyjnego Visual Studio subskrypcjami na stronie <https://manage.visualstudio.com> .

1. Aby dodać wielu subskrybentów jednocześnie, przejdź do karty **Zarządzanie subskrybentami.** Wybierz **kartę Dodaj,** a następnie **z** listy rozwijanej wybierz pozycję Dodaj zbiorczy.  

1. Dodawanie zbiorcze używa szablonu programu Microsoft Excel do przekazywania informacji o subskrybentach. W oknie dialogowym Przekazywanie wielu subskrybentów wybierz pozycję **Pobierz,** aby pobrać szablon.
   > [!div class="mx-imgBorder"]
   > ![Pobieranie szablonu programu Excel w celu przekazania wielu subskrybentów](media/download-template-upload-subscribers.png "Pobierz pusty szablon programu Excel, aby rozpocząć proces przypisywania zbiorczego.")
   >
   > [!NOTE]
   > Zawsze pobieraj najnowszą wersję tego szablonu. Jeśli używasz starszej wersji, przekazywanie zbiorcze może się nie powieść.

1. W arkuszu kalkulacyjnym programu Excel wypełnij pola informacjami dla osób, do których chcesz przypisać subskrypcje. *(Odwołanie* jest polem opcjonalnym). Po zakończeniu zapisz plik lokalnie.

    > [!NOTE]
    > Jedno z pól w szablonie umożliwia administratorom włączanie lub wyłączanie możliwości pobierania oprogramowania przez subskrybentów.  Wyłączenie pobierania powoduje również wyłączenie dostępu do kluczy produktów.

   Aby zapewnić bezproblemowe przekazywanie, należy przestrzegać następujących najlepszych rozwiązań:

    - Sprawdź, czy żadne z pól formularza nie zawiera przecinków.
    - Usuń spacje przed polami formularza i po nich.
    - Upewnij się, że nazwiska użytkowników nie zawierają dodatkowych spacji między dwu częściowymi nazwiskami (na przykład jeśli osoba ma dwuwątowe imię, takie jak "Maggie May", należy wpisać "MaggieMay", ponieważ system nie przycina dodatkowego miejsca).
    - Upewnij się, że wszystkie wymagane pola zostały wypełnione. 
    - Sprawdź **kolumnę Komunikat o błędzie.**  Jeśli zostaną wyświetlone jakiekolwiek błędy, rozwiąż je przed próbą przekazania pliku. 

1. Wróć do portalu administracyjnego Visual Studio Subskrypcje. W **oknie dialogowym Przekazywanie wielu subskrybentów** wybierz pozycję **Przeglądaj.**
   > [!div class="mx-imgBorder"]
   > ![Przejdź do zapisanego szablonu, aby przekazać wielu subskrybentów](media/bulk-add-browse-saved-template.png "Możesz przejść do lokalizacji pliku lub przeciągnąć go i upuścić w tym oknie dialogowym.")

1. Przejdź do zapisanego pliku programu Excel, a następnie wybierz przycisk **OK.**
   > [!div class="mx-imgBorder"]
   > ![Przekazywanie szablonu programu Excel w celu przekazania wielu subskrybentów](media/bulk-upload-subscribers.png "W tym miejscu zostanie wyświetlony szablon z Twoimi danymi.  Wybierz przycisk OK, aby rozpocząć przekazywanie.")

    Zostanie wyświetlone okno dialogowe postępu przekazywania.

    Jeśli szablon zawiera błędy, przekazywanie nie powiedzie się i zostaną wyświetlone błędy, aby można było poprawić szablon i spróbować przekazać zbiorczego ponownie.
   > [!div class="mx-imgBorder"]
   > ![Komunikat o błędzie w przypadku niepowodzenia przekazywania wielu subskrybentów](_img/assign-license-bulk/bulk-add-upload-failure.png "Ten komunikat zostanie wyświetlony, jeśli przekazany plik zawiera błędy.  Rozwiąż błędy i ponownie wykonaj proces dodawania zbiorczego.")

   Jeśli wystąpi błąd, wykonaj następujące kroki:
   1. Otwórz utworzony plik programu Excel, popraw problemy i zapisz plik.
   0. Wróć do portalu administracyjnego i odrzuć komunikat o błędzie.
   0. Wybierz **pozycję Dodaj.**
   0. Wybierz **pozycję Dodaj zbiorczo**.
   0. Ponieważ masz już zapisany plik programu Excel, nie musisz pobierać szablonu.  Wybierz **pozycję Przeglądaj,** znajdź właśnie zapisany plik, a następnie wybierz pozycję **Otwórz**.
   0. Wybierz przycisk **OK**.


    Po pomyślnym przekazyniu zobaczysz listę subskrybentów i komunikat potwierdzający.
   > [!div class="mx-imgBorder"]
   > ![Komunikat z potwierdzeniem, jeśli przekazywanie wielu subskrybentów powiedzie się](_img/assign-license-bulk/bulk-add-upload-success.png "Po pomyślnym zakończeniu przekazywania zostanie wyświetlony komunikat potwierdzający.")

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>Przypisywanie subskrypcji przy użyciu grup Azure Active Directory użytkowników 
Korzystanie z tej funkcji ułatwia korzystanie z przypisań subskrypcji. Możesz dodać Azure Active Directory zabezpieczeń w portalu administrowania subskrypcjami, co gwarantuje, że wszystkie osoby w grupie mają przypisaną subskrypcję. Aby to ułatwić, gdy osoby opuszczają organizację i zostaną usunięci z Azure Active Directory, ich dostęp do subskrypcji również zostanie usunięty. 


> [!IMPORTANT]
>
> Następujące ograniczenia dotyczą używania grup usługi Azure AD do dodawania subskrybentów:
> - Podczas początkowego dodawania grupy do portalu administracyjnego administrator musi być członkiem dzierżawy usługi AAD.  Po dodaniu grupy zmiany członkostwa w grupach nie wymagają zaangażowania administratora. 
> - Grupy muszą zawierać co najmniej jeden członek.  Puste grupy nie są obsługiwane.
> - Wszyscy użytkownicy muszą znajdować się na najwyższym poziomie grupy.  Grupy zagnieżdżone nie są obsługiwane.
> - Obsługiwane są tylko zaufane umowy. (Tylko umowy, które mogą "nadmiernie ująć" subskrypcje, są zaufane).
> - Wszyscy członkowie grupy muszą mieć adres e-mail skojarzony z kontem usługi Azure AD.
> - Oddzielne adresy e-mail dla powiadomień nie są obsługiwane w przypadku subskrypcji dodawanych przy użyciu grup usługi Azure AD.  

Obejrzyj to wideo lub czytaj dalej, aby dowiedzieć się więcej na temat dodawania subskrybentów przy użyciu Azure Active Directory grupy użytkowników. 
<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4rvvW]

1. Zaloguj się do portalu administracyjnego Visual Studio subskrypcjami na stronie [https://manage.visualstudio.com](https://manage.visualstudio.com) .

2. Aby dodać wielu subskrybentów jednocześnie, przejdź do karty **Zarządzanie subskrybentami.**

3. Wybierz **kartę Dodaj,** a następnie **Azure Active Directory grupę** na liście rozwijanej.  

   > [!div class="mx-imgBorder"]
   > ![Wybieranie zbiorczego dodawania przy użyciu usługi Azure AD](_img/assign-license-bulk/bulk-add-aad.png "Wybierz funkcję Zbiorcze dodawanie przy użyciu usługi Azure AD, aby ściągnąć subskrybentów z Azure Active Directory grupy.")

4. Zacznij wprowadzać nazwę grupy usługi Azure AD, która ma być dodawania do pola formularza. Spowoduje to przeszukanie dostępnych grup usługi Azure AD w organizacji. 

5. Po wybraniu grupy pole zostanie automatycznie wypełnione nazwą grupy. Będzie dostępna opcja wyświetlenia użytkowników w tej grupie przed ich dodaniem. Następnie możesz wybrać poziom subskrypcji, prawa pobierania i preferencje dotyczące komunikacji dla grupy. Jeśli chcesz, możesz dodać szczegóły do pola odwołania. 

   > [!div class="mx-imgBorder"]
   > ![Wybieranie grupy usługi Azure AD](_img/assign-license-bulk/bulk-add-aad-details.png "Wybierz nazwę grupy usługi Azure AD, aby dodać subskrybentów z tej grupy.")

6. Wybierz **pozycję Dodaj,** a następnie **potwierdź.** 

7. Aby wyświetlić dodaną grupę, przewiń w dół listy użytkowników.  

8. Wybierz **pozycję Wyświetl subskrybentów,** aby wyświetlić członków grupy. Możesz wyświetlić szczegółowe informacje o subskrybentach w grupie, ale nie możesz edytować subskrybentów ani przypisanych do nich subskrypcji.    

> [!NOTE]
> Jeśli subskrypcje zostały już przypisane indywidualnie do użytkowników, którzy zostaną później dodani jako część grupy usługi Azure AD, zostaną one dodane jako część grupy i nie będą już wyświetlane indywidualnie. Jeśli jednak indywidualna subskrypcja jest dla innego poziomu subskrypcji, będzie mieć dwie subskrypcje.  Przykład: jeśli użytkownik ma indywidualną Visual Studio Professional subskrypcji i jest członkiem grupy, do której przypisujesz Visual Studio Enterprise subskrypcji, będzie miał obie te subskrypcje.  
>
> Jeśli usuniesz subskrybenta z grupy Azure Active Directory, do których przypisano subskrypcje, odzwierciedlenie aktualizacji w portalu administracyjnym może potrwać do 24 godzin. 


## <a name="frequently-asked-questions"></a>Często zadawane pytania
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>Pytanie: Czy mogę wybrać wiele poziomów subskrypcji do przypisania w grupie usługi Azure AD? 
A: Nie — wszyscy w grupie otrzymują tę samą subskrypcję. 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>Pytanie: Czy mogę edytować szczegóły subskrybentów osób dodanych do grupy usługi Azure AD?  
A: Nie — aby zmodyfikować informacje dla poszczególnych subskrybentów, należy usunąć ich z grupy zabezpieczeń usługi Azure AD i przypisać im pojedynczą subskrypcję.  

### <a name="q-why-cant-i-see-the-option-to-use-azure-active-directory-groups-to-add-subscribers"></a>Pytanie: Dlaczego nie widzę opcji użycia grup Azure Active Directory do dodawania subskrybentów?
O: Ta funkcja jest obecnie dostępna tylko dla organizacji z zaufanymi umowami.  Wybierz przycisk **Szczegóły,** aby wyświetlić informacje o umowie.

   > [!div class="mx-imgBorder"]
   > ![Kliknij przycisk Szczegóły](_img/assign-license-bulk/bulk-add-agreement.png "Kliknij przycisk Szczegóły, aby zobaczyć, jakiego rodzaju umowę masz")

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-added-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>Pytanie: Ktoś został dodany do mojej grupy zabezpieczeń usługi Azure AD, ale nie widzę go dodanego w portalu witrynie Subscriptions Administration Portal i nie ma subskrypcji. Czemu nie?  
O: W zależności od tego, jak twoja organizacja skonfigurowała usługę Azure AD, mogą wystąpić opóźnienia do 24 godzin przed dodaniem użytkownika. Jeśli trwa to dłużej niż 24 godziny, odwiedź stronę pomocy technicznej Visual Studio [i subskrypcji.](https://my.visualstudio.com/gethelp)  

## <a name="see-also"></a>Zobacz też
- [Visual Studio dokumentacji](/visualstudio/)
- [Azure DevOps documentation (Dokumentacja usługi Azure DevOps)](/azure/devops/)
- [Dokumentacja platformy Azure](/azure/)
- [Microsoft 365 dokumentacji](/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
- Masz tylko jednego lub dwóch subskrybentów do dodania?  Zobacz Add [single users (Dodawanie pojedynczych użytkowników)](assign-license.md)
- Potrzebujesz pomocy? Skontaktuj się [z pomocą techniczną subskrypcji.](https://aka.ms/vsadminhelp)