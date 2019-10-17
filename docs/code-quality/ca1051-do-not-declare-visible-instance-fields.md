---
title: 'CA1051: Nie deklaruj widocznych pól wystąpień'
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
ms.openlocfilehash: 69fb85c396da1acde40cd9bc46150ca5f1386c17
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449126"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: Nie deklaruj widocznych pól wystąpień

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Kategoria|Microsoft. Design|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Typ zawiera pole wystąpienia nieprywatne.

Domyślnie ta reguła sprawdza tylko typy widoczne na zewnątrz, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Głównym zastosowaniem pola powinno być to, co szczegółowo opisuje implementacja. Pola powinny być `private` lub `internal` i powinny być uwidocznione przy użyciu właściwości. Uzyskiwanie dostępu do właściwości w taki sposób, aby uzyskać dostęp do pola, a kod w metodzie dostępu do właściwości może ulec zmianie jako funkcje typu rozwinięte bez wprowadzania istotnych zmian.

Właściwości, które po prostu zwracają wartość pola prywatnego lub wewnętrznego, są zoptymalizowane do wykonywania na wartości nominalnej z dostępem do pola. wzrost wydajności z używania widocznych zewnętrznie pól zamiast właściwości jest minimalny. *Widoczne na zewnątrz* odnoszą się do `public`, `protected` i `protected internal` (`Public`, `Protected` i `Protected Friend` na Visual Basic) poziomów ułatwień dostępu.

Ponadto pola publiczne nie mogą być chronione przez [żądania połączeń](/dotnet/framework/misc/link-demands). Aby uzyskać więcej informacji, zobacz [CA2112: zabezpieczone typy nie powinny ujawniać pól](../code-quality/ca2112.md). (Wymagania dotyczące linków nie mają zastosowania do aplikacji .NET Core).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy wprowadzić wartość pola `private` lub `internal` i uwidocznić ją przy użyciu właściwości widocznej zewnętrznie.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Pomiń to ostrzeżenie tylko wtedy, gdy masz pewność, że klienci potrzebują bezpośredniego dostępu do pola. W przypadku większości aplikacji uwidocznione pola nie zapewniają wydajności ani korzyści płynących z używania właściwości.

Konsumenci mogą potrzebować dostępu do pól w następujących sytuacjach:

- w kontrolkach zawartości formularzy sieci Web ASP.NET
- gdy platforma docelowa korzysta z `ref`, aby zmodyfikować pola, takie jak platformy Model-View-ViewModel (MVVM) dla WPF i platformy UWP

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1051.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono typ (`BadPublicInstanceFields`) naruszający tę regułę. `GoodPublicInstanceFields` pokazuje skorygowany kod.

[!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]

## <a name="related-rules"></a>Powiązane reguły

- [CA2112: Typy zabezpieczone nie powinny ujawniać pól](../code-quality/ca2112.md)

## <a name="see-also"></a>Zobacz także

- [Wymagania dotyczące linków](/dotnet/framework/misc/link-demands)
