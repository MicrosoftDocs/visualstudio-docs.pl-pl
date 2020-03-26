---
title: Logowanie się do subskrypcji programu Visual Studio za pomocą konta Usługi GitHub | Dokumenty firmy Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 1bdcb3c9-bba1-4e25-a609-9d7e539d78e0
ms.date: 03/09/2020
ms.topic: conceptual
description: Dowiedz się, jak zalogować się do subskrypcji programu Visual Studio za pomocą konta GitHub.
ms.openlocfilehash: 722eeae315a8b4a6bd93fb1048846b147b294afa
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233232"
---
# <a name="signing-in-to-visual-studio-subscriptions-with-your-github-account"></a>Logowanie się do subskrypcji programu Visual Studio za pomocą konta Usługi GitHub 

Kroki, aby zalogować się do subskrypcji programu Visual Studio zależą od rodzaju konta, którego używasz. Na przykład użytkownik może używać konta Microsoft (MSA) lub adresu e-mail podanego przez pracodawcę lub szkołę. Od stycznia 2019 r. możesz teraz również korzystać z konta Usługi GitHub, aby zalogować się do niektórych subskrypcji. 

W tym artykule zostaną opisane kroki logowania się za pomocą konta GitHub.

## <a name="signing-in-with-your-github-account"></a>Logowanie się za pomocą konta GitHub

Obsługa tożsamości usługi GitHub umożliwia korzystanie z istniejącego konta Usługi GitHub jako poświadczenia dla nowego lub istniejącego konta Microsoft, łącząc konto GitHub z kontem Microsoft. 

Po zalogowaniu się za pomocą usługi GitHub firma Microsoft sprawdza, czy wszystkie adresy e-mail skojarzone z kontem Usługi GitHub są zgodne z istniejącym osobistym lub korporacyjnym kontem Microsoft. Jeśli adres jest zgodny z twoim kontem przedsiębiorstwa, zostanie wyświetlony monit o zalogowanie się na to konto. Jeśli adres pasuje do konta osobistego, dodamy Twoje konto GitHub jako metodę logowania do tego konta osobistego.

Po połączeniu poświadczeń konta GitHub i Konta Microsoft można używać tego logowania jednokrotnego w dowolnym miejscu, w którym można używać osobistego konta Microsoft, na przykład w witrynach platformy Azure, aplikacjach pakietu Office i konsoli Xbox. Te konta mogą być również używane do logowania gościa usługi Azure Active Directory jako konta Microsoft, przy założeniu, że adres e-mail jest zgodny z adresem zaproszenia.

> [!NOTE]
> Łączenie tożsamości usługi GitHub z kontem Microsoft nie daje firmie Microsoft dostępu do kodu. Gdy aplikacje, takie jak Azure DevOps i Visual Studio wymagają dostępu do repozytoriów kodu, zostanie wyświetlony monit o udzielenie określonej zgody na ten dostęp. 

### <a name="frequently-asked-questions"></a>Często zadawane pytania
Poniższe często zadawane pytania dotyczą pytań, które mogą wystąpić dotyczące używania poświadczeń konta Usługi GitHub do logowania się do subskrypcji programu Visual Studio.

#### <a name="q-i-forgot-my-github-password--how-can-i-access-my-account-now"></a>P: Nie pamiętam hasła do githubu.  Jak mogę teraz uzyskać dostęp do mojego konta?
Odp.: Możesz odzyskać swoje konto GitHub, przechodząc do [resetowania hasła.](https://github.com/password_reset) Możesz też odzyskać swoje konto Microsoft połączone z GitHub, wpisując adres e-mail konta GitHub w [witrynie Odzyskaj swoje konto.](https://account.live.com/password/reset)

#### <a name="q-i-deleted-my-github-account--how-can-i-access-my-microsoft-account-msa-now"></a>P: Usunąłem moje konto GitHub.  Jak mogę teraz uzyskać dostęp do mojego konta Microsoft (MSA)?
Odp.: Jeśli nie masz żadnych innych poświadczeń w msa (takich jak hasło, aplikacja authenticator lub klucz zabezpieczeń), możesz odzyskać swoje konto Microsoft przy użyciu adresu e-mail dołączonego do niego. Aby rozpocząć, przejdź do [witryny Odzyskaj swoje konto](https://account.live.com/password/reset). Musisz dodać hasło do swojego konta, abyśmy wiedzieli, jak zalogować się później. 

#### <a name="q-theres-no-sign-in-with-github-option-on-the-sign-in-page--how-can-i-use-my-github-credentials-to-sign-in"></a>P: Na stronie logowania nie ma opcji "Zaloguj się za pomocą githubu".  Jak mogę użyć moich poświadczeń GitHub do logowania?
Odp.: Wpisz adres e-mail konta Usługi GitHub wybrany podczas tworzenia konta Microsoft połączonego z witryną GitHub. Odszukamy Cię i wyślemy do GitHub w celu zalogowania się. Lub jeśli na stronie logowania znajduje się łącze opcji logowania, użyj przycisku **Zaloguj się za pomocą usługi GitHub,** który jest wyświetlany po kliknięciu tego łącza. 

#### <a name="q-i-cant-sign-in-to-some-of-my-apps-and-products-with-github--why"></a>P: Nie mogę zalogować się do niektórych moich aplikacji i produktów za pomocą gitHub.  Dlaczego?
O: Nie wszystkie produkty firmy Microsoft mogą uzyskiwać dostęp do GitHub.com ze strony logowania — na przykład konsol Xbox. Zamiast tego, po wpisaniu adresu e-mail z połączonego konta GitHub, wyślemy kod na ten adres, abyśmy mogli zweryfikować, że to naprawdę Ty. Nadal logujesz się na to samo konto, po prostu za pomocą innej metody logowania. 

#### <a name="q--ive-added-a-password-to-the-microsoft-account-i-have-linked-to-my-github-account--will-that-cause-a-problem"></a>P: Dodałem hasło do konta Microsoft, które połączyłem z moim kontem GitHub.  Czy to spowoduje problem?
O: Wcale nie. Nie zmienia to hasła usługi GitHub; po prostu będziesz mieć inny sposób logowania się do konta Microsoft. Za każdym razem, gdy zalogujesz się przy użyciu swojego adresu e-mail, zaoferujemy Ci możliwość zalogowania się za pomocą hasła do konta Microsoft lub ujmując się w usłudze GitHub, aby się zalogować. Zdecydowanie zalecamy, aby w przypadku konieczności dodania hasła upewnij się, że różni się ono od hasła do konta Usługi GitHub.

#### <a name="q-i-want-to-add-the-authenticator-app-to-the-account-i-created-using-github--can-i-do-that"></a>P: Chcę dodać aplikację Authenticator do konta utworzonego za pomocą gitHub.  Czy mogę to zrobić?
O: Nie ma problemu — wystarczy pobrać aplikację i zalogować się przy użyciu adresu e-mail. Gdy zalogujesz się przy użyciu adresu e-mail, zostanie wyświetlony monit o wybranie [aplikacji Authenticator](https://www.microsoft.com/p/microsoft-authenticator/9nblgggzmcj6) lub GitHub jako poświadczenia.

#### <a name="q-ive-enabled-two-factor-authentication-on-both-my-github-and-microsoft-accounts-msa-but-when-i-sign-in-to-my-msa-im-still-asked-to-authenticate-twice--why"></a>P: Włączono uwierzytelnianie dwuskładnikowe zarówno na kontach GitHub, jak i Microsoft (MSA), ale gdy loguję się do msa, nadal jestem proszony o uwierzytelnienie się dwukrotnie.  Dlaczego?
Odp.: Ze względu na ograniczenia zabezpieczeń firma Microsoft liczy zalogowanie się za pomocą usługi GitHub jako weryfikację jednoskładnikową, nawet jeśli włączono weryfikację dwuetapową. W związku z tym musisz ponownie uwierzytelnić się dla swojego konta Microsoft. 

#### <a name="q--how-can-i-tell-if-my-microsoft-account-and-github-accounts-are-linked"></a>Pyt.: Jak sprawdzić, czy moje konto Microsoft i konta GitHub są połączone?
O: Za każdym razem, gdy podpisujesz się przy użyciu aliasu konta (adres e-mail, numer telefonu, nazwa Skype), pokażemy Ci wszystkie metody logowania dla Twojego konta. Jeśli nie widzisz tam GitHub, nie masz jeszcze skonfigurować.

#### <a name="q--how-can-i-unlink-my-microsoft-and-github-accounts"></a>Pyt.: Jak mogę odłączyć moje konta Microsoft i GitHub? 
Odp.: Przejdź do [karty Zabezpieczenia](https://account.microsoft.com/security) account.microsoft.com i kliknij pozycję Więcej **opcji zabezpieczeń,** aby odłączyć konto Usługi GitHub. Odłączenie konta Usługi GitHub powoduje usunięcie go jako metody logowania i usunięcie dostępu do wszystkich repozytoriów usługi GitHub w programie Visual Studio. Inne produkty firmy Microsoft mogły zażądać dostępu do twojego konta Usługi GitHub oddzielnie, więc usunięcie dostępu w tym miejscu nie spowoduje usunięcia dostępu we wszystkich produktach. Przejdź do strony [uprawnień aplikacji](https://github.com/settings/applications) w profilu Usługi GitHub, aby odwołać zgodę z wymienionych tam aplikacji.

#### <a name="q--i-try-to-use-my-github-account-to-sign-in-but-im-prompted-that-i-already-have-a-microsoft-identity-that-i-should-use-instead--whats-happening"></a>P: Próbuję użyć mojego konta GitHub do logowania się, ale jest wyświetlany monit, że mam już tożsamość firmy Microsoft, której powinienem użyć.  Co się dzieje?
Odp.: Jeśli masz adres e-mail usługi Azure Active Directory na koncie Usługi GitHub, oznacza to, że masz już tożsamość firmy Microsoft, która może uzyskiwać dostęp do platformy Azure i uruchamiać potoki ciągłej integracji przy użyciu kodu Usługi GitHub. Przy użyciu tego konta zapewnia, że zasoby platformy Azure i potoki kompilacji pozostają w granicach organizacji. Jeśli jednak wykonujesz osobistą pracę, zalecamy umieszczenie osobistego adresu e-mail na koncie GitHub, aby zawsze mieć do niego dostęp. Po wykonaniu tej tej opcji spróbuj zalogować się ponownie i wybierz pozycję **Użyj innego adresu e-mail,** gdy zostanie wyświetlony monit o zalogowanie się na konto służbowe. Umożliwi to utworzenie nowego konta Microsoft przy użyciu tego osobistego adresu e-mail.

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja usługi Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
Po pomyślnym zalogowaniu się do portalu subskrypcji zalecamy odwiedzenie strony Korzyści https://my.visualstudio.com/benefits i zapoznanie się z doskonałymi narzędziami, usługami i ofertami dostępnymi dla Ciebie.  
