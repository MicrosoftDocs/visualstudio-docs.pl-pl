---
title: Problemy z logowaniem się do subskrypcji programu Visual Studio | Dokumenty firmy Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/11/2020
ms.topic: conceptual
description: Dowiedz się więcej o problemach, które mogą pojawić się podczas logowania się do subskrypcji programu Visual Studio
ms.openlocfilehash: 8175a1d8d2c79aecad25952eebdf734e0a9d29d2
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "79509021"
---
# <a name="issues-signing-in-to-visual-studio-subscriptions"></a>Problemy z logowaniem się do subskrypcji programu Visual Studio
Aby korzystać z subskrypcji programu Visual Studio, należy najpierw się zalogować.  W zależności od subskrypcji być może skonfigurowano ją przy określaniu tożsamości konta Microsoft (MSA) lub usługi Azure Active Directory (AAD).  W tym artykule omówiono niektóre problemy, które mogą wystąpić podczas logowania się do subskrypcji.

## <a name="microsoft-accounts-msa-cannot-be-created-using-workschool-email-addresses"></a>Nie można utworzyć kont Microsoft (MSA) przy użyciu służbowych/szkolnych adresów e-mail
Możliwość tworzenia nowego osobistego konta Microsoft (MSA) przy użyciu służbowego adresu e-mail nie jest już dozwolona, gdy domena poczty e-mail jest skonfigurowana w usłudze Azure AD. Co to oznacza? Jeśli Twoja organizacja korzysta z usługi Office 365 lub innych usług biznesowych firmy Microsoft, które opierają się na usłudze Azure AD, a nazwa domeny została dodana do dzierżawy usługi Azure AD, użytkownicy nie będą już mogli tworzyć nowego osobistego konta Microsoft przy użyciu adresu e-mail w domenie.

### <a name="why-was-this-change-made"></a>Dlaczego ta zmiana została wniesiena?
Posiadanie osobistego konta Microsoft z adresem służbowym jako nazwą użytkownika jest obarczone problemami zarówno dla użytkowników końcowych, jak i działów IT. Przykład:
- Użytkownicy mogą myśleć, że ich osobiste konto Microsoft jest zgodne z zasadami biznesowymi i że są one zgodne podczas zapisywania dokumentu biznesowego w usłudze OneDrive
- Użytkownicy, którzy opuszczają organizację, zazwyczaj tracą dostęp do służbowego adresu e-mail. Gdy to zrobią, mogą nie być w stanie wrócić do osobistego konta Microsoft, jeśli zapomną hasła. Drugą stroną jest to, że ich dział IT może zresetować swoje hasło i dostać się na osobiste konto byłych pracowników.
- Działy IT mają fałszywe poczucie własności konta i bezpieczeństwa. Ale użytkownicy muszą tylko raz w obierzeć kod na służbowy adres e-mail i zmienić nazwę swojego konta w dowolnym momencie w przyszłości.

Sytuacja jest szczególnie myląca dla użytkowników, którzy mają dwa konta z tym samym adresem e-mail (jeden w usłudze Azure AD & jedno konto Microsoft).

### <a name="what-does-this-experience-look-like"></a>Jak wygląda to doświadczenie?
Jeśli spróbujesz zarejestrować się w aplikacji konsumenckiej firmy Microsoft z firmowym adresem e-mail, zobaczysz poniższy komunikat.

   > [!div class="mx-imgBorder"]
   > ![Nie można utworzyć konta z służbową pocztą e-mail](_img/sign-in-issues/cannot-use-work-email.png)

Jeśli jednak spróbujesz zarejestrować się w aplikacji firmy Microsoft obsługującej konta osobiste i służbowe, powinien zostać wyświetlony ten komunikat:

   > [!div class="mx-imgBorder"]
   > ![Obsługiwane konta służbowe/szkolne](_img/sign-in-issues/existing-account.png)

### <a name="are-existing-accounts-affected"></a>Czy dotyczy to istniejących kont?
Opisany tutaj blok rejestracji uniemożliwia tylko tworzenie nowych kont. Nie ma to wpływu na użytkowników, którzy mają już konto Microsoft z służbowym adresem e-mail. Jeśli jesteś już w tej sytuacji, ułatwiliśmy zmianę nazwy osobistego konta Microsoft. Ten [artykuł pomocy technicznej](https://windows.microsoft.com/en-US/Windows/rename-personal-microsoft-account) zawiera proste wskazówki krok po kroku. Zmiana nazwy osobistego konta Microsoft oznacza zmianę nazwy użytkownika i nie ma wpływu na służbową pocztę e-mail ani sposób logowania się do usług biznesowych, takich jak Office 365. Nie ma to również wpływu na twoje rzeczy osobiste — po prostu zmienia sposób, w jaki się do niego logujesz. Możesz użyć innego (osobistego) adresu e-mail, uzyskać nowy @outlook.com adres e-mail od firmy Microsoft lub użyć numeru telefonu jako nowej nazwy użytkownika.

> [!NOTE]
> Jeśli dział IT poprosił cię o utworzenie osobistego konta Microsoft za pomocą służbowej/szkolnej poczty e-mail, na przykład w celu uzyskania dostępu do usług biznesowych firmy Microsoft, takich jak Obsługa klienta Premier, skontaktuj się z zespołem administracyjnym przed zmianą nazwy konta.

## <a name="deleting-a-sign-in-address-may-prevent-access-to-a-subscription"></a>Usunięcie adresu logowania może uniemożliwić dostęp do subskrypcji
Jeśli usuniesz jedną lub więcej tożsamości (MSA lub AAD) skojarzonych z subskrypcją, informacje o subskrybentach, w tym nazwa użytkownika i identyfikator logowania, mogą być anonimowe, co spowoduje utratę dostępu do subskrypcji.

Aby uniknąć wpływu na dostęp do subskrypcji, użyj jednej z tych technik.
- Wdrażanie jednego systemu zarządzania tożsamościami — MSA lub AAD — ale nie obu.
- Skojarz tożsamości usługi AAD i MSA za pośrednictwem dzierżawy.

## <a name="signing-in-may-fail-when-using-aliases"></a>Logowanie może zakończyć się niepowodzeniem podczas używania aliasów
W zależności od typu konta używanego do logowania, dostępne subskrypcje [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)mogą nie być poprawnie wyświetlane podczas logowania się do . Jedną z potencjalnych przyczyn jest użycie "aliasów" lub "przyjaznych nazw" zamiast tożsamości logowania, do której przypisana jest subskrypcja. Nazywa się to "aliasing".

### <a name="what-is-aliasing"></a>Co to jest aliasing?
Termin "aliasing" odnosi się do użytkowników mających różne tożsamości, aby zalogować się do systemu Windows (lub usługi Active Directory) i uzyskać dostęp do poczty e-mail.

Aliasing można napotkać, gdy firma ma usługę Microsoft Online JohnD@contoso.comService dla logowania katalogu, na przykład , ale John.Doe@contoso.comużytkownicy uzyskują dostęp do swoich kont e-mail przy użyciu aliasów lub przyjaznych nazw, takich jak . Dla wielu klientów, którzy zarządzają swoimi subskrypcjami za pośrednictwem Centrum usług licencjonowania zbiorowego (VLSC), może to spowodować niepowodzenie logowania, ponieważ podany adres e-mail (John.Doe@contoso.com) nie jest zgodny z adresem katalogu (JohnD@contoso.com) wymaganym do pomyślnego uwierzytelnienia za pomocą opcji "Konto służbowe".

### <a name="what-options-do-i-have"></a>Jakie mam opcje?
Z punktu widzenia subskrybenta ważne jest, aby najpierw współpracować z administratorem, aby zrozumieć konfigurację tożsamości firmy. W razie potrzeby administrator może być konieczne zaktualizowanie ustawień konta w portalu administracyjnym lub utworzenie konta Microsoft (MSA) przy użyciu firmowego adresu e-mail. Przed podjęciem kroków w celu utworzenia msa, porozmawiać z administratorem dotyczące wszelkich zasad lub problemów z podjęciem tej akcji. 

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja usługi Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
- Dowiedz się, jak [połączyć konta MSA i AAD](/azure/active-directory/b2b/add-users-administrator) w ramach usługi AAD.
- Dowiedz się więcej o [anonimiznie](anonymization.md).
