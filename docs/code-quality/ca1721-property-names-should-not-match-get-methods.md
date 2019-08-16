---
title: 'CA1721: Nazwy właściwości nie powinny być takie same jak nazwy metod Get'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 44028caf027191846fa653db06abbe4027fdde8d
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547092"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: Nazwy właściwości nie powinny być takie same jak nazwy metod Get

|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Nazwa elementu członkowskiego rozpoczyna się od "Get" i w przeciwnym razie dopasowuje nazwę właściwości. Na przykład typ zawierający metodę o nazwie "GetColor" oraz właściwość o nazwie "Color" powoduje naruszenie reguły.

Domyślnie ta reguła sprawdza tylko widoczne na zewnątrz elementy członkowskie i właściwości, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Metody „Get” i właściwości powinny mieć nazwy, które wyraźnie odróżniają ich funkcje.

Konwencje nazewnictwa zapewniają typowy wygląd bibliotek przeznaczonych dla środowiska uruchomieniowego języka wspólnego. Ta spójność skraca czas wymagany do nauczenia się nowej biblioteki oprogramowania i zwiększa zaufanie klienta, że biblioteka została opracowana przez kogoś, kto ma doświadczenie w tworzeniu kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Zmień nazwę tak, aby nie odpowiadała nazwie metody poprzedzonej prefiksem "Get".

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

> [!NOTE]
> To ostrzeżenie może zostać wykluczone, jeśli metoda "Get" jest spowodowana przez implementację interfejsu interfejsu IExtenderProvider.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1721.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (nazywanie). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Przykład

Poniższy przykład zawiera metodę i właściwość, która narusza tę regułę.

[!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
[!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1024: Użyj właściwości, jeśli to konieczne](../code-quality/ca1024-use-properties-where-appropriate.md)