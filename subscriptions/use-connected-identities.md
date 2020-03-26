---
title: Jak używać połączonych kont Microsoft i tożsamości usługi Azure Active Directory | Dokumenty firmy Microsoft
author: evanwindom
ms.author: v-evwin
manager: lank
ms.assetid: 50ce0445-ef1a-4e92-b9d0-aebb2155a111
ms.date: 03/11/2020
ms.topic: conceptual
robots: noindex, nofollow
description: Dowiedz się, jak pracować z połączonymi kontami Microsoft i tożsamościami usługi Azure Active Directory
ms.openlocfilehash: b88c978f330520af62f51e372db93475b71caa36
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233172"
---
# <a name="how-to-use-connected-identities-in-visual-studio-subscriptions"></a>Jak używać połączonych tożsamości w subskrypcjach programu Visual Studio
Jeśli otrzymasz subskrypcję programu Visual Studio za pośrednictwem swojej pracy lub szkoły, a do zalogowania się użyjesz swojego konta Microsoft (MSA), administrator subskrypcji może połączyć usługę MSA z twoją tożsamością w usłudze Azure Active Directory (Azure AD) w organizacji.  Spowoduje to zmianę sposobu uzyskiwania dostępu do niektórych korzyści zawartych w subskrypcji. 

## <a name="overview-of-connected-ids"></a>Omówienie podłączonych identyfikatorów
Organizacje coraz częściej przenoszą się na tożsamości oparte na usłudze Azure AD, aby zapewnić lepsze zabezpieczenia i obsługę automatycznego zarządzania subskrypcjami.  Jeśli subskrypcja używa msa, @outlook.com takich jak lub inny osobisty adres e-mail, administrator może zmienić e-mail logowania do tożsamości usługi Azure AD.  Spowoduje to zmianę sposobu logowania się do https://my.visualstudio.com portalu subskrybenta, ale nie może zmienić sposobu dostępu do wszystkich korzyści.  

Jeśli administrator łączy tożsamości MSA i usługi Azure AD, otrzymasz wiadomość e-mail z informacją, aby rozpocząć dostęp do subskrypcji programu Visual Studio z tożsamością usługi Azure AD zamiast msa. 

## <a name="how-to-access-benefits-using-azure-ad-identities"></a>Jak uzyskać dostęp do korzyści przy użyciu tożsamości usługi Azure AD
Po połączonej przez administratora usługi MSA z tożsamością usługi Azure AD https://my.visualstudio.com musisz zalogować się do portalu subskrybenta przy stanie tożsamości usługi Azure AD, aby uzyskać dostęp do korzyści opartych na usłudze Azure AD.  Należą do nich:
- Visual Studio IDE
- Azure DevOps
- Indywidualne środki na korzystanie z usługi Azure DevTest

## <a name="how-to-access-benefits-using-your-msa"></a>Jak uzyskać dostęp do korzyści za pomocą msa
Dla wielu korzyści oferowanych w usłudze Visual Studio subskrypcji, takich jak Pluralsight, LinkedIn, CloudPilot i innych, faktycznie utworzyć konta użytkowników w witrynach sieci web partnerów.  W przypadku tych kont należy nadal używać tożsamości używanej podczas tworzenia konta.  Na przykład jeśli aktywowano korzyści Pluralsight przy użyciu msa, należy nadal używać msa podczas korzystania z szkolenia Pluralsight, niezależnie od tożsamości używane do logowania się do portalu subskrybenta.  

## <a name="use-an-alternate-identity-to-access-your-subscription"></a>Dostęp do subskrypcji za pomocą alternatywnej tożsamości
Dodanie konta alternatywnego do subskrypcji programu Visual Studio umożliwia dostęp do korzyści subskrypcji, takich jak Azure DevOps i Azure, z inną tożsamością niż ta, do której jest przypisana subskrypcja. W przeszłości ta funkcja była dostępna tylko wtedy, gdy subskrypcja programu Visual Studio (VS) została przypisana do konta Microsoft (MSA). Rozszerzyliśmy tę funkcję dla kont służbowych w usłudze Azure Active Directory (Azure AD).  Aby uzyskać więcej informacji na temat korzystania z kont alternatywnych, zapoznaj się z naszym [artykułem Alternatywne tożsamości.](vs-alternate-identity.md) 

## <a name="frequently-asked-questions"></a>Często zadawane pytania
### <a name="q-how-can-i-contact-my-admin-about-this"></a>P: Jak mogę skontaktować się z moim administratorem w tej sprawie?
O: Aby uzyskać informacje na temat kontaktowania się z administratorem, zapoznaj się z artykułem Skontaktuj się z [administratorem subskrypcji.](contact-my-admin.md)  

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja usługi Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
Gdy administrator połączy konta usługi Azure AD i MSA, zalecamy sprawdzenie, czy można pomyślnie zalogować się do [portalu subskrypcji](https://my.visualstudio.com?wt.mc_id=o~msft~docs) i uzyskać dostęp do korzyści, takich jak Azure DevOps, Visual Studio i indywidualne środki azure devtest. 