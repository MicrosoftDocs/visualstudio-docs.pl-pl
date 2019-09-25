---
title: 'CA1824: Oznaczaj zestawy za pomocą atrybutu NeutralResourcesLanguageAttribute'
ms.date: 03/29/2018
ms.topic: reference
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df5c0db4e9e141e5833893bbbb447328eab8851e
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233344"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Oznaczaj zestawy za pomocą atrybutu NeutralResourcesLanguageAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Kategoria|Microsoft.Performance|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Zestaw zawiera zasób oparty na protokole **resx**, <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> ale nie ma do niego zastosowania.

## <a name="rule-description"></a>Opis reguły

Ten <xref:System.Resources.NeutralResourcesLanguageAttribute> atrybut informuje Menedżera zasobów domyślnej kultury aplikacji. Jeśli zasoby kultury domyślnej są osadzone w zestawie głównym aplikacji i <xref:System.Resources.ResourceManager> muszą pobierać zasoby należące do tej samej kultury co kultura Domyślna <xref:System.Resources.ResourceManager> , automatycznie używa zasobów znajdujących się w zestawie głównym Zamiast wyszukiwania zestawu satelickiego. Spowoduje to pominięcie zwykłej sondy zestawu, zwiększenie wydajności wyszukiwania dla pierwszego załadowanego zasobu i może zmniejszyć zestaw roboczy.

> [!TIP]
> Zobacz [pakowanie i wdrażanie zasobów](/dotnet/framework/resources/packaging-and-deploying-resources-in-desktop-apps) dla procesu, który <xref:System.Resources.ResourceManager> używa do sondowania plików zasobów.

## <a name="fix-violations"></a>Napraw naruszenia

Aby naprawić naruszenie tej zasady, Dodaj atrybut do zestawu i określ język zasobów kultury neutralnej.

### <a name="to-specify-the-neutral-language-for-resources"></a>Aby określić język neutralny dla zasobów

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Właściwości**.

2. Wybierz kartę **aplikacja** , a następnie wybierz pozycję **Informacje o zestawie**.

   > [!NOTE]
   > Jeśli projekt jest projektem .NET Standard lub .NET Core, wybierz kartę **pakiet** .

3. Wybierz język z listy rozwijanej Język **neutralny** lub niezależny od **zestawu** .

4. Kliknij przycisk **OK**.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Można pominąć ostrzeżenie z tej reguły. Może jednak wystąpić spadek wydajności uruchomienia.

## <a name="see-also"></a>Zobacz także

- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- [Zasoby w aplikacjach klasycznych (.NET)](/dotnet/framework/resources/)
- [CA1703 — ciągi zasobów powinny mieć poprawną pisownię](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1701 — wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)