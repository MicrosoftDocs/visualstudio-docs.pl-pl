---
title: W obszarze Omówienie pomijania źródła | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 63d405b0e62735c0c1e3d7bb716ea2db29bc19fe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651573"
---
# <a name="in-source-suppression-overview"></a>Ograniczanie w kodzie źródłowym - Omówienie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomijanie w źródle to możliwość pomijania lub ignorowania naruszeń analizy kodu w kodzie zarządzanym przez dodanie atrybutu **SuppressMessage** do segmentów kodu, które powodują naruszenia. Atrybut **SuppressMessage** jest atrybutem warunkowym, który jest zawarty w metadanych Il zestawu kodu zarządzanego tylko wtedy, gdy symbol kompilacji CODE_ANALYSIS jest zdefiniowany w czasie kompilacji.

 W C++programie/CLI Użyj makr CA_SUPPRESS_MESSAGE lub CA_GLOBAL_SUPPRESS_MESSAGE w pliku nagłówkowym, aby dodać atrybut.

 Nie należy używać pominięć ze źródła w kompilacjach wydania, aby zapobiec przypadkowemu wysłaniu metadanych pomijania w źródle. Ze względu na koszt przetwarzania w przypadku pomijania w źródle wydajność aplikacji może być również obniżona poprzez dołączenie metadanych pomijania w źródle.

> [!NOTE]
> Nie ma potrzeby ręcznego kodu tych atrybutów. Aby uzyskać więcej informacji, zobacz [How to: pomijanie ostrzeżeń przy użyciu elementu menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md). Element menu nie jest dostępny dla C++ kodu.

## <a name="suppressmessage-attribute"></a>SuppressMessage — atrybut
 Po kliknięciu prawym przyciskiem myszy ostrzeżenia analizy kodu w **Lista błędów** , a następnie kliknięciu opcji **Pomiń komunikaty**, atrybut **SuppressMessage** jest dodawany w kodzie lub do globalnego pliku pominięć tego projektu.

 Atrybut **SuppressMessage** ma następujący format:

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]

```

 [C++]

```
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")

```

 Gdzie:

- **Kategoria reguły** — Kategoria, w której zdefiniowana jest reguła. Aby uzyskać więcej informacji na temat kategorii reguł analizy kodu, zobacz [Analiza kodu dla ostrzeżeń związanych z kodem zarządzanym](../code-quality/code-analysis-for-managed-code-warnings.md).

- **Identyfikator reguły** — Identyfikator reguły. Obsługa obejmuje krótką i długą nazwę identyfikatora reguły. Krótka nazwa to CAXXXX; długa nazwa to CAXXXX: FriendlyTypeName.

- **Uzasadnienie** — tekst, który jest używany do dokumentowania przyczyny pomijania wiadomości.

- **Identyfikator komunikatu** — unikatowy identyfikator problemu dla każdego komunikatu.

- **Zakres** — element docelowy, na którym jest pomijane ostrzeżenie. Jeśli obiekt docelowy nie jest określony, zostanie ustawiony na obiekt docelowy atrybutu. Obsługiwane są następujące zakresy:

  - Moduł

  - Przestrzeń nazw

  - Zasób

  - Typ

  - Element członkowski

- **Target** — identyfikator, który jest używany do określenia elementu docelowego, na którym jest pomijane ostrzeżenie. Musi zawierać w pełni kwalifikowaną nazwę elementu.

## <a name="suppressmessage-usage"></a>SuppressMessage użycie
 Ostrzeżenia analizy kodu są pomijane na poziomie, do którego zastosowano wystąpienie atrybutu **SuppressMessage** . Celem jest ścisłe sprzęganie informacji o pominięciu do kodu, w którym występuje naruszenie.

 Ogólna forma pomijania obejmuje kategorię reguły i Identyfikator reguły, która zawiera opcjonalną, czytelną dla człowieka reprezentację nazwy reguły. Na przykład

 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

 Jeśli istnieją ścisłe przyczyny dotyczące minimalizowania metadanych pomijania w źródle, sama nazwa reguły może zostać pozostawiona. Kategoria reguł i jej Identyfikator reguły składają się na wystarczająco unikatowy identyfikator reguły. Na przykład

 `[SuppressMessage("Microsoft.Design", "CA1039")]`

 Ten format nie jest zalecany ze względu na problemy z konserwacją.

## <a name="suppressing-multiple-violations-within-a-method-body"></a>Pomijanie wielu naruszeń w treści metody
 Atrybuty mogą być stosowane tylko do metody i nie mogą być osadzone w treści metody. Można jednak określić identyfikator jako identyfikator wiadomości, aby rozróżnić wiele wystąpień naruszenia w ramach metody.

 [!code-cpp[InSourceSuppression#1](../snippets/cpp/VS_Snippets_CodeAnalysis/InSourceSuppression/cpp/insourcesuppression.cpp#1)]
 [!code-csharp[InSourceSuppression#1](../snippets/csharp/VS_Snippets_CodeAnalysis/InSourceSuppression/cs/InSourceSuppression.cs#1)]
 [!code-vb[InSourceSuppression#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/InSourceSuppression/vb/InSourceSuppression.vb#1)]

## <a name="generated-code"></a>Wygenerowany kod
 Kompilatory kodu zarządzanego i narzędzia innych firm generują kod, aby ułatwić szybkie tworzenie kodu. Kod wygenerowany przez kompilator, który pojawia się w plikach źródłowych jest zwykle oznaczony przy użyciu atrybutu **GeneratedCodeAttribute** .

 Można wybrać, czy pomijać ostrzeżenia i błędy analizy kodu dla wygenerowanego kodu. Aby uzyskać informacje na temat sposobu pomijania takich ostrzeżeń i błędów, zobacz [How to: pomijanie ostrzeżeń dla wygenerowanego kodu](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

 Należy zauważyć, że analiza kodu ignoruje **GeneratedCodeAttribute** , gdy jest stosowana do całego zestawu lub jednego parametru. Te sytuacje występują rzadko.

## <a name="global-level-suppressions"></a>Pominięcia na poziomie globalnym
 Narzędzie do analizy kodu zarządzanego sprawdza atrybuty **SuppressMessage** stosowane na poziomie zestawu, modułu, typu, elementu członkowskiego lub parametru. Wyzwala również naruszenia zasobów i przestrzeni nazw. Te naruszenia muszą być stosowane na poziomie globalnym i są objęte zakresem i elementem przeznaczonym dla siebie. Na przykład następujący komunikat pomija naruszenie przestrzeni nazw:

 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> W przypadku pomijania ostrzeżenia z zakresem przestrzeni nazw pomija ostrzeżenie do samego obszaru nazw. Nie powoduje pomijania ostrzeżenia o typach w przestrzeni nazw.

 Wszystkie pomijanie można wyrazić, określając jawny zakres. Te pominięcia muszą się znajdować na poziomie globalnym. Nie można określić pomijania na poziomie elementu członkowskiego, dekorowania nazwy typ.

 Pomijanie na poziomie globalnym jest jedynym sposobem, aby pominąć komunikaty odwołujące się do kodu generowanego przez kompilator, który nie jest mapowany do jawnie dostarczonego źródła użytkownika. Na przykład poniższy kod pomija naruszenie dla konstruktora emitującego kompilator:

 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> Element docelowy zawsze zawiera w pełni kwalifikowaną nazwę elementu.

## <a name="global-suppression-file"></a>Globalny plik pominięć
 Globalny plik pominięć zachowuje pominięcia, które są pominięciami lub pominięciami na poziomie globalnym, które nie określają celu. Na przykład pominięcia dla naruszeń poziomu zestawu są przechowywane w tym pliku. Ponadto niektóre ASP.NET są przechowywane w tym pliku, ponieważ ustawienia na poziomie projektu nie są dostępne dla kodu za formularzem. Globalne pomijanie jest tworzone i dodawane do projektu przy pierwszym zaznaczeniu opcji **w pliku pomijania projektu** polecenia **Pomiń komunikaty** w oknie Lista błędów. Aby uzyskać więcej informacji, zobacz [How to: pomijanie ostrzeżeń przy użyciu elementu menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).

## <a name="see-also"></a>Zobacz też
 <xref:System.Diagnostics.CodeAnalysis>
