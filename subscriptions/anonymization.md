---
title: Anonimowości danych subskrybenta programu Visual Studio | Dokumentacja firmy Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.date: 10/31/2018
ms.topic: conceptual
description: Dowiedz się, jak są anonimowe dane subskrybentów, gdy dostęp do subskrypcji zostaną utracone.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 4570ff43f946c25c50d298e22de3b0c8a261f870
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810589"
---
# <a name="anonymization-of-visual-studio-subscriber-information"></a>Anonimowości danych subskrybenta programu Visual Studio

Gdy wystąpi zdarzenie, które blokuje subskrybenta korzystanie z subskrypcji, takie jak czas wygaśnięcia subskrypcji lub usunięcie subskrybenta konto logowania, informacje osobiste użytkownika, takie jak nazwa i konto logowania są zasadniczo zaszyfrowane do renderowania ich uniemożliwiającym jego używanie.  To jest ochrona informacji osobistych subskrybenta.

[!INCLUDE [GDPR-related guidance](includes/gdpr-intro-sentence.md)]

## <a name="when-does-anonymization-occur"></a>Kiedy zostanie przeprowadzona anonimizacji

Zdarzenia, które uszkodzić subskrypcja na subskrybencie wyzwoli anonimizacji.  Jak szybko odbywa się anonimizacji, zależy od typu subskrypcji i wyzwalającą zdarzenie. Zobacz tabelę poniżej, aby uzyskać więcej informacji.

| Typ subskrypcji                                                                                                                       | Zdarzenia wyzwalającego anonimizacji                                                                                                     | Gdy wystąpi anonimizacji |
|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|---------------------------|
| Visual Studio Dev Essentials                                                                                                            | Subskrybent oznacza brak program zgody lub nie akceptuje warunki użytkowania                                    | 30 dni               |
| Subskrypcje programu Visual Studio zostały zakupione w ramach Microsoft Store (sprzedaż detaliczna)                                                                      | Subskrypcja wygaśnie lub nie została aktywowana                                                                   | 360 dni                  |
| Subskrypcje programu Visual Studio zakupione w ramach licencjonowania zbiorowego, Visual Studio Marketplace (subskrypcje w chmurze) lub programów, takich jak MPN | Subskrypcja wygaśnie lub nie jest przypisany do użytkownika                                                          | 180 dni                  |
| Wszystkie subskrypcje                                                                                                                       | Konto usługi Azure Active Directory lub konta Microsoft (MSA) używane do logowania się do subskrypcji jest zamknięty. | Natychmiast               |
| Wszystkie subskrypcje                                                                                                                       | Subskrybent zostanie usunięty z dzierżawą, która jest skojarzona z kontem usługi Azure Active Directory                                | Natychmiast               |

## <a name="faq"></a>Najczęściej zadawane pytania

### <a name="q--does-the-anonymization-of-the-subscribers-personal-information-cause-them-to-lose-access-to-the-subscription"></a>Pytanie: czy anonimowości danych osobowych subskrybenta mogą spowodować utratę dostępu do subskrypcji?
Odpowiedź: nie.  Anonimowości znajduje się w odpowiedzi na zdarzenie, które powoduje utratę dostępu do subskrypcji, ale nie spowoduje brak dostępu.

### <a name="q--im-an-administrator-for-my-organizations-subscriptions--if-one-of-my-subscribers-information-is-anonymized-can-that-subscription-be-reassigned-to-another-user"></a>P: jestem administratorem subskrypcji w mojej organizacji.  Jeśli jeden z moich subskrybentów informacje są anonimowe, tej subskrypcji można ponownie przypisać do innego użytkownika?
Odp. tak--tak długo, jak subskrypcja nie wygasła, jego może zostać przypisany do innego subskrybenta.

## <a name="next-steps"></a>Następne kroki

Dowiedz się, jak zapobiegać anonimowości przez [łączenie tożsamości MSA i AAD](/azure/active-directory/b2b/add-users-administrator).
