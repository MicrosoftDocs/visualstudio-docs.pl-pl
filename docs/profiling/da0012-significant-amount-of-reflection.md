---
title: 'DA0012: Znacząca ilość odbicia | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0011
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33617b71c8ba13c459df8bcf29fb8a51cf948299
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62936460"
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012: Znaczne odbicie

|||
|-|-|
|Identyfikator reguły|DA0012|
|Kategoria|Sposób użycia programu .NET framework|
|Metod profilowania|Próbkowania|
|Komunikat|Użytkownik może być nadmiernie używasz odbicia. Jest kosztowną operacją.|
|Typ reguły|Ostrzeżenie|

## <a name="cause"></a>Przyczyna
 Wywołania do metody System.Reflection, takie jak element InvokeMember i GetMember lub typ metod, takich jak MemberInvoke są znaczna część danych profilowania. Jeśli to możliwe, należy wziąć pod uwagę zastąpienie tych metod wczesne powiązania do metod zestawów zależnych.

## <a name="rule-description"></a>Opis reguły
 Odbicie jest elastyczne możliwości programu .NET Framework, który może służyć do wykonywania późne powiązania aplikacji zależnego zestawu środowiska wykonawczego, albo do tworzenia i dynamicznie wykonywanie nowych typów w czasie wykonywania. Jednak te techniki może obniżyć wydajność, jeśli są one często używane lub o nazwie w ścisłą pętli.

 Aby uzyskać więcej informacji, zobacz [odbicia, a późne wiązanie](http://go.microsoft.com/fwlink/?LinkId=177826) sekcji rozdział 5 — poprawianie zarządzane działania kodu, zbiorczo poprawy wydajności aplikacji platformy .NET i skalowalność Microsoft Patterns and Practices Biblioteka w witrynie MSDN.

## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widok szczegółów funkcji](../profiling/function-details-view.md) danych profilowania. Zbadaj funkcje wywoływania metody System.Type lub System.Reflection można odnaleźć sekcji programów Najczęściej korzystanie z interfejsów API odbicia platformy .NET. Należy unikać używania metod, które zwracają metadanych. Wydajność aplikacji ma kluczowe znaczenie, należy unikać używania i późne wiązanie dynamiczne tworzenie typów w czasie wykonywania.