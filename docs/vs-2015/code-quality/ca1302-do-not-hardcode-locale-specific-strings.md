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
ms.openlocfilehash: 18da0471b1ac62f0e61b303c60b46c15cdc2e428
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539012"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: Nie umieszczaj trwale w kodzie ciągów specyficznych dla ustawień regionalnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Kategoria|Microsoft. Globalizacja|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Metoda używa literału ciągu, który reprezentuje część ścieżki określonych folderów systemowych.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Environment.SpecialFolder?displayProperty=fullName>Wyliczenie zawiera elementy członkowskie, które odwołują się do specjalnych folderów systemu. Lokalizacje tych folderów mogą mieć różne wartości w różnych systemach operacyjnych, użytkownik może zmienić niektóre lokalizacje, a lokalizacje są zlokalizowane. Przykładem folderu specjalnego jest folder systemowy "C:\WINDOWS\system32", [!INCLUDE[winxp](../includes/winxp-md.md)] ale "C:\winnt\system32" w [!INCLUDE[win2kfamily](../includes/win2kfamily-md.md)] . <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName>Metoda zwraca lokalizacje, które są skojarzone z <xref:System.Environment.SpecialFolder> wyliczeniem. Lokalizacje zwracane przez <xref:System.Environment.GetFolderPath%2A> są zlokalizowane i odpowiednie dla aktualnie uruchomionego komputera.

 Ta reguła tokenizes ścieżki folderów, które są pobierane przy użyciu <xref:System.Environment.GetFolderPath%2A> metody do oddzielnych poziomów katalogów. Każdy literał ciągu jest porównywany z tokenami. W przypadku znalezienia dopasowania przyjmuje się, że metoda kompiluje ciąg, który odwołuje się do lokalizacji systemowej skojarzonej z tokenem. W celu przenoszenia i lokalizowania należy użyć <xref:System.Environment.GetFolderPath%2A> metody, aby pobrać lokalizacje specjalnych folderów systemowych zamiast używać literałów ciągów.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy pobrać lokalizację przy użyciu <xref:System.Environment.GetFolderPath%2A> metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli literał ciągu nie jest używany do odwoływania się do jednej z lokalizacji systemowych skojarzonych z wyliczeniem, można bezpiecznie pominąć ostrzeżenie z tej reguły <xref:System.Environment.SpecialFolder> .

## <a name="example"></a>Przykład
 Poniższy przykład tworzy ścieżkę folderu danych wspólnych aplikacji, który generuje trzy ostrzeżenia z tej reguły. Następnie przykład Pobiera ścieżkę przy użyciu <xref:System.Environment.GetFolderPath%2A> metody.

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/cs/FxCop.Globalization.HardcodedLocaleStrings.cs#1)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/vb/FxCop.Globalization.HardcodedLocaleStrings.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1303: Nie przekazuj literałów jako zlokalizowanych parametrów](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)
