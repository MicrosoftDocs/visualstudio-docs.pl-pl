---
title: Anonimizacja danych subskrybenta programu Visual Studio | Dokumenty firmy Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.date: 02/20/2020
ms.topic: conceptual
description: Dowiedz się, jak dane subskrybenta są anonimizowane po utracie dostępu do subskrypcji.
ms.openlocfilehash: 439e53b1c67fde0fbda0666652e29bf396abfee2
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "78894416"
---
# <a name="anonymization-of-visual-studio-subscriber-information"></a>Anonimizacja informacji o subskrybentach programu Visual Studio
W przypadku wystąpienia zdarzenia, które blokuje korzystanie przez subskrybenta z subskrypcji, takiego jak wygaśnięcie subskrypcji lub usunięcie konta logowania subskrybenta, dane osobowe użytkownika, takie jak nazwa i konto logowania, są zasadniczo kodowane w celu renderowania nie nadają się do ich użyteczności.  Ma to na celu zabezpieczenie danych osobowych subskrybenta.

[!INCLUDE [GDPR-related guidance](includes/gdpr-intro-sentence.md)]

## <a name="when-does-anonymization-occur"></a>Kiedy występuje anonimizacja?
Zdarzenia, które powodują, że subskrypcja nie jest użyteczna dla subskrybenta, wyzwolą anonimizację.  Jak szybko występuje anonimizacja zależy od typu subskrypcji i zdarzenia wyzwalającego. Więcej informacji można znaleźć w tabeli poniżej.

| Typ subskrypcji                                                                                                                       | Zdarzenie wyzwalające anonimizację                                                                                                     | W przypadku wystąpienia anonimizacji |
|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|---------------------------|
| Visual Studio Dev Essentials                                                                                                            | Subskrybent rezygnuje z programu lub nie akceptuje warunków użytkowania                                    | 30 dni               |
| Subskrypcje programu Visual Studio zakupione za pośrednictwem sklepu Microsoft Store (handel detaliczny)                                                                      | Subskrypcja wygasa lub nie jest aktywowana                                                                   | 360 dni                  |
| Subskrypcje programu Visual Studio nabyte za pośrednictwem licencji zbiorczej, programu Visual Studio Marketplace (subskrypcje w chmurze) lub programów, takich jak MPN | Subskrypcja wygasa lub nie jest przypisana do użytkownika                                                          | 180 dni                  |
| Wszystkie subskrypcje                                                                                                                       | Konto usługi Azure Active Directory lub konto Microsoft (MSA) używane do logowania się do subskrypcji jest zamknięte | Natychmiast               |
| Wszystkie subskrypcje                                                                                                                       | Subskrybent jest usuwany z dzierżawy skojarzonej z kontem usługi Azure Active Directory                                | Natychmiast               |

## <a name="faq"></a>Często zadawane pytania
### <a name="q--does-the-anonymization-of-the-subscribers-personal-information-cause-them-to-lose-access-to-the-subscription"></a>Pyt.: Czy anonimizacja danych osobowych subskrybenta powoduje, że utraci on dostęp do subskrypcji?
Odp.: Nie.  Anonimizacja jest odpowiedzią na zdarzenie, które powoduje utratę dostępu do subskrypcji, ale nie powoduje braku dostępu.

### <a name="q--im-an-administrator-for-my-organizations-subscriptions--if-one-of-my-subscribers-information-is-anonymized-can-that-subscription-be-reassigned-to-another-user"></a>P: Jestem administratorem subskrypcji mojej organizacji.  Jeśli jedna z informacji mojego subskrybenta jest anonimowa, czy subskrypcja ta może zostać ponownie przypisana do innego użytkownika?
Odp.: Tak — dopóki subskrypcja nie wygasła, można ją ponownie przypisać do innego subskrybenta.

### <a name="q-how-can-i-prevent-anonymization-caused-by-deleting-a-sign-in-email-address"></a>Pyt.: Jak mogę zapobiec anonimizacji spowodowanej usunięciem adresu e-mail logowania?
Odp.: Istnieją dwa sposoby zapobiegania problemowi:
- Wdrażanie jednego systemu zarządzania tożsamościami — MSA lub AAD — ale nie obu.  
- Skojarz tożsamości usługi AAD i MSA za pośrednictwem dzierżawy. 

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja usługi Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
Dowiedz się, jak zapobiegać anonimizacji, [kojarząc tożsamości MSA i AAD.](https://docs.microsoft.com/azure/active-directory/b2b/add-users-administrator)


