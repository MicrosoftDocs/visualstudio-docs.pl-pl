---
title: 'DA0001: Użyj StringBuilder do konkadacji | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0001
- vs.performance.rules.DAUseStringBuilder
- vs.performance.1
- vs.performance.rules.DA0001
ms.assetid: a7cc7613-ad5f-48c8-bd2b-56372cc12dfc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0d93de6ce901bfe4d72628f778b18420beb5ebee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779509"
---
# <a name="da0001-use-stringbuilder-for-concatenations"></a>DA0001: Używaj StringBuilder do łączenia

|||
|-|-|
|Identyfikator reguły|DA0001|
|Kategoria|Użycie programu .NET Framework|
|Metody profilowania|Próbkowanie<br /><br /> Oprzyrządowanie|
|Komunikat|Rozważ użycie StringBuilder dla konkadowań ciągów|
|Typ wiadomości|Ostrzeżenie|

## <a name="cause"></a>Przyczyna
 Wywołania System.String.Concat są znaczną część danych profilowania. Należy rozważyć <xref:System.Text.StringBuilder> użycie klasy do konstruowania ciągów z wielu segmentów.

## <a name="rule-description"></a>Opis reguły
 Obiekt <xref:System.String> jest niezmienny. W związku z tym wszelkie modyfikacje ciągu tworzy nowy obiekt ciągu i wyrzucania elementów bezużytecznych oryginału. To zachowanie jest takie samo, niezależnie od tego, czy wywołasz String.Concat jawnie lub użyjesz operatorów łączenia ciągów, takich jak + lub +=.. Wydajność programu może zmniejszyć, jeśli te metody są często wywoływane, na przykład gdy znaki są dodawane do ciągu w ciasnej pętli.

 Klasa StringBuilder jest obiektem modyfikowalnym i, w przeciwieństwie do System.String, większość metod na StringBuilder, które modyfikują wystąpienie tej klasy zwraca odwołanie do tego samego wystąpienia. Można wstawiać znaki lub dołączać tekst do wystąpienia StringBuilder oraz usuwać lub zamieniać znaki w wystąpieniu bez konieczności przydzielania nowego wystąpienia i usuwania oryginalnego wystąpienia.

## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie
 Kliknij dwukrotnie komunikat w oknie **Lista błędów,** aby przejść do [widoku szczegóły funkcji](../profiling/function-details-view.md) danych profilu próbkowania. Znajdź sekcje programu, które najczęściej korzystają z łączenia ciągów. Użyj StringBuilder klasy dla złożonych manipulacji ciągów, w tym częste operacje łączenia ciągów.

 Aby uzyskać więcej informacji na temat pracy z ciągami, sekcja [Operacje ciągu](/previous-versions/msp-n-p/ff647790(v=pandp.10)#string-operations) [rozdziału 5 — poprawa wydajności kodu zarządzanego](/previous-versions/msp-n-p/ff647790(v=pandp.10)) w bibliotece wzorców i praktyk firmy Microsoft.
