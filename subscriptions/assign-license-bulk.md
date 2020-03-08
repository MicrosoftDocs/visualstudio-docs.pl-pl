---
title: Przypisywanie licencji do grup użytkowników dla subskrypcji programu Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/02/2020
ms.topic: conceptual
description: Dowiedz się, jak Administratorzy mogą przypisywać licencje do wielu subskrybentów za pomocą funkcji zbiorczego dodawania lub grup Microsoft Azure Active Directory
ms.openlocfilehash: c8ea294f0e4b2b4deae18e2f5644bf08fff0dfc2
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410406"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Przypisywanie subskrypcji wielu użytkownikom
Portal administrowania subskrypcjami pozwala dodawać użytkowników jeden w czasie lub w dużych grupach.  Aby dodać poszczególnych użytkowników, zobacz [Dodawanie pojedynczych użytkowników](assign-license.md).

Aby dodać dużych grup użytkowników, możesz użyć funkcji dodawania zbiorczego lub jeśli Twoja organizacja korzysta z usługi Microsoft Azure Active Directory (Azure AD), możesz użyć grup usługi Azure AD. W tym artykule opisano proces dla obu tych opcji. 

## <a name="use-bulk-add-to-assign-subscriptions"></a>Używanie dodatków zbiorczych do przypisywania subskrypcji
1. Zaloguj się do portalu administracyjnego subskrypcji programu Visual Studio w witrynie https://manage.visualstudio.com.

2. Aby jednocześnie dodać wielu subskrybentów, przejdź do karty **Zarządzanie subskrybentami** . Wybierz kartę **Dodaj** , a następnie na liście rozwijanej wybierz pozycję **Dodaj zbiorczo** .  

2. Dodawanie zbiorcze używa szablonu programu Microsoft Excel do przekazywania informacji o subskrybencie. W oknie dialogowym przekazywanie wielu subskrybentów kliknij pozycję **Pobierz** , aby pobrać szablon.
   > [!div class="mx-imgBorder"]
   > ![pobrać szablonu programu Excel, aby przekazać wielu subskrybentów](media/download-template-upload-subscribers.png)
   >
   > [!NOTE]
   > Zawsze Pobieraj najnowszą wersję tego szablonu. Jeśli używasz starszej wersji, przekazywanie zbiorcze może zakończyć się niepowodzeniem.

3. W arkuszu kalkulacyjnym programu Excel Wypełnij pola informacjami dla osób, do których chcesz przypisać subskrypcje. (*Odwołanie* jest polem opcjonalnym). Zapisz plik lokalnie po zakończeniu.

   Aby zapewnić bezproblemowe przekazywanie, należy przestrzegać następujących najlepszych rozwiązań:

    - Upewnij się, że żadne z pól formularza nie zawiera przecinków.
    - Usuń odstępy przed i po polach formularza.
    - Upewnij się, że nazwy użytkowników nie zawierają dodatkowych spacji między imioną lub nazwiskiem dwóch części (na przykład jeśli osoba ma dwuczęściową nazwę, taką jak "Maggie", należy ją wpisać jako "MaggieMay", ponieważ system nie przycinania dodatkowego miejsca).
    - Upewnij się, że wszystkie wymagane pola są wypełnione. 
    - Sprawdź kolumnę **komunikat o błędzie** .  Jeśli występują błędy, usuń je przed podjęciem próby przekazania pliku. 

4. Wróć do portalu administracyjnego subskrypcji programu Visual Studio. W oknie dialogowym **przekazywanie wielu subskrybentów** kliknij przycisk **Przeglądaj**.
   > [!div class="mx-imgBorder"]
   > ![przejść do zapisanego szablonu, aby przekazać wielu subskrybentów](media/bulk-add-browse-saved-template.png)

5. Przejdź do zapisanego pliku programu Excel, a następnie kliknij przycisk **OK**.
   > [!div class="mx-imgBorder"]
   > ![przekazać szablon programu Excel w celu przekazania wielu subskrybentów](media/bulk-upload-subscribers.png)

    Zostanie wyświetlone okno dialogowe postęp przekazywania.

    Jeśli szablon zawiera błędy, przekazywanie zakończy się niepowodzeniem, a błędy zostaną wyświetlone, aby można było poprawić szablon i ponowić próbę przekazania zbiorczego.
   > [!div class="mx-imgBorder"]
   > ![komunikat o błędzie, jeśli przekazywanie wielu subskrybentów zakończy się niepowodzeniem](media/bulk-add-template-failed.png)

    Po pomyślnym przekazaniu zostanie wyświetlona lista subskrybentów i komunikat z potwierdzeniem.
   > [!div class="mx-imgBorder"]
   > ![komunikat z potwierdzeniem, jeśli przekazywanie wielu subskrybentów powiedzie się](media/bulk-add-template-success.png)

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>Przypisywanie subskrypcji przy użyciu grup Azure Active Directory 
Korzystanie z tej funkcji ułatwia pozostawanie na swoich przypisaniach subskrypcji. Możesz dodać Azure Active Directory grupy zabezpieczeń w portalu administratora subskrypcji, co zapewni, że wszyscy użytkownicy w grupie mają przypisaną subskrypcję. Aby ułatwić, gdy użytkownicy opuszczają Twoją organizację i zostaną usunięci z Azure Active Directory, ich dostęp do subskrypcji zostanie również usunięty. 

> [!IMPORTANT]
> Następujące ograniczenia dotyczą korzystania z grup usługi Azure AD na potrzeby dodawania subskrybentów:
> - Grupy muszą zawierać co najmniej jednego członka.  Puste grupy nie są obsługiwane.
> - Grupy muszą mieć mniej niż 1 000 użytkowników 
> - Wszyscy użytkownicy muszą znajdować się na najwyższym poziomie grupy.  Grupy zagnieżdżone nie są obsługiwane
> - Obsługiwane są tylko zaufane umowy
> - Wszyscy członkowie grupy muszą mieć adres e-mail skojarzony z kontem usługi Azure AD


1. Zaloguj się do portalu administracyjnego subskrypcji programu Visual Studio w witrynie [https://manage.visualstudio.com](https://manage.visualstudio.com).

2. Aby jednocześnie dodać wielu subskrybentów, przejdź do karty **Zarządzanie subskrybentami** .

3. Wybierz kartę **Dodaj** , a następnie na liście rozwijanej wybierz pozycję **Grupa Azure Active Directory** .  

   > [!div class="mx-imgBorder"]
   > ![wybierz pozycję Dodaj zbiorczo za pomocą usługi Azure AD](_img/assign-license-bulk/bulk-add-aad.png)


4. Rozpocznij wprowadzanie nazwy grupy usługi Azure AD, która ma zostać dodana do pola formularza. Spowoduje to przeszukanie dostępnych grup usługi Azure AD w organizacji. 

5. Po wybraniu grupy pole zostanie automatycznie wypełnione nazwą grupy. W tej grupie będzie dostępna opcja wyświetlania użytkowników przed ich dodaniem. Następnie można wybrać poziom subskrypcji, prawa do pobierania i preferencje komunikacji dla grupy. Jeśli chcesz, możesz dodać szczegóły do pola odwołanie. 

   > [!div class="mx-imgBorder"]
   > ![wybierz pozycję Dodaj zbiorczo za pomocą usługi Azure AD](_img/assign-license-bulk/bulk-add-aad-details.png)

6. Kliknij przycisk **Dodaj** , a następnie **Potwierdź**. 

7. Aby wyświetlić dodaną grupę, przewiń w dół listy użytkowników.  

8. Wybierz pozycję **Wyświetl Subskrybenci** , aby wyświetlić członków grupy. Możesz wyświetlić szczegółowe informacje o subskrybencie w grupie, ale nie możesz wprowadzać żadnych zmian do subskrybentów ani przypisanych do nich subskrypcji.    

## <a name="frequently-asked-questions"></a>Często zadawane pytania
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>P: Czy można wybrać wiele poziomów subskrypcji, które mają być przypisane w ramach grupy usługi Azure AD? 
Odp.: nie — wszyscy użytkownicy w grupie otrzymują tę samą subskrypcję. 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>P: Czy można edytować szczegóły subskrybenta dodanych do grupy usługi Azure AD?  
Odp.: nie--aby zmodyfikować informacje dla poszczególnych subskrybentów, należy usunąć je z grupy zabezpieczeń usługi Azure AD i przypisać im pojedynczą subskrypcję.  

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-added-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>P: dodano kogoś do grupy zabezpieczeń usługi Azure AD, ale nie są one widoczne w portalu administracyjnym subskrypcji i nie mają subskrypcji. Dlaczego?  
Odp.: w zależności od tego, jak Twoja organizacja skonfigurował usługę Azure AD, można zobaczyć opóźnienia nawet przez 24 godziny przed dodaniem użytkownika. Jeśli jest dłuższa niż 24 godziny, [skontaktuj się z pomocą techniczną](https://visualstudio.microsoft.com/support/support-overview-vs).  


## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
- Masz tylko jednego lub dwóch subskrybentów do dodania?  Wyewidencjonowywanie [dodawania pojedynczych użytkowników](assign-license.md)
- Potrzebujesz pomocy? Skontaktuj się z [pomocą techniczną programu Visual Studio Administration i subscriptions](https://visualstudio.microsoft.com/support/support-overview-vs).

