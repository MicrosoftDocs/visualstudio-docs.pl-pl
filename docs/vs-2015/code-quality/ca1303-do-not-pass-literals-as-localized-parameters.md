---
title: 'CA1303: nie przekazuj literałów jako parametrów zlokalizowanych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f3ad1f56215d002c03d346b38ce6155e8df7412b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539116"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: Nie przekazuj literałów jako zlokalizowanych parametrów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Kategoria|Microsoft. Globalizacja|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Metoda przekazuje literał ciągu jako parametr do konstruktora lub metody w [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] bibliotece klas i ten ciąg powinien być Lokalizowalny.

 To ostrzeżenie jest zgłaszane, gdy ciąg literału zostanie przesunięty jako wartość do parametru lub właściwości, co najmniej jeden z następujących przypadków ma wartość true:

- <xref:System.ComponentModel.LocalizableAttribute>Atrybut parametru lub właściwości jest ustawiony na wartość true.

- Nazwa parametru lub właściwości zawiera tekst "text", "Message" lub "Caption".

- Nazwa parametru ciągu, który jest przesyłany do konsoli. Write lub Console. WriteLine ma wartość "value" lub "format".

## <a name="rule-description"></a>Opis reguły
 Literały ciągu, które są osadzone w kodzie źródłowym, są trudne do zlokalizowania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zastąp literał ciągu ciągiem pobranym przez wystąpienie <xref:System.Resources.ResourceManager> klasy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli biblioteka kodu nie zostanie zlokalizowana, można bezpiecznie pominąć ostrzeżenie z tej reguły lub jeśli ten ciąg nie jest widoczny dla użytkownika końcowego lub dewelopera przy użyciu biblioteki kodu.

 Użytkownicy mogą wyeliminować hałas względem metod, które nie powinny być przesyłane do zlokalizowanych ciągów przez zmianę nazwy parametru lub właściwości o nazwie lub poprzez oznaczenie tych elementów jako warunku.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia metodę, która zgłasza wyjątek, gdy jeden z dwóch argumentów jest poza zakresem. Dla pierwszego argumentu Konstruktor wyjątku jest przenoszona jako ciąg literału, co narusza tę regułę. Dla drugiego argumentu Konstruktor prawidłowo przeszedł ciąg pobrany przez <xref:System.Resources.ResourceManager> .

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cpp/FxCop.Globalization.DoNotPassLiterals.cpp#1)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cs/FxCop.Globalization.DoNotPassLiterals.cs#1)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/vb/FxCop.Globalization.DoNotPassLiterals.vb#1)]

## <a name="see-also"></a>Zobacz też
 [Zasoby w aplikacjach klasycznych](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
