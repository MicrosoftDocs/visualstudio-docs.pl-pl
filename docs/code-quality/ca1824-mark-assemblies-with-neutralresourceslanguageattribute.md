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
ms.openlocfilehash: 40cb2a3674884a9fb4f1449c9afa2e0a2d27050f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55919147"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Oznaczaj zestawy za pomocą atrybutu NeutralResourcesLanguageAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Zestaw zawiera **ResX**— na podstawie zasobów, ale nie ma <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> stosowane do niego.

## <a name="rule-description"></a>Opis reguły

<xref:System.Resources.NeutralResourcesLanguageAttribute> Atrybut informuje Menedżera zasobów kultury domyślnej aplikacji. Jeśli zasoby domyślnej kultury są osadzone w głównym zestawie przez aplikację i <xref:System.Resources.ResourceManager> musi pobrać zasoby, które należą do tej samej kultury jako kultury domyślnej <xref:System.Resources.ResourceManager> automatycznie używa zasobów znajdujących się w głównym zestawie zamiast wyszukiwać zestawu satelickiego. To pomija sondy zwykle zestawu, zwiększa wydajność wyszukiwania dla pierwszego zasobu, obciążenia i może zmniejszyć zestaw roboczy.

> [!TIP]
> Zobacz [pakowanie i wdrażanie zasobów](/dotnet/framework/resources/packaging-and-deploying-resources-in-desktop-apps) dla procesu, <xref:System.Resources.ResourceManager> używa do sondowania dla plików zasobów.

## <a name="fix-violations"></a>Naprawić naruszenia

Aby naprawić naruszenie tej zasady, Dodaj atrybut do zestawu, a także określić język zasobów kultury neutralnej.

### <a name="to-specify-the-neutral-language-for-resources"></a>Określa neutralny język zasobów

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **właściwości**.

2. Wybierz **aplikacji** , a następnie wybierz pozycję **informacje o zestawie**.

   > [!NOTE]
   > Jeśli projekt jest projektem .NET Standard i .NET Core, wybierz **pakietu** kartę.

3. Wybierz język z **neutralnym językiem** lub **neutralny język asemblera** listy rozwijanej.

4. Kliknij przycisk **OK**.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest dozwolone, aby pominąć ostrzeżenie od tej reguły. Jednak może obniżyć wydajność uruchamiania.

## <a name="see-also"></a>Zobacz także

- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- [Zasoby w aplikacjach komputerowych (.NET)](/dotnet/framework/resources/)
- [CA1703 — ciągi zasobu powinny być zapisane poprawnie](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1701 — ciąg zasobu, w których wyrazy złożone powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)