---
title: 'CA1302: nie należy umieszczaj ciągów specyficznych dla ustawień regionalnych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6e16fff154b5c0df660b06e5bf9e9e838762adff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661473"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: Nie należy kodować ciągów określonych dla ustawień regionalnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Kategoria|Microsoft. Globalizacja|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Metoda używa literału ciągu, który reprezentuje część ścieżki określonych folderów systemowych.

## <a name="rule-description"></a>Opis reguły
 Wyliczenie <xref:System.Environment.SpecialFolder?displayProperty=fullName> zawiera elementy członkowskie, które odwołują się do specjalnych folderów systemu. Lokalizacje tych folderów mogą mieć różne wartości w różnych systemach operacyjnych, użytkownik może zmienić niektóre lokalizacje, a lokalizacje są zlokalizowane. Przykładem folderu specjalnego jest folder systemowy "C:\WINDOWS\system32" na [!INCLUDE[winxp](../includes/winxp-md.md)], ale "C:\WINNT\system32" na [!INCLUDE[win2kfamily](../includes/win2kfamily-md.md)]. Metoda <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> zwraca lokalizacje, które są skojarzone z wyliczeniem <xref:System.Environment.SpecialFolder>. Lokalizacje zwracane przez <xref:System.Environment.GetFolderPath%2A> są zlokalizowane i odpowiednie dla aktualnie uruchomionego komputera.

 Ta reguła tokenizes ścieżki folderów, które są pobierane za pomocą metody <xref:System.Environment.GetFolderPath%2A> do oddzielnych poziomów katalogów. Każdy literał ciągu jest porównywany z tokenami. W przypadku znalezienia dopasowania przyjmuje się, że metoda kompiluje ciąg, który odwołuje się do lokalizacji systemowej skojarzonej z tokenem. W celu przenoszenia i lokalizowania Użyj metody <xref:System.Environment.GetFolderPath%2A>, aby pobrać lokalizacje specjalnych folderów systemowych zamiast używać literałów ciągów.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy pobrać lokalizację przy użyciu metody <xref:System.Environment.GetFolderPath%2A>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli literał ciągu nie jest używany do odwoływania się do jednej z lokalizacji systemowych skojarzonych z wyliczeniem <xref:System.Environment.SpecialFolder>, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład tworzy ścieżkę folderu danych wspólnych aplikacji, który generuje trzy ostrzeżenia z tej reguły. Następnie przykład Pobiera ścieżkę przy użyciu metody <xref:System.Environment.GetFolderPath%2A>.

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/cs/FxCop.Globalization.HardcodedLocaleStrings.cs#1)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/vb/FxCop.Globalization.HardcodedLocaleStrings.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1303: Nie przekazuj literałów jako parametrów zlokalizowanych](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)
