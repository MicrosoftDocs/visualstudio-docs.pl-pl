---
title: 'CA1824: Oznacz zestawy za pomocą NeutralResourcesLanguageAttribute | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 19077a63d5aa22bda3f968943703a82488e2745d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545291"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Oznaczaj zestawy za pomocą atrybutu NeutralResourcesLanguageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Kategoria|Microsoft. Performance|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Zestaw zawiera zasób oparty na protokole **resx**, ale nie ma do <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> niego zastosowania.

## <a name="rule-description"></a>Opis reguły
 Atrybut **NeutralResourcesLanguage** informujemanager **o języku, który** został użyty do wyświetlenia zasobów kultury neutralnej dla zestawu. Gdy wyszukuje zasoby w tej samej kulturze co neutralny język zasobów, program **ResourceManager** automatycznie korzysta z zasobów, które znajdują się w głównym zestawie. Wykonuje to zamiast wyszukiwania zestawu satelickiego, który ma bieżącą kulturę interfejsu użytkownika dla bieżącego wątku. To zwiększa wydajność wyszukiwania dla pierwszego zasobu, który się ładuje i może zmniejszyć zestaw roboczy.

## <a name="fixing-violations"></a>Naprawianie naruszeń
 Aby naprawić naruszenie tej zasady, Dodaj atrybut do zestawu i określ język zasobów kultury neutralnej.

## <a name="specifying-the-language"></a>Określanie języka

#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>Aby określić język zasobów kultury neutralnej

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie kliknij polecenie **Właściwości**.

2. Na lewym pasku nawigacyjnym wybierz pozycję **aplikacja**, a następnie kliknij pozycję **Informacje o zestawie**.

3. W oknie dialogowym **Informacje o zestawie** wybierz język z listy rozwijanej **Język neutralny** .

4. Kliknij przycisk **OK**.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można pominąć ostrzeżenie z tej reguły. Jednak wydajność uruchamiania może ulec zmniejszeniu.
