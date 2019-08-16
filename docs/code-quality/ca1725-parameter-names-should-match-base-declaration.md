---
title: 'CA1725: Nazwy parametrów powinny być zgodne z deklaracją podstawową'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0d5afd33ffb73c47b0f373f70c56166dbfced6d
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547121"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725: Nazwy parametrów powinny być zgodne z deklaracją podstawową

|||
|-|-|
|TypeName|ParameterNamesShouldMatchBaseDeclaration|
|CheckId|CA1725|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Nazwa parametru w przesłonięciu metody nie jest zgodna z nazwą parametru w podstawowej deklaracji metody lub nazwie parametru w deklaracji interfejsu metody.

Domyślnie ta reguła przegląda tylko zewnętrznie widoczne metody, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Spójne nazywanie parametrów w zastąpieniu hierarchii zwiększa użyteczność zastąpienia metody. Jeśli nazwa parametru w metodzie pochodnej różni się od nazwy podstawowej deklaracji, może nie być jasne, czy metoda jest zastąpieniem metody podstawowej, czy też nowym przeciążeniem metody.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, Zmień nazwę parametru tak, aby była zgodna z deklaracją podstawową. Poprawka jest istotną zmianą dla metod widocznych dla modelu COM.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżenia z tej reguły, z wyjątkiem metod widocznych dla modelu COM w bibliotekach, które zostały wcześniej dostarczone.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1725.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (nazywanie). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).