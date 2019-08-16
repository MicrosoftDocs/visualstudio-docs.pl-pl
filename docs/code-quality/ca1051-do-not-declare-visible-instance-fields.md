---
title: 'CA1051: Nie deklaruj widocznych pól w wystąpieniach'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5dd8a4b2d0b32a8c52f75dee6fd765a7ea6ec9a
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547556"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: Nie deklaruj widocznych pól w wystąpieniach

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Typ zawiera pole wystąpienia nieprywatne.

Domyślnie ta reguła sprawdza tylko typy widoczne na zewnątrz, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Głównym zastosowaniem pola powinno być to, co szczegółowo opisuje implementacja. Pola powinny być `private` lub `internal` i powinny być udostępniane przy użyciu właściwości. Uzyskiwanie dostępu do właściwości w taki sposób, aby uzyskać dostęp do pola, a kod w metodzie dostępu do właściwości może ulec zmianie jako funkcje typu rozwinięte bez wprowadzania istotnych zmian. Właściwości, które po prostu zwracają wartość pola prywatnego lub wewnętrznego, są zoptymalizowane do wykonywania na wartości nominalnej z dostępem do pola. bardzo mały wzrost wydajności jest skojarzony z użyciem widocznych zewnętrznie pól nad właściwościami.

Widoczne na zewnątrz odnoszą `public`się `protected`do poziomów `protected internal` dostępności, `Protected`, i `Protected Friend` (`Public`, i w Visual Basic).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy wprowadzić pole `private` lub `internal` i uwidocznić je przy użyciu właściwości widocznej zewnętrznie.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły. Pola widoczne na zewnątrz nie zapewniają żadnych korzyści, które nie są dostępne dla właściwości. Ponadto pola publiczne nie mogą być chronione przez [żądania połączeń](/dotnet/framework/misc/link-demands). Zobacz [CA2112: Zabezpieczone typy nie powinny ujawniać](../code-quality/ca2112-secured-types-should-not-expose-fields.md)pól.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1051.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono typ (`BadPublicInstanceFields`), który narusza tę regułę. `GoodPublicInstanceFields`pokazuje poprawiony kod.

[!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]

## <a name="related-rules"></a>Powiązane reguły

- [CA2112 Zabezpieczone typy nie powinny ujawniać pól](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Zobacz także

- [Wymagania dotyczące linków](/dotnet/framework/misc/link-demands)