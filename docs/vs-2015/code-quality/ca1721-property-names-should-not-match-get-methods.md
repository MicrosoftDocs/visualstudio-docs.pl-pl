---
title: 'CA1721: Nazwy właściwości nie powinny odpowiadać metody get | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 94d120a7656fc9270543ceeb57063124764c4bca
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431197"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: Nazwy właściwości nie powinny być takie same jak nazwy metod Get
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Nazwa publicznego lub chronionego elementu członkowskiego zaczyna się od "Get" i odpowiada nazwie właściwości publicznej lub chronionej. Na przykład typ, który zawiera metodę o nazwie "Getcolor —" i właściwość, która nosi nazwę "Color" narusza tę regułę.

## <a name="rule-description"></a>Opis reguły
 Metody GET i właściwości powinny mieć nazwy, które wyraźnie odróżniają ich funkcje.

 Konwencje nazewnictwa Obejmij wygląd wspólnych bibliotek obiektu docelowego środowiska uruchomieniowego języka wspólnego. Zmniejsza to czas, który jest wymagany, aby dowiedzieć się nowa Biblioteka oprogramowania i zwiększa poziom zaufania klientów, że biblioteka został opracowany przez osobę, która ma doświadczenie w tworzenie kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zmień nazwę, tak aby nazwę metody, która jest poprzedzony znakiem "Get" nie pasuje.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

> [!NOTE]
> To ostrzeżenie, mogą zostać wyłączone, jeśli metoda Get jest spowodowany przez zaimplementowanie interfejsu iextenderprovider —.

## <a name="example"></a>Przykład
 Poniższy przykład zawiera metody i właściwości, które spełniają tej reguły.

 [!code-csharp[FxCop.Naming.GetMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/cs/FxCop.Naming.GetMethod.cs#1)]
 [!code-vb[FxCop.Naming.GetMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/vb/FxCop.Naming.GetMethod.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1024: Korzystanie z właściwości, gdzie jest to odpowiednie](../code-quality/ca1024-use-properties-where-appropriate.md)
