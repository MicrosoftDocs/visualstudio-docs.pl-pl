---
title: 'DA0007: Unikaj używania wyjątków do przepływu sterowania | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAExceptionsThrown
- vs.performance.7
- vs.performance.rules.DA0007
- vs.performance.DA0007
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7ae7b890e12d56e61571ecbf72dc1b0cd39567a4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53898206"
---
# <a name="da0007-avoid-using-exceptions-for-control-flow"></a>DA0007: Unikaj używania wyjątków do przepływu sterowania

|||  
|-|-|  
|Identyfikator reguły|DA0007|  
|Kategoria|Sposób użycia programu .NET framework|  
|Metod profilowania|Wszystkie|  
|Komunikat|Stale jest zgłaszana wysoka liczba wyjątków. Należy rozważyć ograniczenie użycia wyjątków w logice programu.|  
|Typ komunikatu|Ostrzeżenie|  

 Podczas profilowania za pomocą próbkowania pamięci platformy .NET i metod rywalizacji zasobów musi zebrać co najmniej 25 próbek do wyzwolenia tej reguły.  

## <a name="cause"></a>Przyczyna  
 Wysoki współczynnik obsługi wyjątków w .NET Framework zostały wywołane w danych profilowania. Należy rozważyć użycie inną logikę przepływu sterowania w celu zmniejszenia liczby wyjątków, które są generowane.  

## <a name="rule-description"></a>Opis reguły  
 Korzystanie z obsługi wyjątków w celu przechwytywania błędów i innych zdarzeń, które zakłócają działanie programu jest dobrym rozwiązaniem, korzystanie z obsługi wyjątków jako część logiki wykonywania regularnych program może być kosztowne i należy ich unikać. W większości przypadków wyjątki należy używać tylko w przypadku okoliczności, które występują rzadko i nie oczekuje. Wyjątki nie stosuje się do zwracania wartości jako część przepływu typowego programu. W wielu przypadkach można uniknąć zgłaszania wyjątków, sprawdzanie poprawności wartości i przy użyciu logikę warunkową w celu wstrzymania wykonywania instrukcji, które powodują problemu.  

 Aby uzyskać więcej informacji, zobacz [Zarządzanie wyjątkami](http://go.microsoft.com/fwlink/?LinkID=177825) części **rozdział 5 — poprawę wydajności kodu zarządzanego** w **poprawy wydajności aplikacji platformy .NET i skalowalności** ilości **Microsoft Patterns and Practices** biblioteki w witrynie MSDN.  

## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, przejdź do widoku znaczników. Znajdź kolumnę, która zawiera **wyjątki .NET CLR (@ProcessInstance)\\liczba Excels zgłoszony / sec** pomiarów. Określa, czy określone faz wykonywania programu obsługi wyjątków w przypadku częściej niż inne. Przy użyciu profilu pobierania próbek, spróbuj zidentyfikować instrukcji throw i bloki, które generują występujących wyjątków try/catch. Jeśli to konieczne, należy dodać logikę do bloki, które pomagają zrozumieć, które wyjątki, które są aktualnie obsługiwane najczęściej catch. W przypadku, gdy jest to możliwe, Zastąp często wykonywane throw instrukcje lub bloki catch prosty przepływ kontrolować kod logiki i walidacji.  

 Na przykład gdyby się okazać, że aplikacji została obsługa występujących wyjątków dividebyzeroexception —, dodając logikę do programu, aby sprawdzić, czy mianownikach z wartościami zerowymi zwiększa wydajność aplikacji.