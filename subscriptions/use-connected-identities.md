---
title: Jak używać połączonych konto Microsoft i Azure Active Directory tożsamości | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 09/27/2019
ms.topic: conceptual
robots: noindex, nofollow
description: Dowiedz się, jak korzystać z połączonych kont Microsoft i tożsamości Azure Active Directory
ms.openlocfilehash: 1a862caa1f984f5d22f041a6f0cbff6534d8cc1c
ms.sourcegitcommit: bcdab788085bd9931d73883fe70cd5831317dca2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2019
ms.locfileid: "72816578"
---
# <a name="how-to-use-connected-identities-in-visual-studio-subscriptions"></a>Jak używać połączonych tożsamości w subskrypcjach programu Visual Studio
Jeśli otrzymasz subskrypcję programu Visual Studio za pomocą swojej firmy lub szkoły i używasz konto Microsoft (MSA) do logowania się, administrator subskrypcji może połączyć Twoje konto MSA z Twoją tożsamością w Azure Active Directory organizacji (Azure AD).  Spowoduje to zmianę sposobu uzyskiwania dostępu do niektórych korzyści uwzględnionych w Twojej subskrypcji. 

## <a name="overview-of-connected-ids"></a>Przegląd połączonych identyfikatorów
Organizacje są coraz bardziej przenoszone do tożsamości opartych na usłudze Azure AD, aby zapewnić lepsze zabezpieczenia i obsługę zautomatyzowanego zarządzania subskrypcjami.  Jeśli subskrypcja używa konta MSA, takiego jak @outlook.com lub inny osobisty adres e-mail, administrator może zmienić wiadomość e-mail dotyczącą logowania na swoją tożsamość usługi Azure AD.  Spowoduje to zmianę sposobu logowania się do portalu subskrybenta w https://my.visualstudio.com ale może nie zmienić sposobu uzyskiwania dostępu do wszystkich korzyści.  

Jeśli administrator łączy Twoje konto MSA i tożsamości usługi Azure AD, otrzymasz wiadomość e-mail z informacją o konieczności rozpoczęcia uzyskiwania dostępu do subskrypcji programu Visual Studio za pomocą tożsamości usługi Azure AD zamiast Twojego konta MSA. 

## <a name="how-to-access-benefits-using-azure-ad-identities"></a>Jak uzyskać dostęp do korzyści przy użyciu tożsamości usługi Azure AD
Gdy administrator nawiązał połączenie Twojego konta MSA z tożsamością usługi Azure AD, musisz zalogować się do portalu subskrybenta w https://my.visualstudio.com z tożsamością usługi Azure AD, aby uzyskać dostęp do korzyści, które korzystają z usługi Azure AD.  Należą do nich następujące elementy:
- Visual Studio IDE
- Azure DevOps
- Kredyty na korzystanie z usługi Azure DevTest

## <a name="how-to-access-benefits-using-your-msa"></a>Jak uzyskać dostęp do korzyści przy użyciu konta MSA
W przypadku wielu korzyści oferowanych w ramach subskrypcji programu Visual Studio, takich jak Pluralsight, LinkedIn, CloudPilot i inne, w rzeczywistości tworzysz konta użytkowników w witrynach sieci Web partnerów.  W przypadku tych kont należy nadal używać tożsamości, która została użyta podczas tworzenia konta.  Na przykład w przypadku aktywowania korzyści Pluralsight przy użyciu konta MSA należy nadal korzystać z usługi MSA podczas podejmowania szkolenia Pluralsight, niezależnie od tożsamości używanej do logowania się w portalu subskrybenta.  

## <a name="use-an-alternate-identity-to-access-your-subscription"></a>Korzystanie z alternatywnej tożsamości w celu uzyskania dostępu do subskrypcji
Dodanie alternatywnego konta do subskrypcji programu Visual Studio pozwala uzyskać dostęp do korzyści z subskrypcji, takich jak Azure DevOps i Azure, z inną tożsamością niż ta, do której jest przypisana subskrypcja. W przeszłości ta funkcja była dostępna tylko wtedy, gdy subskrypcja programu Visual Studio (VS) została przypisana do konta Microsoft (MSA). Ta funkcja została rozszerzona o konta służbowe w Azure Active Directory (Azure AD).  Aby uzyskać więcej informacji na temat korzystania z alternatywnych kont, zapoznaj się z artykułami dotyczącymi [tożsamości alternatywnych](vs-alternate-identity.md) . 

## <a name="frequently-asked-questions"></a>Często zadawane pytania
### <a name="q-how-can-i-contact-my-admin-about-this"></a>P: Jak mogę skontaktować się z administratorem?
Odp.: Aby uzyskać informacje na temat kontaktowania się z administratorem, zobacz nasz artykuł dotyczący [administratora subskrypcji](contact-my-admin.md) .  

## <a name="next-steps"></a>Następne kroki
Gdy administrator nawiąże połączenie z kontami usługi Azure AD i MSA, zalecamy zweryfikowanie, czy można pomyślnie zalogować się do [portalu subskrypcji](https://my.visualstudio.com?wt.mc_id=o~msft~docs) i uzyskać dostęp do korzyści, takich jak Azure DevOps, Visual Studio i Twoje indywidualne środki na korzystanie z platformy Azure DevTest. 