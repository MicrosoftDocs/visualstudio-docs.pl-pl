---
title: 'CA1302: Nie należy kodować ciągów określonych dla ustawień regionalnych'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 727acfa5497f2d7f0d09349ff2f5f6648c9d1ca6
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444412"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: Nie należy kodować ciągów określonych dla ustawień regionalnych

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Kategoria|Microsoft. Globalizacja|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Metoda używa literału ciągu, który reprezentuje część ścieżki określonych folderów systemowych.

## <a name="rule-description"></a>Opis reguły
Wyliczenie <xref:System.Environment.SpecialFolder?displayProperty=fullName> zawiera elementy członkowskie, które odwołują się do specjalnych folderów systemu. Lokalizacje tych folderów mogą mieć różne wartości w różnych systemach operacyjnych, użytkownik może zmienić niektóre lokalizacje, a lokalizacje są zlokalizowane. Przykładem folderu specjalnego jest folder systemowy "C:\WINDOWS\system32" na [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)], ale "C:\WINNT\system32" w [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)]. Metoda <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> zwraca lokalizacje skojarzone z wyliczeniem <xref:System.Environment.SpecialFolder>. Lokalizacje zwracane przez <xref:System.Environment.GetFolderPath%2A> są zlokalizowane i odpowiednie dla aktualnie uruchomionego komputera.

Ta reguła tokenizes ścieżki folderów, które są pobierane za pomocą metody <xref:System.Environment.GetFolderPath%2A> do oddzielnych poziomów katalogów. Każdy literał ciągu jest porównywany z tokenami. W przypadku znalezienia dopasowania przyjmuje się, że metoda kompiluje ciąg, który odwołuje się do lokalizacji systemowej skojarzonej z tokenem. W celu przenoszenia i lokalizowania należy użyć metody <xref:System.Environment.GetFolderPath%2A>, aby pobrać lokalizacje specjalnych folderów systemowych zamiast używać literałów ciągów.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, należy pobrać lokalizację przy użyciu metody <xref:System.Environment.GetFolderPath%2A>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Jeśli literał ciągu nie jest używany do odwoływania się do jednej z lokalizacji systemowych skojarzonych z wyliczeniem <xref:System.Environment.SpecialFolder>, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład tworzy ścieżkę folderu danych wspólnych aplikacji, który generuje trzy ostrzeżenia z tej reguły. Następnie przykład Pobiera ścieżkę przy użyciu metody <xref:System.Environment.GetFolderPath%2A>.

[!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
[!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]

## <a name="related-rules"></a>Powiązane reguły
[CA1303: Nie przekazuj literałów jako parametrów zlokalizowanych](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)
