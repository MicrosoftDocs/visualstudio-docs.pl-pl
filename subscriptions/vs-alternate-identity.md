---
title: Tożsamości dla subskrybentów programu Visual Studio
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 04/10/2018
ms.topic: conceptual
description: Jak dodać alternatywne tożsamości dla Twojej subskrypcji programu Visual Studio na potrzeby usługi Azure DevOps i platformie Azure
searchscope: vs subscription
ms.openlocfilehash: 63a372d4a0e0e70a008f86a36aae73516bf42458
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62428106"
---
# <a name="identities-for-visual-studio-subscribers"></a>Tożsamości dla subskrybentów programu Visual Studio

Podczas aktywowania subskrypcji programu Visual Studio, można przejść tożsamości (lub logowania) używanej podczas aktywacji przy użyciu subskrypcji programu Visual Studio. Dzięki temu firma Microsoft może rozpoznawać należy na [portal dla subskrybentów programu Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs)w DevOps platformy Azure, a na platformie Azure.

W metodyce DevOps platformy Azure możemy Sprawdź stan swojej subskrypcji programu Visual Studio, każdym razem, gdy możesz zalogować się i udzielają Ci funkcji automatycznie w każdej organizacji, w którym użytkownik jest członkiem.
Ponieważ te funkcje są dołączone jako korzyści dla subskrybentów, jest to bezpłatne o dodanie Cię jako członka w dowolnej organizacji DevOps platformy Azure, korzystając z tożsamość, która jest połączona z subskrypcją programu Visual Studio.

Na platformie Azure, możemy sprawdzić stan swojej subskrypcji programu Visual Studio, aktywując swoje [miesięcznych środków platformy Azure](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) oznacza to korzyści dla subskrybentów.

W ramach [portal dla subskrybentów programu Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), można dodać **alternatywnej tożsamości** — oprócz tożsamość używana podczas aktywacji. Obecnie firma Microsoft zezwala na dodawanie alternatywnej tożsamości w przypadku korzystania z konta Microsoft do aktywowania subskrypcji. Ten sposób można również dodać pracy konta firmowego lub szkolnego (który jest używany podczas logowania się do programu Visual Studio, usługi Office 365 lub siecią firmową lub szkolnego), umożliwiając dostęp DevOps platformy Azure przy użyciu konta osobistego i swojego konta firmowego lub szkolnego.

## <a name="add-an-alternate-account-to-your-visual-studio-subscription"></a>Dodaj alternatywne konto do subskrypcji programu Visual Studio

Dodawanie alternatywnego konta z subskrypcją programu Visual Studio umożliwia dostęp do korzyści z subskrypcji, takich jak DevOps platformy Azure i platformą Azure przy użyciu innej tożsamości niż ta, która jest przypisana subskrypcja. W przeszłości ta funkcja była dostępna, tylko wtedy, gdy Twoja subskrypcja programu Visual Studio (VS) została przypisana do konta Microsoft (MSA). Uzupełniliśmy tę funkcję dla kont służbowych w usłudze Azure Active Directory (Azure AD).

To nie zapewnia kopii subskrypcji na inne konto; zapewnia tylko dwie korzyści z kontem alternatywnych dostęp do usługi.

W przypadku wszystkich subskrypcji można dodać "konto służbowe", aby można było używać tego konta z korzyści, które wymagają logowania (VS IDE, DevOps platformy Azure i platformy Azure).

### <a name="add-the-alternate-account"></a>Dodaj alternatywne konto

1. Zaloguj się do portalu subskrybenta programu Visual Studio z Twoim kontem Microsoft (https://my.visualstudio.com).

2. Przejdź do **subskrypcje**.

    > [!div class="mx-imgBorder"]
    > ![Dodaj alternatywne konto — przejdź do subskrypcji w portalu programu VS](_img/vs-alternate-identity/my-vs-subscriptions.png)

3. Wybierz **Dodaj alternatywne konto**.
    > [!div class="mx-imgBorder"]
    > ![Wybierz opcję Dodaj alternatywne konto ](_img/vs-alternate-identity/choose-add-alternate-account.png)

4. Dodaj swoje konto służbowe.
    > [!div class="mx-imgBorder"]
    > ![Dodaj konto służbowe](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. Użyj swojego konta firmowego lub szkolnego, aby zarejestrować się w DevOps platformy Azure (https://{youraccount}.visualstudio.com).
    > [!div class="mx-imgBorder"]
    > ![Użyj swojego konta firmowego lub szkolnego](_img/vs-alternate-identity/sign-in-with-alternate-account.png)

Twoje alternatywne konto jest dodawane do subskrypcji programu Visual Studio, dzięki czemu zarówno tożsamości korzystanie z zalet subskrypcji, które wymagają Zaloguj się przy użyciu alternatywnego konta (IDE, DevOps platformy Azure i platformy Azure).

## <a name="faq"></a>Najczęściej zadawane pytania

### <a name="q--why-doesnt-azure-devops-recognize-me-as-a-visual-studio-subscriber"></a>PYT.:  Dlaczego nie DevOps platformy Azure rozpoznaje mnie jako subskrybent programu Visual Studio?

Odp.: Azure DevOps powinien rozpoznaje automatycznie subskrypcji Zaloguj się przy użyciu Twojej tożsamości podstawowej lub alternatywnej. W przeciwnym razie możesz wypróbować kilka rzeczy:

* Sprawdź, czy aktywną subskrypcję programu Visual Studio, [obejmuje DevOps platformy Azure jako pakiety korzyści](vs-azure-devops.md).

* Upewnij się, że używasz logowania/tożsamość, która może być podstawowy lub alternatywnej tożsamości dla Twojej subskrypcji programu Visual Studio.

* Odwiedź stronę [portal dla subskrybentów programu Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) co najmniej raz przed zarejestrowanie się w DevOps platformy Azure.

Jeśli nadal DevOps platformy Azure nie rozpoznaje subskrypcji [się z pomocą techniczną](https://visualstudio.microsoft.com/team-services/support/)
