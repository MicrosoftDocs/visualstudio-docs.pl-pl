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
ms.openlocfilehash: 44bdb8c12b48a983b88e6a035fc1522856b306be
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235585"
---
# <a name="ca1053-static-holder-types-should-not-have-default-constructors"></a>CA1053: Statyczne typy posiadaczy nie powinny mieć domyślnych konstruktorów

|||
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Kategoria|Microsoft.Design|
|Zmiana podziału|Kluczowa|

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