---
title: 'CA2109: Przejrzyj widoczne procedury obsługi zdarzeń | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3ddcab6e0f416837bcd7b01521a6d77ddce691b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520981"
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109: Przejrzyj widoczne procedury obsługi zdarzeń
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|ReviewVisibleEventHandlers|
|CheckId|CA2109|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Wykryto publiczną lub chronioną metodę obsługi zdarzeń.

## <a name="rule-description"></a>Opis reguły
 Widoczna na zewnątrz metoda obsługi zdarzeń przedstawia problem z zabezpieczeniami, który wymaga przeglądu.

 Metody obsługi zdarzeń nie powinny być udostępnione, chyba że jest to absolutnie konieczne. Procedura obsługi zdarzeń, typ delegata, który wywołuje uwidocznioną metodę, można dodać do dowolnego zdarzenia, o ile program obsługi i podpisy zdarzeń pasują do siebie. Zdarzenia mogą być potencjalnie wywoływane przez dowolny kod i są często wywoływane przez wysoce zaufany kod systemowy w odpowiedzi na akcje użytkownika, takie jak kliknięcie przycisku. Dodanie kontroli zabezpieczeń do metody obsługi zdarzeń nie zapobiega zarejestrowaniu przez kod procedury obsługi zdarzeń, która wywołuje metodę.

 Żądanie nie może mieć niezawodnej ochrony metody wywoływanej przez program obsługi zdarzeń. Wymagania dotyczące zabezpieczeń pomagają chronić kod przed niezaufanymi wywołaniami poprzez badanie wywołań w stosie wywołań. Kod, który dodaje procedurę obsługi zdarzeń do zdarzenia, nie musi być obecny na stosie wywołań, gdy są uruchamiane metody obsługi zdarzeń. W związku z tym stos wywołań może mieć tylko wysoce zaufanych wywołujących, gdy wywoływana jest metoda obsługi zdarzeń. Powoduje to, że wymagania wykonywane przez metodę obsługi zdarzeń powiodło się. Ponadto w przypadku wywołania metody żądanie może zostać potwierdzone. Z tego powodu ryzyko naprawienia naruszenia tej reguły można ocenić dopiero po przejrzeniu metody obsługi zdarzeń. Podczas przeglądania kodu należy wziąć pod uwagę następujące zagadnienia:

- Czy program obsługi zdarzeń wykonuje wszystkie operacje, które są niebezpieczne lub możliwe do wykorzystania, takie jak potwierdzenia uprawnień lub pominięcie uprawnienia do kodu niezarządzanego?

- Jakie są zagrożenia bezpieczeństwa i z kodu, ponieważ mogą być uruchamiane w dowolnym momencie z tylko wysoce zaufanymi wywołaniami na stosie?

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, przejrzyj metodę i Oceń następujące elementy:

- Czy można utworzyć metodę obsługi zdarzeń niepubliczną?

- Czy można przenieść wszystkie niebezpieczne funkcje z programu obsługi zdarzeń?

- Czy w przypadku nałożenia żądania zabezpieczeń można to zrobić w inny sposób?

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń ostrzeżenie z tej reguły tylko po dokładnym przeglądzie zabezpieczeń, aby upewnić się, że kod nie stanowi zagrożenia dla bezpieczeństwa.

## <a name="example"></a>Przykład
 Poniższy kod przedstawia metodę obsługi zdarzeń, która może być używana przez złośliwy kod.

 [!code-csharp[FxCop.Security.EventSecLib#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.EventSecLib/cs/FxCop.Security.EventSecLib.cs#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> <xref:System.EventArgs?displayProperty=fullName>
 [Wymagania dotyczące zabezpieczeń](https://msdn.microsoft.com/324c14f8-54ff-494d-9fd1-bfd20962c8ba)
