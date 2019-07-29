---
title: 'CA1053: Statyczne typy przechowujące nie powinny mieć konstruktorów'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fec59e1d683c7867eb1cad9ae4e796a0815200d4
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/29/2019
ms.locfileid: "68604785"
---
# <a name="ca1053-static-holder-types-should-not-have-default-constructors"></a>CA1053: Statyczne typy posiadaczy nie powinny mieć domyślnych konstruktorów

|||
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

> [!NOTE]
> Reguła CA1053 jest łączona w [CA1052: Statyczne typy zbiorników powinny być](ca1052-static-holder-types-should-be-sealed.md) zapieczętowane w [analizatorach FxCop](fxcop-analyzers.yml).

## <a name="cause"></a>Przyczyna

Publiczny lub zagnieżdżony typ publiczny deklaruje tylko statyczne elementy członkowskie i ma konstruktora domyślnego.

## <a name="rule-description"></a>Opis reguły

Konstruktor domyślny jest zbędny, ponieważ wywołujące statyczne elementy członkowskie nie wymagają wystąpienia typu. Ponadto, ponieważ typ nie ma elementów członkowskich niestatycznych, utworzenie wystąpienia nie zapewnia dostępu do żadnego z elementów członkowskich typu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, Usuń konstruktora domyślnego.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły. Obecność konstruktora domyślnego sugeruje, że typ nie jest typem statycznym.