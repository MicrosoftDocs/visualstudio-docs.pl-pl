---
title: Logowanie się do subskrypcji programu Visual Studio może zakończyć się niepowodzeniem podczas korzystania z aliasów | Dokumenty firmy Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 97bf7474-c6c2-49b3-b2c9-f1b2808eed1a
ms.date: 03/02/2020
ms.topic: conceptual
description: Logowanie może zakończyć się niepowodzeniem, jeśli używane są aliasy lub przyjazne nazwy
ms.openlocfilehash: 0f5ed4fe67dbd863a7ba4c22f10946cbeb1c36b0
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "79509060"
---
# <a name="signing-into-visual-studio-subscriptions-may-fail-when-using-aliases"></a>Logowanie się do subskrypcji programu Visual Studio może zakończyć się niepowodzeniem podczas używania aliasów
W zależności od typu konta używanego do logowania, dostępne subskrypcje [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)mogą nie być poprawnie wyświetlane podczas logowania się do . Jedną z potencjalnych przyczyn jest użycie "aliasów" lub "przyjaznych nazw" zamiast tożsamości logowania, do której przypisana jest subskrypcja. Nazywa się to "aliasing".

## <a name="what-is-aliasing"></a>Co to jest aliasing?
Termin "aliasing" odnosi się do użytkowników mających różne tożsamości, aby zalogować się do systemu Windows (lub usługi Active Directory) i uzyskać dostęp do poczty e-mail.

Aliasing można napotkać, gdy firma ma usługę Microsoft Online ServiceJohnD@contoso.comdla logowania do katalogu, na przykład ' , aleJohn.Doe@contoso.comużytkownicy uzyskują dostęp do swoich kont e-mail przy użyciu aliasów lub przyjaznych nazw, takich jak ' " . Upewnij się, że użytkownicy używają "Adresu e-mail logowania" https://manage.visualstudio.com wymienionego w portalu administracyjnym, aby uzyskać dostęp do swoich subskrypcji. 

## <a name="what-are-the-potential-issues"></a>Jakie są potencjalne problemy?

W zależności od typu konta subskrybenta mogą napotkać jeden z dwóch problemów. 

### <a name="work-or-school-account-upn-mismatch-issue"></a>Problem niezgodności upn konta służbowego lub służbowego 
Niezgodność nazwy UPN można napotkać, gdy firma ma skonfigurowaną usługą Active Directory, w której nazwa UPN (UserPrincipalName) nie jest taka sama jak podstawowy adres SMTP. 

#### <a name="how-to-detect-if-your-sign-in-address-is-impacted-by-a-upn-mismatch"></a>Jak wykryć, czy niezgodność z usterką upn ma wpływ na adres logowania 

1. Zaloguj https://my.visualstudio.com/subscriptions się przy użyciu adresu logowania wymienionego w wiadomości e-mail przypisania subskrypcji.

2. Sprawdź, czy adres e-mail logowania podany w prawym górnym rogu strony jest zgodny z adresem użytym do zalogowania się.  Jeśli tak się nie stanie, twoja owana jest nieprawidłowa i nie będzie można wyświetlić subskrypcji. 

> [!div class="mx-imgBorder"]
> ![Zaloguj się na adres e-mail](_img//aliasing/sign-in-email.png)

#### <a name="how-to-fix-a-upn-mismatch"></a>Jak naprawić niezgodność z wiązką upn

1. Uzyskiwanie dostępu do portalu zarządzania administrowania programem Visual Studio[https://manage.visualstudio.com](https://manage.visualstudio.com) 

2. Znajdź subskrybenta, który ma problem z niezgodnością numeru UPN. (Funkcja [Filtruj](search-license.md) może ułatwić znalezienie subskrybenta).

3. Zmienianie adresu e-mail logowania na upn subskrybenta 

0. Zapisywanie zmian 

0. Poinformuj subskrybenta, aby wylogować się z portalu subskrybenta i uzyskać dostęp ponownie za pomocą umowy UPN 

### <a name="personal-account-aliasing-issue"></a>Problem z aliasingu konta osobistego

Osobiste konta subskrypcji mogą również wystąpić problemy, jeśli adres e-mail używany do logowania się do portalu subskrypcji programu Visual Studio nie pasuje do adresu e-mail skojarzonego z subskrypcją. 

#### <a name="how-to-detect-if-your-personal-subscription-account-is-impacted-by-an-aliasing-issue"></a>Jak wykryć, czy problem z aliasem ma wpływ na twoje osobiste konto subskrypcji

1. Zaloguj się do[https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions)

0. Sprawdź, czy adres e-mail logowania podany w prawym górnym rogu strony jest zgodny z adresem użytym do zalogowania się.  Jeśli zalogowany adres e-mail nie jest taki sam jak adres e-mail używany do uzyskiwania dostępu do witryny sieci Web, występuje konflikt między kontem a aliasem.

#### <a name="how-to-fix-an-alias-issue"></a>Jak rozwiązać problem z aliasem

Platforma Programu Visual Studio nadaje priorytet aliasowi podstawowemu, aby wyświetlić szczegóły subskrypcji. 

1. Przejdź do **witryny Zarządzanie loguj się do firmy Microsoft**. Zaloguj się do swojego konta Microsoft, jeśli zostanie wyświetlony monit. 

2. W obszarze Aliasy konta wybierz pozycję **Powierz pole wyboru Podstawowego** obok adresu e-mail użytego do przypisania subskrypcji. 

> [!div class="mx-imgBorder"]
> ![Ustawianie podstawowego adresu e-mail](_img//aliasing/account-aliases.png)

3. Wyloguj się z portalu subskrypcji programu Visual Studio (https://my.visualstudio.com) 

4. Zaloguj się ponownie przy użyciu konta używanego do przypisywania subskrypcji, która powinna być teraz skonfigurowana jako alias podstawowy. 

## <a name="preventing-aliasing-issues"></a>Zapobieganie problemom z aliasowaniem

Jako administrator istnieją dwie opcje, aby zapewnić subskrybentom pomyślne [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)logowanie na .
- Pierwszą opcją (zalecaną) jest wykorzystanie konta katalogu jako logowania do portalu https://my.visualstudio.comsubskrypcji programu Visual Studio pod adresem .  
- Drugą opcją (mniej bezpieczną) jest umożliwienie subskrybentom logowania się przy użyciu innego adresu e-mail niż ich adres e-mail katalogu.

Obie te opcje są skonfigurowane w portalu administracyjnym, wykonując następujące kroki:  
1. Zaloguj się[https://manage.visualstudio.com](https://manage.visualstudio.com) 

0. Jeśli zmieniasz jednego użytkownika, wybierz go w tabeli i kliknij prawym przyciskiem myszy, aby edytować. Spowoduje to otwarcie panelu, w którym można zmodyfikować adres e-mail logowania. Dokonaj niezbędnych aktualizacji w polu adresu e-mail logowania. Kliknij przycisk Zapisz, a zmiany zostaną wprowadzone.  

0. Jeśli chcesz wprowadzić te zmiany do dużej liczby użytkowników, można skorzystać z funkcji edycji zbiorczej. Przeczytaj [artykuł Edytuj wielu subskrybentów przy użyciu zbiorczej edycji](https://docs.microsoft.com/visualstudio/subscriptions/edit-license#edit-multiple-subscribers-using-bulk-edit) artykułu, aby uzyskać więcej informacji.

> [!NOTE]
> W przypadku zmian zarówno indywidualnych, jak i zbiorczych subskrybenci otrzymają wiadomość e-mail z instrukcjami, że ich adres e-mail logowania się zmienił i będą musieli zalogować się przy użyciu zaktualizowanego adresu e-mail. Należy również pamiętać, że jeśli subskrybent wcześniej aktywował korzyści pod innym adresem logowania, będzie musiał nadal używać innego adresu logowania, aby uzyskać do nich dostęp.  

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja usługi Microsoft 365](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>Następne kroki
Dowiedz się więcej o zarządzaniu subskrypcjami programu Visual Studio.
- [Przypisywanie poszczególnych subskrypcji](assign-license.md)
- [Przypisywanie wielu subskrypcji](assign-license-bulk.md)
- [Edytowanie subskrypcji](edit-license.md)
- [Określanie maksymalnego użycia](maximum-usage.md)


