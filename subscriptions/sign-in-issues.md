---
title: Problemy z logowaniem do subskrypcji programu Visual Studio | Dokumentacja firmy Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.date: 11/07/2018
ms.topic: conceptual
description: Dowiedz się więcej o problemach, które mogą wystąpić podczas logowania się do subskrypcji programu Visual Studio
ms.openlocfilehash: c0687d08503389826b4c23b6add2a56f68e6a483
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67784948"
---
# <a name="issues-signing-in-to-visual-studio-subscriptions"></a>Problemy z logowaniem do subskrypcji programu Visual Studio
Aby korzystać z subskrypcji programu Visual Studio, należy najpierw zalogować.  W zależności od Twojej subskrypcji może być skonfigurowaniu go za pomocą konta Microsoft (MSA) lub tożsamości usługi Azure Active Directory (AAD).  W tym artykule omówiono niektóre problemy, które można napotkać podczas logowania się do Twojej subskrypcji.

## <a name="microsoft-accounts-msa-cannot-be-created-using-workschool-email-addresses"></a>Nie można utworzyć konta Microsoft (MSA) przy użyciu adresów e-mail służbowe

Możliwość tworzenia nowych osobistego konta Microsoft (MSA) przy użyciu adresu e-mail służbowe nie jest już dozwolona po skonfigurowaniu domeny poczty e-mail w usłudze Azure AD. Co to oznacza? Jeśli Twoja organizacja korzysta z usługi Office 365 lub innych usług biznesowych firmy Microsoft, które zależą od usługi Azure AD i dodaniu nazwy domeny do dzierżawy usługi Azure AD, użytkownicy nie będą już mogli tworzyć nowe osobiste konto Microsoft przy użyciu adresu e-mail w domenie.

### <a name="why-was-this-change-made"></a>Dlaczego ta zmiana została wprowadzona?

Osobiste Account Microsoft z adresem pracy jako nazwy użytkownika jest obarczone zagrożeniami problemy użytkowników końcowych i podobne działom IT. Na przykład:
- Użytkownicy mogą traktować czy swoje osobiste konto Microsoft jest zgodny z firmy i że są one w zakresie zgodności podczas zapisywania dokumentów firmy do usługi OneDrive
- Użytkownicy, którzy są ogólnie opuścić organizację utracić dostęp do służbowych adresów e-mail. Gdy tak robią, nie może być możliwe tworzenie kopii do swojego osobistego konta Microsoft, jeśli zapomną swoich haseł. Z drugiej strony jest, że dział IT może zresetować swoje hasło i uzyskać do osobistego konta byłych pracowników.
- Działy IT mają fałszywe poczucie własności konta i zabezpieczeń. Jednak użytkownicy potrzebują tylko kod do służbowej poczty e-mail adres raz i w dowolnym momencie w przyszłości zmienić nazwę swojego konta w obie strony.

Ta sytuacja jest szczególnie kłopotliwe dla użytkowników, którzy mają dwa konta z tego samego adresu e-mail (w usłudze Azure AD i jednego konta Microsoft).

### <a name="what-does-this-experience-look-like"></a>Jak wygląda to środowisko?

Jeśli spróbujesz zarejestrować się w aplikacji klienta Microsoft z pracą lub szkolny adres e-mail, zobaczysz poniższy komunikat.

   > [!div class="mx-imgBorder"]
   > ![Nie można utworzyć konto przy użyciu służbowego adresu e-mail](_img/sign-in-issues/cannot-use-work-email.png)

Jednak Jeśli spróbujesz zarejestrować się w aplikacji firmy Microsoft, który obsługuje konta osobiste i służbowe, powinien zostać wyświetlony ten komunikat:

   > [!div class="mx-imgBorder"]
   > ![Konto służbowe obsługiwane](_img/sign-in-issues/existing-account.png)

### <a name="are-existing-accounts-affected"></a>Istniejące konta dotyczy problem?
Blok tworzenia konta, opisane w tym miejscu zapobiega tylko tworzenie nowych kont. Go nie ma wpływu na użytkowników, którzy już Account firmy Microsoft z adresem e-mail służbowe. Jeśli jesteś już w tej sytuacji, wprowadziliśmy, ułatwiając Zmień nazwę osobistego konta Microsoft. To [artykuł pomocy technicznej](http://windows.microsoft.com/en-US/Windows/rename-personal-microsoft-account) proste wskazówki krok po kroku. Zmiana nazwy Twojego osobistego konta Microsoft oznacza zmianę nazwy użytkownika i nie ma wpływu na służbowego adresu e-mail lub sposobu logowania się do usług biznesowych, takich jak Office 365. On również nie ma wpływu na Twoje osobiste rzeczy — po prostu zmienia sposób, zaloguj się do niego. Możesz używać innego adresu e-mail (osobistych), Utwórz nowe @outlook.com adres e-mail od firmy Microsoft lub numer telefonu służy jako nowa nazwa użytkownika.

> [!NOTE]
> Jeśli dział IT pojawi się pytanie do utworzenia osobiste konto Microsoft z służbowe poczty e-mail, na przykład w celu uzyskania dostępu firmy Microsoft usług biznesowych korzystający z pomocy technicznej, takie jak, a następnie komunikować się z zespołem administracyjnym przed zmianą nazwy konta.

## <a name="deleting-a-sign-in-address-may-prevent-access-to-a-subscription"></a>Usuwanie adres logowania może uniemożliwić dostęp do subskrypcji

Jeśli usuniesz jedną lub więcej tożsamości (zarządzanych kont usług lub usługi AAD) skojarzonych z subskrypcją, Twoje informacje subskrybenta, w tym nazwę użytkownika i Identyfikatora logowania może być renderowana anonimowe, co spowoduje utratę dostępu do Twojej subskrypcji.

Aby uniknąć wpływu na dostęp do Twojej subskrypcji, użyj jednej z poniższych metod.
- Wdróż system zarządzania obsługą jednej tożsamości — konta Microsoft lub usługi AAD — ale nie oba jednocześnie.
- Skojarz tożsamości usługi AAD i zarządzanych kont usług, za pomocą dzierżawy.

## <a name="next-steps"></a>Następne kroki
- Dowiedz się, jak [Połącz konto MSA, a usługi AAD konta](/azure/active-directory/b2b/add-users-administrator) w ramach usługi AAD.
- Dowiedz się więcej o [anonimowości](anonymization.md).
