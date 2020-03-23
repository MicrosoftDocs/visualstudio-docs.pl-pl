---
title: Tożsamości dla subskrybentów programu Visual Studio
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/19/2019
ms.topic: conceptual
description: Jak dodać alternatywną tożsamość dla subskrypcji programu Visual Studio, aby użyć dla usługi Azure DevOps i platformy Azure
ms.openlocfilehash: e19774f2314280b2e5a995a7d83336f1403682a4
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "72816559"
---
# <a name="identities-for-visual-studio-subscribers"></a>Tożsamości dla subskrybentów programu Visual Studio
Po aktywowaniu subskrypcji programu Visual Studio łączymy tożsamość (lub login), która została użyta podczas aktywacji z subskrypcją programu Visual Studio. W ten sposób możemy rozpoznać Cię w [portalu subskrybenta programu Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), w usłudze Azure DevOps i na platformie Azure.

W usłudze Azure DevOps sprawdzamy stan subskrypcji programu Visual Studio przy każdym logowaniu i automatycznie udzielamy funkcji w każdej organizacji, w której jesteś członkiem.
Ponieważ te funkcje są uwzględniane jako korzyści subskrybenta, można dodać użytkownika jako członka w dowolnej organizacji Azure DevOps podczas korzystania z tożsamości, która jest połączona z subskrypcją programu Visual Studio.

Na platformie Azure sprawdzamy stan subskrypcji programu Visual Studio po aktywowaniu [miesięcznych indywidualnych kredytów usługi Azure DevTest,](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) które są korzyścią dla subskrybenta.

W [portalu subskrybenta programu Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs)można dodać **alternatywną tożsamość** — oprócz tożsamości używanej podczas aktywacji. Zezwalamy na dodanie alternatywnej tożsamości, jeśli do aktywacji subskrypcji użyto konta Microsoft. W ten sposób można również dodać konto służbowe (którego używasz podczas logowania do programu Visual Studio, usługi Office 365 lub sieci firmowej lub szkolnej), umożliwiając dostęp do usługi Azure DevOps przy użyciu zarówno konta osobistego, jak i konta służbowego.

## <a name="add-an-alternate-account-to-your-subscription"></a>Dodawanie konta alternatywnego do subskrypcji
Dodanie konta alternatywnego do subskrypcji programu Visual Studio umożliwia dostęp do korzyści subskrypcji, takich jak Azure DevOps i Azure, z inną tożsamością niż ta, do której jest przypisana subskrypcja. W przeszłości ta funkcja była dostępna tylko wtedy, gdy subskrypcja programu Visual Studio (VS) została przypisana do konta Microsoft (MSA). Rozszerzyliśmy tę funkcję dla kont służbowych w usłudze Azure Active Directory (Azure AD).

Nie zapewnia to kopii subskrypcji na inne konto; zapewnia tylko możliwość dostępu do dwóch korzyści z kontem alternatywnym.

Dla wszystkich subskrypcji można dodać "konto służbowe", dzięki czemu można użyć tego konta z korzyści, które wymagają logowania (VS IDE, Azure DevOps i azure).

### <a name="add-the-alternate-account"></a>Dodawanie konta alternatywnego
1. Zaloguj się do portalu subskrybenta programu Visualhttps://my.visualstudio.com)Studio za pomocą swojego konta Microsoft ( .
2. Kliknij kartę **Subskrypcje.**
3. Wybierz **pozycję Dodaj konto alternatywne**.
4. Dodaj swoje konto służbowe.
    > [!div class="mx-imgBorder"]
    > ![Dodawanie konta służbowego](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. Zaloguj się do usługi Azure DevOps (https://{youraccount}.visualstudio.com).
    > [!div class="mx-imgBorder"]
    > ![Używanie konta służbowego](_img/vs-alternate-identity/sign-in-with-alternate-account.png)

Twoje konto alternatywne jest dodawane do subskrypcji programu Visual Studio, umożliwiając obu tożsamości do korzystania z zalet subskrypcji, które wymagają, aby zalogować się przy użyciu konta alternatywnego (IDE, Azure DevOps i azure).

## <a name="faq"></a>Często zadawane pytania

### <a name="q--why-doesnt-azure-devops-recognize-me-as-a-visual-studio-subscriber"></a>Pyt.: Dlaczego usługa DevOps nie rozpoznaje mnie jako subskrybenta programu Visual Studio?

Odp.: Usługa Azure DevOps powinna automatycznie rozpoznawać subskrypcję po zalogowaniu się przy użyciu tożsamości podstawowej lub alternatywnej. Jeśli nie, możesz wypróbować kilka rzeczy:

* Sprawdź, czy masz aktywną subskrypcję programu Visual Studio, która zawiera [usługi Azure DevOps](vs-azure-devops.md#eligibility) jako korzyść.

* Upewnij się, że używasz logowania/tożsamości, która jest podstawową lub alternatywną tożsamością subskrypcji programu Visual Studio.

* Odwiedź [portal subskrybentów programu Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) co najmniej raz przed zalogowaniem się do usługi Azure DevOps.

Jeśli usługa Azure DevOps nadal nie rozpoznaje twojej subskrypcji, skontaktuj się z [pomocą techniczną usługi Azure DevOps.](https://azure.microsoft.com/support/devops/)
