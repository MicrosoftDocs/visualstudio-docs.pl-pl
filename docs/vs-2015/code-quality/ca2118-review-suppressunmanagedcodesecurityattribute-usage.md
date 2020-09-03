---
title: 'CA2118: przegląd użycia SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bc0e88265245d795697d32a9e6a95909c0415259
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538661"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: Przejrzyj przypadki użycia atrybutu SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|CheckId|CA2118|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony lub składowa ma <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> atrybut.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> zmienia domyślne zachowanie systemu zabezpieczeń dla elementów członkowskich wykonujących niezarządzany kod przy użyciu międzyoperacyjności modelu COM lub wywołania platformy. Ogólnie rzecz biorąc, system wprowadza [dane i modelowanie](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) do niezarządzanego kodu. To zapotrzebowanie występuje w czasie wykonywania dla każdego wywołania elementu członkowskiego i sprawdza każdy obiekt wywołujący w stosie wywołań w celu uzyskania uprawnień. Gdy atrybut jest obecny, system wykonuje [żądania](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) dotyczące uprawnień: uprawnienia bezpośredniego wywołującego są sprawdzane, gdy obiekt wywołujący jest skompilowany w trybie JIT.

 Atrybut ten jest używany głównie w celu zwiększenia wydajności; jednak wzrost wydajności powoduje znaczące zagrożenia dla bezpieczeństwa. Jeśli umieścisz atrybut na publicznych składowych, które wywołują metody natywne, wywołujący w stosie wywołań (innym niż bezpośredni obiekt wywołujący) nie potrzebują uprawnień do kodu niezarządzanego do wykonywania kodu niezarządzanego. W zależności od akcji i obsługi danych w publicznej składowej można zezwolić niezaufanym wywołującym na dostęp do funkcji zwykle ograniczonych do wiarygodnego kodu.

 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]Polega na sprawdzaniu zabezpieczeń, aby uniemożliwić wywoływanie bezpośredniego dostępu do przestrzeni adresowej bieżącego procesu. Ponieważ ten atrybut pomija normalne zabezpieczenia, kod stanowi poważne zagrożenie, jeśli można go użyć do odczytu lub zapisu w pamięci procesu. Należy pamiętać, że ryzyko nie jest ograniczone do metod, które celowo zapewniają dostęp do pamięci procesu; jest również obecny w każdym scenariuszu, w którym złośliwy kod może uzyskać dostęp w dowolny sposób, na przykład dostarczając zaskakujące, źle sformułowane lub nieprawidłowe dane wejściowe.

 Domyślne zasady zabezpieczeń nie przyznają uprawnienia do kodu niezarządzanego do zestawu, chyba że jest on wykonywany z komputera lokalnego lub jest członkiem jednej z następujących grup:

- Grupa kodów strefy komputera

- Grupa kodu o silnej nazwie firmy Microsoft

- Grupa kodu o silnej nazwie ECMA

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Uważnie Przejrzyj swój kod, aby upewnić się, że ten atrybut jest absolutnie niezbędny. Jeśli nie znasz zabezpieczeń kodu zarządzanego lub nie rozumiesz skutków zabezpieczeń związanych z użyciem tego atrybutu, usuń go z kodu. Jeśli atrybut jest wymagany, należy się upewnić, że obiekty wywołujące nie mogą w sposób złośliwy używać kodu. Jeśli kod nie ma uprawnień do wykonywania kodu niezarządzanego, ten atrybut nie ma wpływu i powinien zostać usunięty.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Aby bezpiecznie pominąć ostrzeżenie z tej reguły, należy upewnić się, że kod nie zapewnia wywołujących dostępu do natywnych operacji lub zasobów, które mogą być używane w sposób niszczący.

## <a name="example"></a>Przykład
 Poniższy przykład narusza regułę.

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesDoNotSuppress/cs/FxCop.Security.TypesDoNotSuppress.cs#1)]

## <a name="example"></a>Przykład
 W poniższym przykładzie `DoWork` Metoda zapewnia publicznie dostępną ścieżkę kodu do metody wywołania platformy `FormatHardDisk` .

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PInvokeAndSuppress/cs/FxCop.Security.PInvokeAndSuppress.cs#1)]

## <a name="example"></a>Przykład
 W poniższym przykładzie metoda publiczna `DoDangerousThing` powoduje naruszenie. Aby rozwiązać ten problem, `DoDangerousThing` należy mieć charakter prywatny, a dostęp do niego powinien być realizowany za pomocą metody publicznej zabezpieczonej przez żądanie zabezpieczeń, co zostało opisane przez `DoWork` metodę.

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypeInvokeAndSuppress/cs/FxCop.Security.TypeInvokeAndSuppress.cs#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>[Zasady bezpiecznego kodowania — wymagania dotyczące](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [Security Optimizations](https://msdn.microsoft.com/cf255069-d85d-4de3-914a-e4625215a7c0) [danych i](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) [linków](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) modelowania
