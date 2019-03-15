---
title: 'CA1040: Unikaj pustych interfejsów'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 726953de0a92c0237ecaf7b724d9586a5d0f4c16
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57868733"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: Unikaj pustych interfejsów

|||
|-|-|
|TypeName|AvoidEmptyInterfaces|
|CheckId|CA1040|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Interfejs zadeklarować wszystkie elementy Członkowskie lub nie implementuje dwa lub więcej interfejsów.

Domyślnie ta reguła przegląda tylko widoczne na zewnątrz interfejsów, ale jest to [konfigurowalne](#configurability).

## <a name="rule-description"></a>Opis reguły

Interfejsy definiują elementy członkowskie, które zapewniają zachowanie lub użycie kontraktu. Funkcjonalność opisana przez interfejs może zostać przyjęta przez dowolny typ, niezależnie od tego, gdzie ten typ się pojawia w hierarchii dziedziczenia. Typ implementuje interfejs, dostarczając implementacje dla jego elementów członkowskich. Pusty interfejs nie definiuje żadnych elementów członkowskich. W związku z tym nie definiuje kontraktu, który może być implementowana.

Jeśli projekt zawiera pusty powinny implementować interfejsy, które typy, prawdopodobnie używasz interfejsu jako znacznik lub do identyfikowania grupy typów. Jeśli ten identyfikator będzie występować w czasie wykonywania, prawidłowym sposobem, aby osiągnąć ten cel jest używać atrybutu niestandardowego. Użyj obecności lub braku atrybutu lub właściwości atrybutu, aby zidentyfikować typów docelowych. Jeśli identyfikator musi wystąpić w czasie kompilacji, a następnie dopuszcza się użycia pusty interfejs.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Usuń interfejs lub dodać członków do niego. Jeśli pusty interfejs jest używany jako etykieta zestaw typów, Zamień niestandardowy atrybut interfejsu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli ten interfejs jest używany do identyfikowania zestaw typów w czasie kompilacji.

## <a name="configurability"></a>Konfigurowalne

Po uruchomieniu tej reguły z [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) (a nie przy użyciu statycznej analizy kodu) części, które można skonfigurować Twojej bazy kodu do uruchomienia tej reguły na, oparte na ich dostępność. Na przykład aby określić, że zasady powinny być uruchamiane wyłącznie w odniesieniu do powierzchni interfejsu API niepublicznych, Dodaj następujące pary klucz wartość w pliku .editorconfig w projekcie:

```
dotnet_code_quality.ca1040.api_surface = private, internal
```

Można skonfigurować tę opcję tylko reguły dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [analizatory FxCop analizujące kod z skonfigurować](configure-fxcop-analyzers.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje pusty interfejs.

[!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CSharp/ca1040-avoid-empty-interfaces_1.cs)]
[!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CPP/ca1040-avoid-empty-interfaces_1.cpp)]
[!code-vb[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/VisualBasic/ca1040-avoid-empty-interfaces_1.vb)]