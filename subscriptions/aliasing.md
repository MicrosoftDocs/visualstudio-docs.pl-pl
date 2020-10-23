---
title: Logowanie się do subskrypcji programu Visual Studio może zakończyć się niepowodzeniem podczas korzystania z aliasów | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 97bf7474-c6c2-49b3-b2c9-f1b2808eed1a
ms.date: 10/22/2020
ms.topic: conceptual
description: Logowanie może zakończyć się niepowodzeniem w przypadku używania aliasów lub przyjaznych nazw
ms.openlocfilehash: 4d9b3194cf7636106740e35b230cc02aaab7eded
ms.sourcegitcommit: bf5e2bba5acdcf05869b861211f8bb755081e5ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2020
ms.locfileid: "92467612"
---
# <a name="signing-into-visual-studio-subscriptions-may-fail-when-using-aliases"></a>Logowanie się do subskrypcji programu Visual Studio może zakończyć się niepowodzeniem podczas korzystania z aliasów
W zależności od typu konta użytego do zalogowania się dostępne subskrypcje mogą nie być poprawnie wyświetlane podczas logowania do programu [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) . Jedną z potencjalnych przyczyn jest użycie "aliasów" lub "przyjaznych nazw" zamiast tożsamości logowania, do której przypisano subskrypcję. Jest to nazywane "aliasem".

## <a name="what-is-aliasing"></a>Co to jest aliasowanie?
Termin "aliasowanie" odnosi się do użytkowników, którzy mają różne tożsamości do logowania się do systemu Windows (lub Active Directory) oraz do uzyskiwania dostępu do poczty e-mail.

Aliasowanie może wystąpić, gdy firma ma usługę online firmy Microsoft dotyczącą logowania do katalogu, na przykład " JohnD@contoso.com ", ale użytkownicy uzyskują dostęp do swoich kont e-mail przy użyciu aliasów lub przyjaznych nazw, takich jak " John.Doe@contoso.com ". Upewnij się, że użytkownicy korzystają z adresu E-mail logowania, jak to zostało pokazane w portalu administracyjnym w https://manage.visualstudio.com celu uzyskania dostępu do subskrypcji. 

## <a name="what-are-the-potential-issues"></a>Jakie są potencjalne problemy?

W zależności od typu konta subskrybenta mogą wystąpić jeden z dwóch problemów. 

### <a name="work-or-school-account-upn-mismatch-issue"></a>Problem niezgodności nazwy UPN konta służbowego lub szkolnego 
Można napotkać niezgodność nazw UPN, gdy firma ma Active Directory skonfigurowany, gdzie UserPrincipalName (UPN) nie jest taki sam jak podstawowy adres SMTP. 

#### <a name="how-to-detect-if-your-sign-in-address-is-impacted-by-a-upn-mismatch"></a>Jak wykryć, czy na adres logowania ma wpływ niezgodność nazw UPN 

1. Zaloguj się https://my.visualstudio.com/subscriptions przy użyciu adresu logowania wymienionego w wiadomości e-mail dotyczącej przypisania subskrypcji.

2. Kliknij swoją nazwę w prawym górnym rogu strony.  Spowoduje to otwarcie Twojego profilu.  Sprawdź, czy adres e-mail logowania podany w profilu jest zgodny z adresem użytym do zalogowania.  Jeśli tak nie jest, nazwa UPN jest niezgodna i nie będzie można wyświetlić subskrypcji. 

> [!div class="mx-imgBorder"]
> ![Adres e-mail logowania](_img//aliasing/sign-in-email.png "Upewnij się, że adres e-mail wyświetlany w Twoim profilu jest zgodny z identyfikatorem używanym do logowania.")

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
> ![Ustaw podstawowy adres e-mail](_img//aliasing/account-aliases.png "Użyj linku Utwórz podstawowy, aby wybrać podstawowy alias dla subskrypcji.")

3. Wyloguj się z portalu subskrypcji programu Visual Studio (https://my.visualstudio.com) 

4. Zaloguj się ponownie przy użyciu konta używanego do przypisania subskrypcji, która powinna zostać teraz skonfigurowana jako alias podstawowy. 

## <a name="preventing-aliasing-issues"></a>Zapobieganie problemom z aliasami

Jako administrator dostępne są dwie opcje, dzięki którym Subskrybenci mogą pomyślnie korzystać z funkcji logowania [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) .
- Pierwszą opcją (zalecane) jest użycie konta katalogu jako logowania w portalu subskrypcji programu Visual Studio pod adresem https://my.visualstudio.com .  
- Druga opcja (mniej bezpieczna) polega na tym, że Subskrybenci mogą się zalogować przy użyciu innego adresu e-mail niż adres e-mail swojego katalogu.

Obie te opcje są konfigurowane w portalu administracyjnym, wykonując następujące czynności:  
1. Zaloguj się [https://manage.visualstudio.com](https://manage.visualstudio.com) 

0. Jeśli zmieniasz pojedynczego użytkownika, wybierz tego użytkownika z tabeli i kliknij prawym przyciskiem myszy, aby edytować. Spowoduje to otwarcie panelu, w którym można zmodyfikować adres e-mail logowania. Wprowadź wymagane aktualizacje w polu adres e-mail logowania. Kliknij przycisk Zapisz, aby zmiany zaczęły obowiązywać.  

0. Jeśli musisz wprowadzić te zmiany do dużej liczby użytkowników, możesz skorzystać z funkcji Edytuj zbiorczo. Aby uzyskać więcej informacji, przeczytaj artykuł [Edycja wielu subskrybentów korzystających z edycji zbiorczej](./edit-license.md#edit-multiple-subscribers-using-bulk-edit) .

> [!NOTE]
> W przypadku zmian indywidualnych i zbiorczych subskrybenci otrzymają wiadomość e-mail z instrukcjami, że ich adresy e-mail logowania zostały zmienione i będą musieli zalogować się przy użyciu zaktualizowanego adresu e-mail. Należy również pamiętać, że jeśli Subskrybenci wcześniej aktywowali korzyści pod innym adresem logowania, muszą nadal korzystać z innego adresu logowania, aby uzyskać do nich dostęp.  

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](/visualstudio/)
- [Dokumentacja usługi Azure DevOps](/azure/devops/)
- [Dokumentacja platformy Azure](/azure/)
- [Dokumentacja Microsoft 365](/microsoft-365/)


## <a name="next-steps"></a>Następne kroki
Dowiedz się więcej o zarządzaniu subskrypcjami programu Visual Studio.
- [Przypisywanie pojedynczych subskrypcji](assign-license.md)
- [Przypisywanie wielu subskrypcji](assign-license-bulk.md)
- [Edytowanie subskrypcji](edit-license.md)
- [Określanie maksymalnego użycia](maximum-usage.md)