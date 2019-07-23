---
title: Zachowywanie anonimowości danych subskrybentów programu Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/19/2019
ms.topic: conceptual
description: Dowiedz się, jak anonimowe dane subskrybenta, gdy dostęp do subskrypcji zostanie utracony.
ms.openlocfilehash: 8ba1a462083281c2228f2d6e25c42485ead8aa19
ms.sourcegitcommit: 485881e6ba872c7b28a7b17ceaede845e5bea4fe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2019
ms.locfileid: "68377963"
---
# <a name="anonymization-of-visual-studio-subscriber-information"></a>Zachowywanie anonimowości informacji o subskrybencie programu Visual Studio
Gdy wystąpi zdarzenie, które blokuje użycie subskrypcji przez subskrybenta, takie jak wygaśnięcie subskrypcji lub usunięcie konta logowania subskrybenta, informacje osobiste użytkownika, takie jak nazwa i konto logowania, są zasadniczo szyfrowane w celu renderowania nie można ich używać.  Jest to gotowe do ochrony danych osobowych subskrybenta.

[!INCLUDE [GDPR-related guidance](includes/gdpr-intro-sentence.md)]

## <a name="when-does-anonymization-occur"></a>Kiedy występuje zachowywanie anonimowości?
Zdarzenia, które renderują subskrypcję niezdatną do użycia przez subskrybenta, będą wyzwalać zachowywanie anonimowości.  Szybkość występowania zachowywanie anonimowości zależy od typu subskrypcji i zdarzenia wyzwalania. Aby uzyskać więcej informacji, zobacz poniższą tabelę.

| Typ subskrypcji                                                                                                                       | Zdarzenie wyzwalające zachowywanie anonimowości                                                                                                     | Gdy wystąpi zachowywanie anonimowości |
|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|---------------------------|
| Visual Studio Dev Essentials                                                                                                            | Subskrybenci z programem lub nie akceptują warunków użytkowania                                    | 30 dni               |
| Subskrypcje programu Visual Studio zakupione w ramach Microsoft Store (sprzedaż detaliczna)                                                                      | Subskrypcja wygaśnie lub nie została aktywowana                                                                   | 360 dni                  |
| Subskrypcje programu Visual Studio nabyte w ramach licencji zbiorczej, Visual Studio Marketplace (subskrypcje w chmurze) lub programy takie jak MPN | Subskrypcja wygasa lub nie jest przypisana do użytkownika                                                          | 180 dni                  |
| Wszystkie subskrypcje                                                                                                                       | Konto Azure Active Directory lub konto Microsoft (MSA) użyte do zalogowania się do subskrypcji jest zamknięte | Niezwłocznie               |
| Wszystkie subskrypcje                                                                                                                       | Subskrybent jest usuwany z dzierżawy skojarzonej z kontem Azure Active Directory                                | Niezwłocznie               |

## <a name="faq"></a>Najczęściej zadawane pytania
### <a name="q--does-the-anonymization-of-the-subscribers-personal-information-cause-them-to-lose-access-to-the-subscription"></a>PYTANIA  Czy zachowywanie anonimowości informacji osobistych subskrybenta spowoduje utratę dostępu do subskrypcji?
Odp.:  Nie.  Zachowywanie anonimowości jest w odpowiedzi na zdarzenie, które powoduje utratę dostępu do subskrypcji, ale nie powoduje braku dostępu.

### <a name="q--im-an-administrator-for-my-organizations-subscriptions--if-one-of-my-subscribers-information-is-anonymized-can-that-subscription-be-reassigned-to-another-user"></a>PYTANIA  Jestem administratorem dla subskrypcji mojej organizacji.  Jeśli jedna z informacji na subskrybencie to anonimowe, czy można ponownie przypisać subskrypcję do innego użytkownika?
Odp.:  Tak — o ile subskrypcja nie wygasła, może zostać ponownie przypisana do innego subskrybenta.

## <a name="next-steps"></a>Następne kroki
Dowiedz się, jak zapobiegać zachowywanie anonimowości przez [łączenie tożsamości usługi MSA i usługi AAD](/azure/active-directory/b2b/add-users-administrator).
