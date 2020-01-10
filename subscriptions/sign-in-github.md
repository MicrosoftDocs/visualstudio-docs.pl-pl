---
title: Logowanie do subskrypcji programu Visual Studio za pomocą konta usługi GitHub | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/11/2019
ms.topic: conceptual
description: Dowiedz się, jak zalogować się do subskrypcji programu Visual Studio za pomocą konta usługi GitHub.
ms.openlocfilehash: 8a1c2884dbc5570ab18cf7496c699774702b5b62
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850532"
---
# <a name="signing-in-to-visual-studio-subscriptions-with-your-github-account"></a>Logowanie do subskrypcji programu Visual Studio za pomocą konta usługi GitHub 

Kroki umożliwiające zalogowanie się do subskrypcji programu Visual Studio zależą od rodzaju konta, którego używasz. Na przykład może być używane konto Microsoft (MSA) lub adres e-mail dostarczony przez pracodawcę lub szkołę. Od stycznia 2019 możesz teraz zalogować się do niektórych subskrypcji przy użyciu konta usługi GitHub. 

W tym artykule przedstawiono procedurę logowania się przy użyciu konta usługi GitHub.

## <a name="signing-in-with-your-github-account"></a>Logowanie się przy użyciu konta usługi GitHub

Obsługa tożsamości usługi GitHub umożliwia korzystanie z istniejącego konta w usłudze GitHub jako poświadczenia dla nowego lub istniejącego konto Microsoft, łącząc konto usługi GitHub z konto Microsoft. 

Po zalogowaniu się za pomocą usługi GitHub firma Microsoft sprawdza, czy adresy e-mail skojarzone z kontem w usłudze GitHub są zgodne z istniejącymi konto Microsoftami osobistymi i firmowymi. Jeśli adres jest zgodny z Twoim kontem przedsiębiorstwa, zostanie wyświetlony monit o zalogowanie się do tego konta. Jeśli adres jest zgodny z kontem osobistym, dodamy konto usługi GitHub jako metodę logowania do tego konta osobistego.

Po połączeniu poświadczeń usługi GitHub i konto Microsoft można korzystać z logowania jednokrotnego w dowolnym miejscu, w którym można używać konto Microsoft osobistego, takich jak witryny platformy Azure, aplikacje pakietu Office i Xbox. Te konta mogą być również używane na potrzeby logowania Azure Active Directory Gości jako konto Microsoft, przy założeniu, że adres e-mail jest zgodny z adresem na zaproszeniu.

> [!NOTE]
> Łączenie tożsamości usługi GitHub z konto Microsoft nie daje dostępu do kodu. Gdy aplikacje takie jak Azure DevOps i Visual Studio wymagają dostępu do repozytoriów kodu, zostanie wyświetlony monit o przyznanie określonej zgody na dostęp. 

### <a name="frequently-asked-questions"></a>Często zadawane pytania
Poniższe często zadawane pytania umożliwiają zalogowanie się do subskrypcji programu Visual Studio w przypadku korzystania z poświadczeń konta usługi GitHub.

#### <a name="q-i-forgot-my-github-password--how-can-i-access-my-account-now"></a>P: nie pamiętam mojego hasła usługi GitHub.  Jak mogę teraz uzyskać dostęp do mojego konta?
Odp.: możesz odzyskać konto usługi GitHub, przechodząc do [resetowania hasła](https://github.com/password_reset). Możesz też odzyskać konto Microsoft połączone z usługą GitHub, wprowadzając adres e-mail konta usługi GitHub w obszarze [Odzyskaj konto](https://account.live.com/password/reset).

#### <a name="q-i-deleted-my-github-account--how-can-i-access-my-microsoft-account-msa-now"></a>P: Usunięto moje konto usługi GitHub.  Jak mogę teraz uzyskać dostęp do konta konto Microsoft (MSA)?
Odp.: Jeśli nie masz żadnych innych poświadczeń w usłudze MSA (na przykład hasło, aplikacja uwierzytelniania lub klucz zabezpieczeń), możesz odzyskać konto Microsoft przy użyciu dołączanego adresu e-mail. Aby rozpocząć, przejdź do obszaru [Odzyskiwanie konta](https://account.live.com/password/reset). Musisz dodać hasło do swojego konta, aby dowiedzieć się, jak zalogować się później. 

#### <a name="q-theres-no-sign-in-with-github-option-on-the-sign-in-page--how-can-i-use-my-github-credentials-to-sign-in"></a>P: nie ma opcji "Zaloguj się za pomocą usługi GitHub" na stronie logowania.  Jak można się zalogować przy użyciu poświadczeń usługi GitHub?
Odp.: wpisz adres e-mail konta usługi GitHub wybrany podczas tworzenia konto Microsoft połączonego z usługą GitHub. Zajrzyjmy ci i wyślemy Ci wiadomość do usługi GitHub w celu zalogowania się. Jeśli na stronie logowania znajduje się link opcji logowania, użyj przycisku **Zaloguj się przy użyciu usługi GitHub** , który jest wyświetlany po kliknięciu tego linku. 

#### <a name="q-i-cant-sign-in-to-some-of-my-apps-and-products-with-github--why"></a>P: nie mogę zalogować się do niektórych moich aplikacji i produktów za pomocą usługi GitHub.  Dlaczego?
Odp.: nie wszystkie produkty firmy Microsoft mogą uzyskać dostęp do GitHub.com ze strony logowania, na przykład konsol Xbox. Zamiast tego po wpisaniu adresu e-mail z połączonego konta usługi GitHub wyślemy do niego kod, więc możemy sprawdzić, czy jest to naprawdę ty. Nadal logujesz się do tego samego konta, po prostu przez inną metodę logowania. 

#### <a name="q--ive-added-a-password-to-the-microsoft-account-i-have-linked-to-my-github-account--will-that-cause-a-problem"></a>P: dodano hasło do konto Microsoft, które zostało połączone z kontem usługi GitHub.  Czy spowoduje to problem?
Odp.: nie. Nie spowoduje to zmiany hasła usługi GitHub. będziesz mieć już inny sposób na zalogowanie się do konto Microsoft. Za każdym razem, gdy zalogujesz się przy użyciu swojego adresu e-mail, oferujemy możliwość zalogowania się przy użyciu hasła konto Microsoft lub przejściu do usługi GitHub, aby się zalogować. Zdecydowanie zalecamy, aby w razie konieczności dodać hasło, upewnij się, że jest ono inne niż hasło do konta usługi GitHub.

#### <a name="q-i-want-to-add-the-authenticator-app-to-the-account-i-created-using-github--can-i-do-that"></a>P: chcę dodać aplikację Authenticator do konta utworzonego za pomocą usługi GitHub.  Czy mogę to zrobić?
Odp.: nie ma problemu — po prostu pobierz aplikację i zaloguj się przy użyciu swojego adresu e-mail. Po zalogowaniu się przy użyciu adresu e-mail zostanie wyświetlony monit o wybranie [aplikacji Authenticator](https://www.microsoft.com/account/authenticator#getapp) lub GitHub jako poświadczenia.

#### <a name="q-ive-enabled-two-factor-authentication-on-both-my-github-and-microsoft-accounts-msa-but-when-i-sign-in-to-my-msa-im-still-asked-to-authenticate-twice--why"></a>Pytanie: włączono uwierzytelnianie dwuskładnikowe zarówno na stronie my GitHub, jak i na kontach Microsoft (MSA), ale po zalogowaniu się do mojego elementu MSA nadal jest wymagane dwukrotne uwierzytelnienie.  Dlaczego?
Odp.: ze względu na ograniczenia zabezpieczeń firma Microsoft zlicza logowanie za pomocą usługi GitHub w ramach weryfikacji jednoskładnikowej, nawet jeśli w tym miejscu włączono weryfikację dwuetapową. W związku z tym należy ponownie uwierzytelnić konto Microsoft. 

#### <a name="q--how-can-i-tell-if-my-microsoft-account-and-github-accounts-are-linked"></a>P: Jak mogę sprawdzić, czy są połączone konta konto Microsoft i GitHub?
Odp.: za każdym razem, gdy zalogujesz się przy użyciu aliasu konta (adres e-mail, numer telefonu, nazwa użytkownika Skype), zostaną wyświetlone wszystkie metody logowania dla Twojego konta. Jeśli nie widzisz tam usługi GitHub, nie zostało to jeszcze zrobione.

#### <a name="q--how-can-i-unlink-my-microsoft-and-github-accounts"></a>P: Jak mogę odłączyć moje konta Microsoft i GitHub? 
Odp.: Przejdź do [karty zabezpieczenia](https://account.microsoft.com/security) w programie account.Microsoft.com, a następnie kliknij pozycję **więcej opcji zabezpieczeń** , aby odłączyć konto usługi GitHub. Odłączenie konta usługi GitHub spowoduje usunięcie go jako metody logowania i usunięcie dostępu do wszystkich repozytoriów GitHub w programie Visual Studio. Inne produkty firmy Microsoft mogły zażądać dostępu do konta usługi GitHub osobno, więc usunięcie dostępu nie spowoduje usunięcia dostępu we wszystkich produktach. Przejdź do strony [uprawnienia aplikacji](https://github.com/settings/applications) w profilu usługi GitHub, aby odwołać zgodę z aplikacji znajdujących się na liście.

#### <a name="q--i-try-to-use-my-github-account-to-sign-in-but-im-prompted-that-i-already-have-a-microsoft-identity-that-i-should-use-instead--whats-happening"></a>Pytanie: próbuję zalogować się przy użyciu konta usługi GitHub, ale otrzymuję monit o podanie tożsamości firmy Microsoft, której należy użyć zamiast tego.  Co się dzieje?
Odp.: Jeśli masz Azure Active Directory adres e-mail na koncie usługi GitHub, oznacza to, że masz już tożsamość firmy Microsoft, która może uzyskiwać dostęp do platformy Azure i uruchamiać potoki CI przy użyciu kodu usługi GitHub. Użycie tego konta zapewnia, że Twoje zasoby platformy Azure i potoki kompilacji pozostaną w granicach organizacyjnych. Jeśli jednak wykonujesz osobistą służbę, zalecamy umieszczenie osobistego adresu e-mail na Twoim koncie usługi GitHub, aby zawsze miał dostęp do niego. Po wykonaniu tej czynności spróbuj zalogować się ponownie i wybierz opcję **Użyj innego adresu e-mail** , gdy zostanie wyświetlony monit o zalogowanie się do konta służbowego. Pozwoli to utworzyć nowe konto Microsoft przy użyciu tego osobistego adresu e-mail.

## <a name="next-steps"></a>Następne kroki
Po pomyślnym zalogowaniu się do portalu subskrypcji zalecamy odwiedzenie strony korzyści w https://my.visualstudio.com/benefits i eksplorowanie doskonałych narzędzi, usług i ofert dostępnych dla Ciebie.  
