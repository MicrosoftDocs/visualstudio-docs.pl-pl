---
title: Problemy z logowaniem do subskrypcji programu Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 176c7f11-b19d-49e9-a6dd-b2e5da5e8480
ms.date: 02/19/2021
ms.topic: conceptual
description: Informacje o problemach, które mogą wystąpić podczas logowania do subskrypcji programu Visual Studio
ms.openlocfilehash: 5735e0c4178e6866539fff2edac6155642a1ba73
ms.sourcegitcommit: f9ed9c4c6c166ef9826feb21dcb9c4d47ed14e1a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/10/2021
ms.locfileid: "102607200"
---
# <a name="issues-signing-in-to-visual-studio-subscriptions"></a>Problemy z logowaniem do subskrypcji programu Visual Studio
Aby korzystać z subskrypcji programu Visual Studio, musisz najpierw się zalogować.  W zależności od subskrypcji można skonfigurować ją za pomocą tożsamości usługi konto Microsoft (MSA) lub Azure Active Directory (AAD).  W tym artykule omówiono niektóre problemy, które można napotkać podczas logowania się do subskrypcji.

## <a name="microsoft-accounts-msa-cannot-be-created-using-workschool-email-addresses"></a>Konta Microsoft (MSA) nie mogą być tworzone przy użyciu służbowych adresów e-mail
Możliwość utworzenia nowego osobistego konta Microsoft (MSA) przy użyciu służbowego adresu e-mail nie jest już dozwolona, jeśli domena poczty e-mail jest skonfigurowana w usłudze Azure AD. Co to oznacza? Jeśli Twoja organizacja używa Microsoft 365 lub innych usług firmy Microsoft, które korzystają z usługi Azure AD, a jeśli dodaliśmy nazwę domeny do dzierżawy usługi Azure AD, użytkownicy nie będą już mogli tworzyć nowych konto Microsoft osobistych przy użyciu adresu e-mail w domenie.

### <a name="why-was-this-change-made"></a>Dlaczego ta zmiana została wprowadzona?
Korzystanie z osobistego konta Microsoft z adresem służbowym jako nazwa użytkownika jest fraught z problemami dotyczącymi użytkowników końcowych i działów IT. Na przykład:
- Użytkownicy mogą myśleć, że ich osobiste konto Microsoft są zgodne z firmą i są zgodne, gdy zapisują Dokument biznesowy w usłudze OneDrive
- Użytkownicy, którzy opuszczają organizację, zazwyczaj utracą dostęp do służbowego adresu e-mail. Gdy to zrobią, mogą nie być w stanie wrócić do swoich osobistych konto Microsoft w przypadku zapomnienia hasła. Przerzucanie to, że dział IT może zresetować swoje hasło i uzyskać dostęp do konta osobistego byłych pracowników.
- Działy IT mają fałszywe znaczenie dla własności konta i bezpieczeństwa. Jednak użytkownicy muszą tylko raz roundtrip kod do służbowego adresu e-mail, a w przyszłości mogą zmienić nazwę swojego konta.

Ta sytuacja jest szczególnie myląca dla użytkowników mających dwa konta z tym samym adresem e-mail (jeden w usłudze Azure AD & jeden konto Microsoft).

### <a name="what-does-this-experience-look-like"></a>Jak wygląda to środowisko?
Jeśli spróbujesz zarejestrować aplikację dla klienta firmy Microsoft przy użyciu służbowego adresu e-mail, zobaczysz poniższy komunikat.

   > [!div class="mx-imgBorder"]
   > ![Nie można utworzyć konta przy użyciu służbowego adresu e-mail](_img/sign-in-issues/cannot-use-work-email.png "Podaj nazwę użytkownika i hasło, aby utworzyć konto.")

Jednak jeśli spróbujesz zarejestrować się w celu uzyskania aplikacji firmy Microsoft, która obsługuje konta osobiste i służbowe, zobaczysz następujący komunikat:

   > [!div class="mx-imgBorder"]
   > ![Obsługiwane konta służbowe](_img/sign-in-issues/existing-account.png "Nie możesz utworzyć konta w tym miejscu przy użyciu służbowego adresu e-mail...")

### <a name="are-existing-accounts-affected"></a>Czy dotyczy to istniejących kont?
Opisany tutaj blok rejestracji uniemożliwia tworzenie nowych kont. Nie ma to wpływu na użytkowników, którzy mają już konto Microsoft z adresem e-mail. Jeśli jesteś już w tej sytuacji, możemy ułatwić zmianę nazwy konto Microsoft osobistej. Ten [artykuł pomocy technicznej](https://windows.microsoft.com/en-US/Windows/rename-personal-microsoft-account) zawiera proste wskazówki krok po kroku. Zmiana nazwy osobistego konto Microsoft oznacza zmianę nazwy użytkownika i nie ma wpływu na służbowy adres e-mail ani sposób logowania się do usług firmowych, takich jak Microsoft 365. Nie ma to również wpływu na Twoje osobiste rzeczy — po prostu zmienia sposób logowania się do niego. Możesz użyć innego adresu e-mail (osobistego), uzyskać nowy @outlook.com adres e-mail od firmy Microsoft lub użyć numeru telefonu jako nowej nazwy użytkownika.

> [!NOTE]
> Jeśli Twój dział INFORMATYCZNy prosi Cię o utworzenie osobistego konto Microsoft za pomocą poczty e-mail, na przykład w celu uzyskania dostępu do usług firmowych firmy Microsoft, takich jak pomoc techniczna Premium, należy skontaktować się z zespołem administracyjnym przed zmianą nazwy konta.

## <a name="deleting-a-sign-in-address-may-prevent-access-to-a-subscription"></a>Usunięcie adresu logowania może uniemożliwić dostęp do subskrypcji
W przypadku usunięcia co najmniej jednej tożsamości (MSA lub AAD) skojarzonej z subskrypcją informacje o subskrybentach, w tym nazwa użytkownika i identyfikator logowania, mogą być renderowane anonimowo, co spowodowało utratę dostępu do subskrypcji.

Aby uniknąć wpływu na dostęp do subskrypcji, użyj jednej z tych technik.
- Wdróż pojedynczy system zarządzania tożsamościami — MSA lub AAD--, ale nie oba.
- Skojarz tożsamości usługi AAD i MSA za pośrednictwem dzierżawy.

## <a name="signing-in-may-fail-when-using-aliases"></a>Logowanie może zakończyć się niepowodzeniem w przypadku korzystania z aliasów
W zależności od typu konta użytego do zalogowania się dostępne subskrypcje mogą nie być poprawnie wyświetlane podczas logowania do programu [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) . Jedną z potencjalnych przyczyn jest użycie "aliasów" lub "przyjaznych nazw" zamiast tożsamości logowania, do której przypisano subskrypcję. Jest to nazywane "aliasem".

### <a name="what-is-aliasing"></a>Co to jest aliasowanie?
Termin "aliasowanie" odnosi się do użytkowników, którzy mają różne tożsamości do logowania się do systemu Windows (lub Active Directory) oraz do uzyskiwania dostępu do poczty e-mail.

Aliasowanie może wystąpić, gdy firma ma usługę online firmy Microsoft dotyczącą logowania do katalogu, na przykład JohnD@contoso.com , ale użytkownicy uzyskują dostęp do swoich kont e-mail przy użyciu aliasów lub przyjaznych nazw, takich jak John.Doe@contoso.com . W przypadku wielu klientów, którzy zarządzają swoimi subskrypcjami za pośrednictwem usługi licencjonowania zbiorowego (VLSC), może to spowodować nieudane działanie logowania, ponieważ podany adres e-mail ( John.Doe@contoso.com ) nie jest zgodny z adresem katalogu ( JohnD@contoso.com ) wymaganym do pomyślnego uwierzytelnienia za pomocą opcji "konto służbowe".

### <a name="what-options-do-i-have"></a>Jakie są dostępne opcje?
Z perspektywy subskrybenta ważne jest, aby najpierw współpracować z administratorem w celu zrozumienia konfiguracji tożsamości firmy. W razie potrzeby administrator może potrzebować aktualizacji ustawień konta z poziomu portalu administratora lub utworzyć konto Microsoft (MSA) przy użyciu firmowego adresu e-mail. Przed wykonaniem kroków związanych z tworzeniem konta MSA skontaktuj się z administratorem w sprawie wszelkich zasad lub problemów związanych z wykonaniem tej akcji.

## <a name="resources"></a>Zasoby
- Aby uzyskać pomoc dotyczącą sprzedaży, subskrypcji, kont i rozliczeń dla subskrypcji programu Visual Studio, zobacz [Obsługa subskrypcji](https://aka.ms/vssubscriberhelp)programu Visual Studio. 

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](/visualstudio/)
- [Azure DevOps documentation (Dokumentacja usługi Azure DevOps)](/azure/devops/)
- [Dokumentacja platformy Azure](/azure/)
- [Dokumentacja Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
- Dowiedz się [, jak połączyć konta usługi MSA i AAD](/azure/active-directory/b2b/add-users-administrator) w usłudze AAD.
- Dowiedz się więcej o [zachowywanie anonimowości](anonymization.md).