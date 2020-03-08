---
title: Logowanie się do subskrypcji programu Visual Studio może zakończyć się niepowodzeniem podczas korzystania z aliasów | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/02/2020
ms.topic: conceptual
description: Logowanie może zakończyć się niepowodzeniem w przypadku używania aliasów lub przyjaznych nazw
ms.openlocfilehash: 53b277296e6923bb78717bb76a0c20d2861c29ce
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865391"
---
# <a name="signing-into-visual-studio-subscriptions-may-fail-when-using-aliases"></a>Logowanie się do subskrypcji programu Visual Studio może zakończyć się niepowodzeniem podczas korzystania z aliasów
W zależności od typu konta użytego do zalogowania się dostępne subskrypcje mogą nie być poprawnie wyświetlane podczas logowania się do [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Jedną z potencjalnych przyczyn jest użycie "aliasów" lub "przyjaznych nazw" zamiast tożsamości logowania, do której przypisano subskrypcję. Jest to nazywane "aliasem".

## <a name="what-is-aliasing"></a>Co to jest aliasowanie?
Termin "aliasowanie" odnosi się do użytkowników, którzy mają różne tożsamości do logowania się do systemu Windows (lub Active Directory) oraz do uzyskiwania dostępu do poczty e-mail.

Aliasowanie można napotkać, gdy firma ma usługę online firmy Microsoft dotyczącą logowania do katalogu, na przykład "JohnD@contoso.com", ale użytkownicy uzyskują dostęp do swoich kont e-mail przy użyciu aliasów lub przyjaznych nazw, takich jak "John.Doe@contoso.com". W przypadku wielu klientów, którzy zarządzają swoimi subskrypcjami za pośrednictwem usługi licencjonowania zbiorowego (VLSC), może to spowodować nieudane działanie logowania, ponieważ podany adres e-mail ("John.Doe@contoso.com") nie jest zgodny z adresem katalogu ("JohnD@contoso.com"), który jest wymagany do pomyślnego uwierzytelnienia za pośrednictwem opcji "konto służbowe".  Upewnij się, że użytkownicy korzystają z adresu E-mail "Logowanie", jak to zostało wymienione w portalu administracyjnym w https://manage.visualstudio.com, aby uzyskać dostęp do subskrypcji. 

## <a name="what-are-the-potential-issues"></a>Jakie są potencjalne problemy?

W zależności od typu konta subskrybenta mogą wystąpić jeden z dwóch problemów. 

### <a name="work-or-school-account-upn-mismatch-issue"></a>Problem niezgodności nazwy UPN konta służbowego lub szkolnego 
Można napotkać niezgodność nazw UPN, gdy firma ma Active Directory skonfigurowany, gdzie UserPrincipalName (UPN) nie jest taki sam jak podstawowy adres SMTP. 

#### <a name="how-to-detect-if-your-sign-in-address-is-impacted-by-a-upn-mismatch"></a>Jak wykryć, czy na adres logowania ma wpływ niezgodność nazw UPN 

1. Zaloguj się do https://my.visualstudio.com/subscriptions przy użyciu adresu logowania wymienionego w wiadomości e-mail dotyczącej przypisania subskrypcji.

2. Sprawdź, czy adres e-mail logowania wyświetlany w prawym górnym rogu strony jest zgodny z adresem użytym do zalogowania.  Jeśli tak nie jest, nazwa UPN jest niezgodna i nie będzie można wyświetlić subskrypcji. 

> [!div class="mx-imgBorder"]
> ![adres e-mail logowania](_img//aliasing/sign-in-email.png)

#### <a name="how-to-fix-a-upn-mismatch"></a>Jak naprawić niezgodność nazw UPN

1. Dostęp do portalu zarządzania administracyjnego programu Visual Studio [https://manage.visualstudio.com](https://manage.visualstudio.com) 

2. Znajdź subskrybenta z niezgodnością nazwy UPN. (Funkcja [filtru](search-license.md) może ułatwić znalezienie subskrybenta).

3. Zmień adres poczty logowania na nazwę UPN subskrybenta 

0. Zapisz zmiany 

0. Poinformuj subskrybenta, aby wylogować się z portalu subskrybenta i uzyskać do niego dostęp przy użyciu nazwy UPN 

### <a name="personal-account-aliasing-issue"></a>Problem z aliasem konta osobistego

Jeśli adres e-mail używany do logowania się do portalu subskrypcji programu Visual Studio nie jest zgodny z adresem e-mail skojarzonym z subskrypcją, można także skorzystać z osobistych kont subskrypcji. 

#### <a name="how-to-detect-if-your-personal-subscription-account-is-impacted-by-an-aliasing-issue"></a>Jak wykryć, czy Twoje konto subskrypcji osobistej ma wpływ na problem z aliasem

1. Zaloguj się do [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions)

0. Sprawdź, czy adres e-mail logowania wyświetlany w prawym górnym rogu strony jest zgodny z adresem użytym do zalogowania.  Jeśli zalogowany adres e-mail nie jest taki sam jak adres e-mail używany do uzyskiwania dostępu do witryny sieci Web, występuje konflikt między kontem a aliasem.

#### <a name="how-to-fix-an-alias-issue"></a>Jak rozwiązać problem związany z aliasem

Platforma Visual Studio ustala priorytet aliasu podstawowego, aby wyświetlić szczegóły subskrypcji. 

1. Przejdź do obszaru **Zarządzanie sposobem logowania do firmy Microsoft**. Jeśli zostanie wyświetlony monit, zaloguj się do konto Microsoft. 

2. W obszarze Aliasy kont wybierz pozycję **Utwórz podstawową** obok adresu e-mail używanego do przypisywania subskrypcji. 

> [!div class="mx-imgBorder"]
> ![ustawić podstawowego adresu e-mail](_img//aliasing/account-aliases.png)

3. Wyloguj się z portalu subskrypcji programu Visual Studio (https://my.visualstudio.com) 

4. Zaloguj się ponownie przy użyciu konta używanego do przypisania subskrypcji, która powinna zostać teraz skonfigurowana jako alias podstawowy. 

## <a name="preventing-aliasing-issues"></a>Zapobieganie problemom z aliasami

Jako administrator dostępne są dwie opcje zapewnienia pomyślnego logowania się dla subskrybentów [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs).
- Pierwsza opcja (zalecane) polega na użyciu konta katalogu jako logowania dla portalu subskrypcji programu Visual Studio w https://my.visualstudio.com.  
- Druga opcja (mniej bezpieczna) polega na tym, że Subskrybenci mogą się zalogować przy użyciu innego adresu e-mail niż adres e-mail swojego katalogu.

Obie te opcje są konfigurowane w portalu administracyjnym, wykonując następujące czynności:  
1. Zaloguj się do [https://manage.visualstudio.com](https://manage.visualstudio.com) 

0. Jeśli zmieniasz pojedynczego użytkownika, wybierz tego użytkownika z tabeli i kliknij prawym przyciskiem myszy, aby edytować. Spowoduje to otwarcie panelu, w którym można zmodyfikować adres e-mail logowania. Wprowadź wymagane aktualizacje w polu adres e-mail logowania. Kliknij przycisk Zapisz, aby zmiany zaczęły obowiązywać.  

0. Jeśli musisz wprowadzić te zmiany do dużej liczby użytkowników, możesz skorzystać z funkcji Edytuj zbiorczo. Aby uzyskać więcej informacji, przeczytaj artykuł [Edycja wielu subskrybentów korzystających z edycji zbiorczej](https://docs.microsoft.com/visualstudio/subscriptions/edit-license#edit-multiple-subscribers-using-bulk-edit) .

> [!NOTE]
> W przypadku zmian indywidualnych i zbiorczych subskrybenci otrzymają wiadomość e-mail z instrukcjami, że ich adresy e-mail logowania zostały zmienione i będą musieli zalogować się przy użyciu zaktualizowanego adresu e-mail. Należy również pamiętać, że jeśli Subskrybenci wcześniej aktywowali korzyści pod innym adresem logowania, muszą nadal korzystać z innego adresu logowania, aby uzyskać do nich dostęp.  

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja Microsoft 365](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>Następne kroki
Dowiedz się więcej o zarządzaniu subskrypcjami programu Visual Studio.
- [Przypisywanie pojedynczych subskrypcji](assign-license.md)
- [Przypisywanie wielu subskrypcji](assign-license-bulk.md)
- [Edytowanie subskrypcji](edit-license.md)
- [Określanie maksymalnego użycia](maximum-usage.md)


