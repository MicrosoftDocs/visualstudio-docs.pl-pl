---
title: Logowanie się do subskrypcji programu Visual Studio może zakończyć się niepowodzeniem podczas korzystania z aliasów | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 02/14/2020
ms.topic: conceptual
description: Logowanie może zakończyć się niepowodzeniem w przypadku używania aliasów lub przyjaznych nazw
ms.openlocfilehash: dff48852e566522ad01ee07bd46cda72b8e1e249
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2020
ms.locfileid: "77276620"
---
# <a name="signing-in-to-visual-studio-subscriptions-may-fail-when-using-aliases"></a>Logowanie się do subskrypcji programu Visual Studio może zakończyć się niepowodzeniem podczas korzystania z aliasów
W zależności od typu konta użytego do zalogowania się dostępne subskrypcje mogą nie być poprawnie wyświetlane podczas logowania się do [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Jedną z potencjalnych przyczyn jest użycie "aliasów" lub "przyjaznych nazw" zamiast tożsamości logowania, do której przypisano subskrypcję. Jest to nazywane "aliasem".

## <a name="what-is-aliasing"></a>Co to jest aliasowanie?
Termin "aliasowanie" odnosi się do użytkowników, którzy mają różne tożsamości do logowania się do systemu Windows (lub Active Directory) oraz do uzyskiwania dostępu do poczty e-mail.

Aliasowanie można napotkać, gdy firma ma usługę online firmy Microsoft dotyczącą logowania do katalogu, na przykład "olivia@contoso.com", ale użytkownicy uzyskują dostęp do swoich kont e-mail przy użyciu aliasów lub przyjaznych nazw, takich jak "OliviaG@contoso.com". Upewnij się, że użytkownicy logują się przy użyciu adresu E-mail "Logowanie", jak to zostało wymienione w portalu administratora subskrypcji programu Visual Studio w https://manage.visualstudio.com, aby uzyskać dostęp do swoich subskrypcji

## <a name="as-an-administrator-what-options-do-i-have"></a>Jakie opcje są dostępne dla administratorów?

W zależności od typu konta subskrybenta Znajdź odpowiednie rozwiązanie poniżej:

### <a name="work-or-school-account-upn-mismatch-issue"></a>Problem niezgodności nazwy UPN konta służbowego lub szkolnego

Niezgodność głównej nazwy użytkownika (UPN) można napotkać, gdy Compnay ma aktywny Diretory skonfigurowany, gdzie nazwa UPN nie jest taka sama jak podstawowy adres SMTP. 

#### <a name="how-to-detect-if-a-users-sign-in-address-has-a-upn-mismatch"></a>Jak wykryć, czy adres logowania użytkownika ma niezgodność nazw UPN

Użytkownik powinien wykonać następujące czynności:

1. Zaloguj się do https://my.visualstudio.com przy użyciu adresu logowania wymienionego w wiadomości e-mail dotyczącej przypisania subskrypcji.  

    > [!NOTE]
    > Jeśli nie mają swoich wiadomości e-mail dotyczących przypisania subskrypcji, możesz ponownie wysłać ją do nich z poziomu portalu Adminstration.  

2. Kliknij kartę **subskrypcje** .
3. Sprawdź, czy adres e-mail wyświetlany w prawym górnym rogu wskazuje, że użytkownik jest zalogowany jako... " jest taka sama jak adres e-mail logowania w wiadomości e-mail dotyczącej przypisania subskrypcji.  Jeśli nie, nie będą oni mogli uzyskać dostępu do korzyści z subskrypcji. 

   > [!div class="mx-imgBorder"]
   > ](_img/aliasing/aliasing-subscriptions-page.png) strony subskrypcji ![

#### <a name="how-to-correct-the-upn-mismatch"></a>Jak poprawić niezgodność nazw UPN

1. Dostęp do portalu zarządzania administracyjnego programu Visual Studio w witrynie https://manage.visualstudio.com 

2. Zlokalizuj użytkownika z niezgodnością nazwy UPN.  Funkcja [Filter](search-license.md) może to ułatwić, jeśli masz wiele subskrypcji. 

3. Zmień adres E-mail logowania na nazwę UPN użytkownika.

4. Zapisz zmiany 

5. Poproszenie użytkownika o wylogowanie się z portalu subskrybenta i ponowne zalogowanie się przy użyciu nazwy UPN.   

### <a name="personal-account-aliasing-issue"></a>Problem z aliasem konta osobistego

Problemy z aliasami mogą również mieć wpływ na konta osobiste. 

#### <a name="how-to-detect-if-a-personal-account-has-an-aliasing-issue"></a>Jak wykryć, czy konto osobiste ma problem z aliasem

1. Zaloguj się https://my.visualstudio.com.

2. Kliknij kartę **subskrypcje** i Sprawdź adres, z którym użytkownik jest zalogowany. 

3. Jeśli zalogowany adres e-mail nie jest taki sam jak adres e-mail używany do uzyskiwania dostępu do witryny sieci Web, występuje konflikt między kontem a aliasem. 

#### <a name="how-to-fix-a-personal-account-aliasing-issue"></a>Jak rozwiązać problem z aliasem konta osobistego

Platforma subskrypcji programu Visual Studio ustala priorytet aliasu podstawowego w celu wyświetlenia szczegółów subskrypcji.  Aby rozwiązać ten problem, należy utworzyć inny alias adresu e-mail dla aliasu podstawowego logowania. 

1. Przejdź do obszaru [Zarządzanie sposobem logowania do firmy Microsoft](https://go.microsoft.com/fwlink/p/?linkid=842796).
2. Jeśli zostanie wyświetlony monit, zaloguj się do konto Microsoft. 
3. W obszarze Aliasy kont wybierz pozycję **Utwórz podstawową** obok adresu e-mail używanego do przypisywania subskrypcji. 
4. W obszarze Aliasy kont wybierz pozycję Utwórz podstawową obok adresu e-mail używanego do przypisywania subskrypcji. 
5. Wyloguj się z portalu subskrybentów programu Visual Studio (https://my.visualstudio.com) 
6. Uzyskaj ponownie dostęp do portalu przy użyciu nowego aliasu podstawowego. 

### <a name="ensure-a-successful-experience-for-your-users"></a>Zapewnij pomyślne środowisko dla użytkowników

Jako administrator dostępne są dwie opcje zapewnienia pomyślnego logowania się dla subskrybentów https://my.visualstudio.com. 

- Pierwsza opcja (zalecana) polega na użyciu konta katalogu jako adresu logowania w https://manage.visualstudio.com.
- Druga opcja, która jest mniej bezpieczna, druga opcja (mniej bezpieczna), polega na tym, że Subskrybenci mogą się zalogować przy użyciu innego adresu e-mail niż adres e-mail katalogu.

Obie opcje są konfigurowane w portalu administracyjnym, wykonując następujące czynności:

1. Zaloguj się do https://manage.visualstudio.com 

2. Jeśli zmieniasz pojedynczego użytkownika, wybierz tego użytkownika z tabeli i kliknij prawym przyciskiem myszy, aby edytować. Spowoduje to otwarcie panelu, w którym można zmodyfikować adres e-mail logowania.  

3. Wprowadź wymagane aktualizacje w polu adres e-mail logowania. 

4. Kliknij przycisk Zapisz, aby zmiany zaczęły obowiązywać.  
Jeśli musisz wprowadzić te zmiany do dużej liczby użytkowników, możesz skorzystać z funkcji Edytuj zbiorczo. Aby uzyskać więcej informacji na temat tego procesu, przeczytaj sekcję **Edycja wielu subskrybentów korzystających z edycji zbiorczej** .  

## <a name="next-steps"></a>Następne kroki
Dowiedz się więcej o zarządzaniu subskrypcjami programu Visual Studio.
- [Przypisywanie pojedynczych subskrypcji](assign-license.md)
- [Przypisywanie wielu subskrypcji](assign-license-bulk.md)
- [Edytowanie subskrypcji](edit-license.md)
- [Usuwanie subskrypcji](delete-license.md)
- [Określanie maksymalnego użycia](maximum-usage.md)

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](/visualstudio/)
- [Dokumentacja usługi Azure DevOps](/azure/devops/)
- [Dokumentacja platformy Azure](/azure/)
- [Dokumentacja Microsoft 365](/microsoft-365/)
