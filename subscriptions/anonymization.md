---
title: Zachowywanie anonimowości danych subskrybentów programu Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 02/20/2020
ms.topic: conceptual
description: Dowiedz się, jak anonimowe dane subskrybenta, gdy dostęp do subskrypcji zostanie utracony.
ms.openlocfilehash: f3a35448dd0befbbb91f1657dd62b2b99ff37a2a
ms.sourcegitcommit: 3c105990656cd509062ce60e52e776c794f6305d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77520842"
---
# <a name="anonymization-of-visual-studio-subscriber-information"></a>Zachowywanie anonimowości informacji o subskrybencie programu Visual Studio
Gdy wystąpi zdarzenie, które blokuje użycie subskrypcji przez subskrybenta, takie jak wygaśnięcie subskrypcji lub usunięcie konta logowania subskrybenta, informacje osobiste użytkownika, takie jak nazwa i konto logowania, są zasadniczo szyfrowane w celu renderowania nie można ich używać.  Jest to gotowe do ochrony danych osobowych subskrybenta.

[!INCLUDE [GDPR-related guidance](includes/gdpr-intro-sentence.md)]

## <a name="when-does-anonymization-occur"></a>Kiedy występuje zachowywanie anonimowości?
Zdarzenia, które renderują subskrypcję niezdatną do użycia przez subskrybenta, będą wyzwalać zachowywanie anonimowości.  Szybkość występowania zachowywanie anonimowości zależy od typu subskrypcji i zdarzenia wyzwalania. Więcej informacji można znaleźć w tabeli poniżej.

| Typ subskrypcji                                                                                                                       | Zdarzenie wyzwalające zachowywanie anonimowości                                                                                                     | Gdy wystąpi zachowywanie anonimowości |
|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|---------------------------|
| Visual Studio Dev Essentials                                                                                                            | Subskrybenci z programem lub nie akceptują warunków użytkowania                                    | 30 dni               |
| Subskrypcje programu Visual Studio zakupione w ramach Microsoft Store (sprzedaż detaliczna)                                                                      | Subskrypcja wygaśnie lub nie została aktywowana                                                                   | 360 dni                  |
| Subskrypcje programu Visual Studio nabyte w ramach licencji zbiorczej, Visual Studio Marketplace (subskrypcje w chmurze) lub programy takie jak MPN | Subskrypcja wygasa lub nie jest przypisana do użytkownika                                                          | 180 dni                  |
| Wszystkie subskrypcje                                                                                                                       | Konto Azure Active Directory lub konto Microsoft (MSA) użyte do zalogowania się do subskrypcji jest zamknięte | Niezwłocznie               |
| Wszystkie subskrypcje                                                                                                                       | Subskrybent jest usuwany z dzierżawy skojarzonej z kontem Azure Active Directory                                | Niezwłocznie               |

## <a name="faq"></a>Często zadawane pytania
### <a name="q--does-the-anonymization-of-the-subscribers-personal-information-cause-them-to-lose-access-to-the-subscription"></a>P: czy zachowywanie anonimowości informacji osobistych subskrybenta powoduje utratę dostępu do subskrypcji?
Odp.: nie.  Zachowywanie anonimowości jest w odpowiedzi na zdarzenie, które powoduje utratę dostępu do subskrypcji, ale nie powoduje braku dostępu.

### <a name="q--im-an-administrator-for-my-organizations-subscriptions--if-one-of-my-subscribers-information-is-anonymized-can-that-subscription-be-reassigned-to-another-user"></a>P: jestem administratorem dla subskrypcji mojej organizacji.  Jeśli jedna z informacji na subskrybencie to anonimowe, czy można ponownie przypisać subskrypcję do innego użytkownika?
Odp.: tak — o ile subskrypcja nie wygasła, może zostać ponownie przypisana do innego subskrybenta.

### <a name="q-how-can-i-prevent-anonymization-caused-by-deleting-a-sign-in-email-address"></a>P: Jak mogę zapobiec zachowywanie anonimowości spowodowane przez usunięcie adresu e-mail logowania?
Odp.: Istnieją dwa sposoby na uniknięcie problemu:
- Wdróż pojedynczy system zarządzania tożsamościami — MSA lub AAD--, ale nie oba.  
- Skojarz tożsamości usługi AAD i MSA za pośrednictwem dzierżawy. 

## <a name="next-steps"></a>Następne kroki
Dowiedz się, jak zapobiegać zachowywanie anonimowości przez [kojarzenie tożsamości usługi MSA i usługi AAD](https://docs.microsoft.com/azure/active-directory/b2b/add-users-administrator).

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja Microsoft 365](https://docs.microsoft.com/microsoft-365/)
