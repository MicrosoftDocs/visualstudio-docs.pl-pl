---
title: 'CA1824: Oznacz zestawy za pomocą atrybutu NeutralResourcesLanguageAttribute | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 795d48b96392057a3f96cf3a67f3c49de8aee9b9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052171"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Oznaczaj zestawy za pomocą atrybutu NeutralResourcesLanguageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Zestaw zawiera **ResX**— na podstawie zasobów, ale nie ma <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> stosowane do niego.

## <a name="rule-description"></a>Opis reguły
 **NeutralResourcesLanguage** informuje atrybut **ResourceManager** języka, który był używany do wyświetlania zasobów kultury neutralnej dla zestawu. Podczas wyszukiwania zasobów w tej samej kulturze jako język neutralne zasoby **ResourceManager** automatycznie używa zasobów, które znajdują się w głównym zestawie. Robi to zamiast wyszukiwać zestawu satelickiego, który ma Bieżąca kultura interfejsu użytkownika dla bieżącego wątku. To zwiększa wydajność wyszukiwania dla pierwszego zasobu, który się ładuje i może zmniejszyć zestaw roboczy.

## <a name="fixing-violations"></a>Naprawianie naruszenia
 Aby naprawić naruszenie tej zasady, Dodaj atrybut do zestawu, a także określić język zasobów kultury neutralnej.

## <a name="specifying-the-language"></a>Określając język

#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>Aby określić język zasobów kultury neutralnej

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **właściwości**.

2. Na pasku nawigacyjnym po lewej stronie wybierz **aplikacji**, a następnie kliknij przycisk **informacje o zestawie**.

3. W **informacje o zestawie** okna dialogowego Wybierz język z **niezależny od języka** listy rozwijanej.

4. Kliknij przycisk **OK**.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest dozwolone, aby pominąć ostrzeżenie od tej reguły. Jednak może zmniejszyć wydajność uruchamiania.
