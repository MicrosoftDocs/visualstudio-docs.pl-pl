---
title: 'CA1302: Nie umieszczaj trwale w kodzie ciągów specyficznych dla ustawień regionalnych'
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
ms.openlocfilehash: a52add4453276ebf415b47f7f50e74b51a573306
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546534"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: Nie umieszczaj trwale w kodzie ciągów specyficznych dla ustawień regionalnych

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Kategoria|Microsoft.Globalization|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Metoda używa literał ciągu reprezentujący części ścieżki niektórych folderów systemowych.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Environment.SpecialFolder?displayProperty=fullName> Wyliczenia zawiera elementy członkowskie, które odwołują się do folderów specjalnych systemu. Lokalizacje tych folderów mogą mieć różne wartości w różnych systemach operacyjnych, użytkownik może zmienić niektóre z tych lokalizacji i lokalizacje są zlokalizowane. Przykładem specjalny folder jest folder systemowy, który jest "C:\WINDOWS\system32" na [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] , ale "C:\WINNT\system32" na [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)]. <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> Metoda zwraca lokalizacje, które są skojarzone z <xref:System.Environment.SpecialFolder> wyliczenia. Lokalizacje, które są zwracane przez <xref:System.Environment.GetFolderPath%2A> są zlokalizowane i odpowiednie dla danego komputera.

 Ta zasada tokenizes ścieżek folderów, które są pobierane za pomocą <xref:System.Environment.GetFolderPath%2A> metody na poziomy oddzielny katalog. Literał ciągu jest porównywany z tokenów. Jeśli zostanie znalezione dopasowanie, zakłada się, że metoda tworzy ciąg, który odwołuje się do lokalizacji w systemie, który jest skojarzony z tokenem. W przypadku przenoszenia i przeglądu możliwości lokalizacji używać <xref:System.Environment.GetFolderPath%2A> metodę, która pobierze lokalizacje folderów specjalnych systemu, zamiast literałów ciągów.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy pobrać lokalizacji przy użyciu <xref:System.Environment.GetFolderPath%2A> metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżeń dla tej reguły, jeśli literał ciągu nie jest używana do odwoływania się do jednej z lokalizacji systemu, które jest skojarzone z można bezpiecznie <xref:System.Environment.SpecialFolder> wyliczenia.

## <a name="example"></a>Przykład
 Poniższy przykład tworzy ścieżkę do wspólnego folderu dane aplikacji, która powoduje wygenerowanie ostrzeżenia trzy od tej reguły. Następnie przykład pobiera ścieżki przy użyciu <xref:System.Environment.GetFolderPath%2A> metody.

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1303: Nie przekazuj literałów jako parametrów zlokalizowanych](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)