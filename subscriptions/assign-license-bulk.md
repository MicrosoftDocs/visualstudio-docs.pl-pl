---
title: Przypisywanie licencji do grup użytkowników dla subskrypcji programu Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: c2853359-18fd-4be4-97a6-02230c862f92
ms.date: 03/21/2021
ms.topic: how-to
description: Dowiedz się, jak Administratorzy mogą przypisywać licencje do wielu subskrybentów za pomocą funkcji zbiorczego dodawania lub grup Microsoft Azure Active Directory
ms.openlocfilehash: 4744f689e9b03e4a6cf8c804409abddfde16c527
ms.sourcegitcommit: d7d9fb79448b3534923cc95071d1f91eabde88e8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104776899"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Przypisywanie subskrypcji wielu użytkownikom
Portal administrowania subskrypcjami pozwala dodawać użytkowników jeden w czasie lub w dużych grupach.  Aby dodać poszczególnych użytkowników, zobacz [Dodawanie pojedynczych użytkowników](assign-license.md).

Aby dodać dużych grup użytkowników, możesz użyć funkcji dodawania zbiorczego lub jeśli Twoja organizacja korzysta z usługi Microsoft Azure Active Directory (Azure AD), możesz użyć grup usługi Azure AD. W tym artykule opisano proces dla obu tych opcji.  Obejrzyj ten film wideo lub przeczytaj, aby dowiedzieć się więcej o funkcji dodawania zbiorczego. 

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vxNq]

## <a name="use-bulk-add-to-assign-subscriptions"></a>Używanie dodatków zbiorczych do przypisywania subskrypcji
1. Zaloguj się do portalu administracyjnego subskrypcji programu Visual Studio pod adresem <https://manage.visualstudio.com> .

1. Aby jednocześnie dodać wielu subskrybentów, przejdź do karty **Zarządzanie subskrybentami** . Wybierz kartę **Dodaj** , a następnie wybierz pozycję **Dodaj zbiorczo** na liście rozwijanej.  

1. Dodawanie zbiorcze używa szablonu programu Microsoft Excel do przekazywania informacji o subskrybencie. W oknie dialogowym przekazywanie wielu subskrybentów wybierz pozycję **Pobierz** , aby pobrać szablon.
   > [!div class="mx-imgBorder"]
   > ![Pobierz szablon programu Excel, aby przekazać wielu subskrybentów](media/download-template-upload-subscribers.png "Pobierz pusty szablon programu Excel, aby rozpocząć proces przydziału zbiorczego.")
   >
   > [!NOTE]
   > Zawsze Pobieraj najnowszą wersję tego szablonu. Jeśli używasz starszej wersji, przekazywanie zbiorcze może zakończyć się niepowodzeniem.

1. W arkuszu kalkulacyjnym programu Excel Wypełnij pola informacjami dla osób, do których chcesz przypisać subskrypcje. (*Odwołanie* jest polem opcjonalnym). Zapisz plik lokalnie po zakończeniu.

    > [!NOTE]
    > Jedno z pól szablonu umożliwia administratorom Włączanie lub wyłączanie możliwości pobierania oprogramowania przez subskrybentów.  Wyłączenie pobierania powoduje także wyłączenie dostępu do kluczy produktów.

   Aby zapewnić bezproblemowe przekazywanie, należy przestrzegać następujących najlepszych rozwiązań:

    - Sprawdź, czy żadne z pól formularza nie zawiera przecinków.
    - Usuń spacje przed polami formularza i po nich.
    - Upewnij się, że nazwy użytkowników nie zawierają dodatkowych spacji między imioną lub nazwiskiem dwóch części (na przykład jeśli osoba ma dwuczęściową nazwę, taką jak "Maggie", należy ją wpisać jako "MaggieMay", ponieważ system nie przycinania dodatkowego miejsca).
    - Upewnij się, że wszystkie wymagane pola są wypełnione. 
    - Sprawdź kolumnę **komunikat o błędzie** .  Jeśli występują błędy, usuń je przed podjęciem próby przekazania pliku. 

1. Wróć do portalu administracyjnego subskrypcji programu Visual Studio. W oknie dialogowym **przekazywanie wielu subskrybentów** wybierz pozycję **Przeglądaj**.
   > [!div class="mx-imgBorder"]
   > ![Przejdź do zapisanego szablonu, aby przekazać wielu subskrybentów](media/bulk-add-browse-saved-template.png "Możesz przejść do lokalizacji pliku lub przeciągnąć i upuścić ją w tym oknie dialogowym.")

1. Przejdź do zapisanego pliku programu Excel, a następnie wybierz przycisk **OK**.
   > [!div class="mx-imgBorder"]
   > ![Przekaż szablon programu Excel, aby przekazać wielu subskrybentów](media/bulk-upload-subscribers.png "Szablon zawierający dane zostanie wyświetlony w tym miejscu.  Wybierz przycisk OK, aby rozpocząć przekazywanie.")

    Zostanie wyświetlone okno dialogowe postęp przekazywania.

    Jeśli szablon zawiera błędy, przekazywanie zakończy się niepowodzeniem, a błędy zostaną wyświetlone, aby można było poprawić szablon i ponowić próbę przekazania zbiorczego.
   > [!div class="mx-imgBorder"]
   > ![Komunikat o błędzie, jeśli przekazywanie wielu subskrybentów zakończy się niepowodzeniem](_img/assign-license-bulk/bulk-add-upload-failure.png "Ten komunikat zostanie wyświetlony, jeśli przekazany plik zawiera błędy.  Usuń błędy i ponownie wykonaj proces dodawania zbiorczego.")

   Jeśli wystąpi błąd, wykonaj następujące kroki:
   1. Otwórz utworzony plik programu Excel, Usuń problemy i Zapisz plik.
   0. Wróć do portalu administracyjnego i Odrzuć komunikat o błędzie.
   0. Wybierz pozycję **Dodaj**.
   0. Wybierz pozycję **Dodaj zbiorczo**.
   0. Ponieważ plik programu Excel został już zapisany, nie musisz pobierać szablonu.  Wybierz pozycję **Przeglądaj**, Znajdź zapisany plik, a następnie wybierz pozycję **Otwórz**.
   0. Wybierz przycisk **OK**.


    Po pomyślnym przekazaniu zostanie wyświetlona lista subskrybentów i komunikat z potwierdzeniem.
   > [!div class="mx-imgBorder"]
   > ![Komunikat z potwierdzeniem, jeśli przekazywanie wielu subskrybentów powiedzie się](_img/assign-license-bulk/bulk-add-upload-success.png "Gdy przekazywanie zakończy się pomyślnie, zostanie wyświetlony komunikat z potwierdzeniem.")

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>Przypisywanie subskrypcji przy użyciu grup Azure Active Directory 
Korzystanie z tej funkcji ułatwia pozostawanie na swoich przypisaniach subskrypcji. Możesz dodać Azure Active Directory grupy zabezpieczeń w portalu administratora subskrypcji, co zapewni, że wszyscy użytkownicy w grupie mają przypisaną subskrypcję. Aby ułatwić, gdy użytkownicy opuszczają Twoją organizację i zostaną usunięci z Azure Active Directory, ich dostęp do subskrypcji zostanie również usunięty. 


> [!IMPORTANT]
>
> Następujące ograniczenia dotyczą korzystania z grup usługi Azure AD na potrzeby dodawania subskrybentów:
> - Administrator musi być członkiem dzierżawy usługi AAD podczas pierwszego dodawania grupy do portalu administracyjnego.  Po dodaniu grupy zmiany członkostwa w grupach nie wymagają zaangażowania administratora. 
> - Grupy muszą zawierać co najmniej jednego członka.  Puste grupy nie są obsługiwane.
> - Grupy muszą mieć mniej niż 1 000 użytkowników. 
> - Wszyscy użytkownicy muszą znajdować się na najwyższym poziomie grupy.  Zagnieżdżone grupy nie są obsługiwane.
> - Obsługiwane są tylko zaufane umowy. (Ufają tylko umowom, które mogą "nadmiarowe subskrypcje").
> - Wszyscy członkowie grupy muszą mieć adres e-mail skojarzony z kontem usługi Azure AD.
> - Oddzielne adresy e-mail dla powiadomień nie są obsługiwane w przypadku subskrypcji dodanych za pomocą grup usługi Azure AD.  

Obejrzyj ten film wideo lub przeczytaj, aby dowiedzieć się więcej na temat dodawania subskrybentów za pomocą funkcji grupy Azure Active Directory. 
<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4rvvW]

1. Zaloguj się do portalu administracyjnego subskrypcji programu Visual Studio pod adresem [https://manage.visualstudio.com](https://manage.visualstudio.com) .

2. Aby jednocześnie dodać wielu subskrybentów, przejdź do karty **Zarządzanie subskrybentami** .

3. Wybierz kartę **Dodaj** , a następnie na liście rozwijanej wybierz pozycję **Grupa Azure Active Directory** .  

   > [!div class="mx-imgBorder"]
   > ![Wybierz pozycję Dodaj zbiorczo za pomocą usługi Azure AD](_img/assign-license-bulk/bulk-add-aad.png "Wybierz pozycję Dodaj zbiorczo przy użyciu funkcji usługi Azure AD, aby ściągnąć subskrybentów z grupy Azure Active Directory.")

4. Rozpocznij wprowadzanie nazwy grupy usługi Azure AD, która ma zostać dodana do pola formularza. Spowoduje to przeszukanie dostępnych grup usługi Azure AD w organizacji. 

5. Po wybraniu grupy pole zostanie automatycznie wypełnione nazwą grupy. W tej grupie będzie dostępna opcja wyświetlania użytkowników przed ich dodaniem. Następnie można wybrać poziom subskrypcji, prawa do pobierania i preferencje komunikacji dla grupy. Jeśli chcesz, możesz dodać szczegóły do pola odwołanie. 

   > [!div class="mx-imgBorder"]
   > ![Wybierz grupę usługi Azure AD](_img/assign-license-bulk/bulk-add-aad-details.png "Wybierz nazwę grupy usługi Azure AD, aby dodać subskrybentów z tej grupy.")

6. Wybierz pozycję **Dodaj** , a następnie **Potwierdź**. 

7. Aby wyświetlić dodaną grupę, przewiń w dół listy użytkowników.  

8. Wybierz pozycję **Wyświetl Subskrybenci** , aby wyświetlić członków grupy. Możesz wyświetlić szczegółowe informacje o subskrybencie w grupie, ale nie możesz wprowadzać żadnych zmian do subskrybentów ani przypisanych do nich subskrypcji.    

> [!NOTE]
> Jeśli masz już przypisane subskrypcje do użytkowników, którzy zostali następnie dodani jako części grupy usługi Azure AD, zostaną one dodane jako część grupy i nie będą już wyświetlane indywidualnie. Jednak jeśli indywidualna subskrypcja dotyczy innego poziomu subskrypcji, będą oni mieć dwie subskrypcje.  Przykład: Jeśli użytkownik ma indywidualną subskrypcję Visual Studio Professional i jest członkiem grupy, do której przypiszesz subskrypcje Visual Studio Enterprise, będą one mieć oba te elementy.  
>
> W przypadku usunięcia abonenta z grupy Azure Active Directory, do której przypisano subskrypcje, może upłynąć nawet 24 godziny, aby aktualizacja została odzwierciedlona w portalu administracyjnym. 


## <a name="frequently-asked-questions"></a>Często zadawane pytania
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>P: Czy można wybrać wiele poziomów subskrypcji, które mają być przypisane w ramach grupy usługi Azure AD? 
Odp.: nie — wszyscy użytkownicy w grupie otrzymują tę samą subskrypcję. 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>P: Czy można edytować szczegóły subskrybenta dodanych do grupy usługi Azure AD?  
Odp.: nie--aby zmodyfikować informacje dla poszczególnych subskrybentów, należy usunąć je z grupy zabezpieczeń usługi Azure AD i przypisać im pojedynczą subskrypcję.  

### <a name="q-why-cant-i-see-the-option-to-use-azure-active-directory-groups-to-add-subscribers"></a>P: Dlaczego nie widzę opcji używania grup Azure Active Directory do dodawania subskrybentów?
Odp.: Ta funkcja jest obecnie dostępna tylko dla organizacji z zaufanymi umowami.  Wybierz przycisk **szczegóły** , aby wyświetlić informacje o umowie.

   > [!div class="mx-imgBorder"]
   > ![Kliknij przycisk Szczegóły](_img/assign-license-bulk/bulk-add-agreement.png "Kliknij przycisk Szczegóły, aby zobaczyć, jakiego rodzaju umowę")

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-added-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>P: dodano kogoś do grupy zabezpieczeń usługi Azure AD, ale nie są one widoczne w portalu administracyjnym subskrypcji i nie mają subskrypcji. Czemu nie?  
Odp.: w zależności od tego, jak Twoja organizacja skonfigurował usługę Azure AD, można zobaczyć opóźnienia nawet przez 24 godziny przed dodaniem użytkownika. Jeśli jest dłuższa niż 24 godziny, odwiedź [wsparcie administracyjne i subskrypcje programu Visual Studio](https://my.visualstudio.com/gethelp).  

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](/visualstudio/)
- [Azure DevOps documentation (Dokumentacja usługi Azure DevOps)](/azure/devops/)
- [Dokumentacja platformy Azure](/azure/)
- [Dokumentacja Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
- Masz tylko jednego lub dwóch subskrybentów do dodania?  Wyewidencjonowywanie [dodawania pojedynczych użytkowników](assign-license.md)
- Potrzebujesz pomocy? Skontaktuj się z [pomocą techniczną](https://aka.ms/vsadminhelp).