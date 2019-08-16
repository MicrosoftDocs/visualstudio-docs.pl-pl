---
title: 'CA1716: Identyfikatory nie powinny być zgodne ze słowami kluczowymi'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a51ac9509cf891c05166d46e4b72b862c0dc723
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547083"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: Identyfikatory nie powinny być zgodne ze słowami kluczowymi

|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Nazwa przestrzeni nazw, typu lub elementu członkowskiego w interfejsie jest zgodna z zastrzeżonym słowem kluczowym w języku programowania.

Domyślnie ta reguła przegląda tylko zewnętrznie widoczne obszary nazw, typy i elementy członkowskie, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Identyfikatory przestrzeni nazw, typów i elementów członkowskich wirtualnych i interfejsów nie powinny być zgodne ze słowami kluczowymi, które są zdefiniowane przez Języki przeznaczone dla środowiska uruchomieniowego języka wspólnego. W zależności od używanego języka i słowa kluczowego, błędy kompilatora i niejasności mogą utrudniać korzystanie z biblioteki.

Ta reguła sprawdza słowa kluczowe w następujących językach:

- Visual Basic
- C#
- C++/CLI

Porównanie bez uwzględniania wielkości liter jest używane dla Visual Basic słów kluczowych, a porównanie z uwzględnieniem wielkości liter jest używane dla innych języków.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Wybierz nazwę, która nie jest wyświetlana na liście słów kluczowych.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Możesz pominąć ostrzeżenie z tej reguły, Jeśli wiesz, że identyfikator nie będzie mylić użytkowników interfejsu API i że biblioteka jest użyteczna we wszystkich dostępnych językach w programie .NET.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1716.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (nazywanie). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).