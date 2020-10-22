---
title: Tożsamości dla subskrybentów programu Visual Studio
author: evanwindom
ms.author: v-evwin
manager: lank
ms.assetid: 86f2856c-8adf-4085-9962-f4136679e5ed
ms.date: 10/21/2019
ms.topic: conceptual
description: Jak dodać alternatywną tożsamość dla subskrypcji programu Visual Studio, aby korzystać z usługi Azure DevOps i platformy Azure
ms.openlocfilehash: d7820707758cd06209a412b2a860de81cb08c054
ms.sourcegitcommit: d3bca34f82de03fa34ecdd72233676c17fb3cb14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2020
ms.locfileid: "92353182"
---
# <a name="identities-for-visual-studio-subscribers"></a>Tożsamości dla subskrybentów programu Visual Studio
Gdy aktywujesz swoją subskrypcję programu Visual Studio, połączymy tożsamość (lub logowanie), która została użyta podczas aktywacji z subskrypcją programu Visual Studio. W ten sposób możemy rozpoznać użytkownika w [portalu subskrybentów programu Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), na platformie Azure DevOps i na platformie Azure.

W usłudze Azure DevOps sprawdzimy swój stan subskrypcji programu Visual Studio za każdym razem, gdy zalogujesz się, i udzielsz użytkownikom funkcji automatycznie w każdej organizacji, w której jesteś członkiem.
Ponieważ te funkcje są objęte korzyścią dla subskrybentów, możesz dodać Cię jako członka w dowolnej organizacji usługi Azure DevOps, korzystając z tożsamości połączonej z subskrypcją programu Visual Studio.

Na platformie Azure sprawdzimy swój status subskrypcji programu Visual Studio, gdy aktywujesz [miesięczne środki na korzystanie z platformy Azure DevTest](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) , które jest korzyścią dla subskrybenta.

W [portalu subskrybenta programu Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs)można dodać **alternatywną tożsamość** — oprócz tożsamości użytej podczas aktywacji. Pozwalamy dodać alternatywną tożsamość, jeśli użyto konto Microsoft, aby aktywować subskrypcję. W ten sposób można także dodać konto służbowe (używane podczas logowania do programu Visual Studio, Microsoft 365 lub sieci firmowej), co umożliwia dostęp do usługi Azure DevOps przy użyciu konta osobistego i konta służbowego.

## <a name="add-an-alternate-account-to-your-subscription"></a>Dodawanie alternatywnego konta do subskrypcji
Dodanie alternatywnego konta do subskrypcji programu Visual Studio pozwala uzyskać dostęp do korzyści z subskrypcji, takich jak usługa Azure DevOps i platforma Azure, przy użyciu innej tożsamości niż ta, do której jest przypisana subskrypcja. W przeszłości ta funkcja była dostępna tylko wtedy, gdy subskrypcja programu Visual Studio (VS) została przypisana do konta Microsoft (MSA). Ta funkcja została rozszerzona o konta służbowe w Azure Active Directory (Azure AD).

Nie powoduje to udostępnienia kopii subskrypcji dla innego konta. Umożliwia to tylko uzyskanie dostępu do dwóch korzyści za pomocą alternatywnego konta.

W przypadku wszystkich subskrypcji możesz dodać "konto służbowe", aby można było używać tego konta z korzyściami, które wymagają logowania (VS IDE, Azure DevOps i Azure).

### <a name="add-the-alternate-account"></a>Dodawanie alternatywnego konta
1. Zaloguj się do portalu subskrybentów programu Visual Studio przy użyciu konto Microsoft ( https://my.visualstudio.com) .
2. Wybierz kartę **subskrypcje** .
3. Wybierz pozycję **Dodaj alternatywne konto**.
4. Dodaj swoje konto służbowe.
    > [!div class="mx-imgBorder"]
    > ![Dodaj konto służbowe](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png "Dodawanie konta służbowego jako alternatywnego konta w ramach subskrypcji.")

5. Użyj konta służbowego, aby zalogować się do usługi Azure DevOps (https://{YourAccount}. VisualStudio. com).

Twoje alternatywne konto jest dodawane do subskrypcji programu Visual Studio, co pozwala obu tożsamości wykorzystać zalety subskrypcji, które wymagają zalogowania się przy użyciu alternatywnego konta (IDE, Azure DevOps i Azure).

## <a name="faq"></a>Często zadawane pytania

### <a name="q--why-doesnt-azure-devops-recognize-me-as-a-visual-studio-subscriber"></a>P: Dlaczego usługa Azure DevOps nie rozpoznaje mnie jako subskrybenta programu Visual Studio?

Odp.: usługa Azure DevOps powinna automatycznie rozpoznawać swoją subskrypcję po zalogowaniu się przy użyciu tożsamości podstawowej lub alternatywnej. Jeśli tak się nie dzieje, możesz wypróbować kilka rzeczy:

* Sprawdź, czy masz aktywną subskrypcję programu Visual Studio, która obejmuje [usługę Azure DevOps](vs-azure-devops.md#eligibility) .

* Upewnij się, że używasz nazwy logowania/tożsamości, która jest podstawową lub alternatywną tożsamością subskrypcji programu Visual Studio.

* Odwiedź [Portal subskrybentów programu Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) co najmniej raz przed zalogowaniem się do usługi Azure DevOps.

Jeśli usługa Azure DevOps nadal nie rozpoznaje Twojej subskrypcji, skontaktuj się z [pomocą techniczną platformy Azure DevOps](https://azure.microsoft.com/support/devops/).

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](/visualstudio/)
- [Dokumentacja usługi Azure DevOps](/azure/devops/)
- [Dokumentacja platformy Azure](/azure/)
- [Dokumentacja Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Następne kroki 
Aby uzyskać więcej informacji na temat korzystania z platformy Azure, platformy Azure DevOps lub środowiska IDE programu Visual Studio, zapoznaj się z następującymi zasobami:
- [Azure](vs-azure.md)
- [Azure DevOps](vs-azure-devops.md)
- [Program Visual Studio](vs-ide-benefit.md)