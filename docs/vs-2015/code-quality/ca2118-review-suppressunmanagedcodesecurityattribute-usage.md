---
title: 'CA2118: Przejrzyj przypadki użycia atrybutu SuppressUnmanagedCodeSecurityAttribute | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: eb76233e968ad8212d15fbcc815c31ffd0f1838a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60059178"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: Przejrzyj przypadki użycia atrybutu SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|CheckId|CA2118|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony lub elementu członkowskiego ma <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> atrybutu.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> Zmienia domyślne zachowanie systemu zabezpieczeń dla elementów członkowskich wykonujących kod niezarządzany, za pomocą wywołań międzyoperacyjnych COM lub platformy. Ogólnie rzecz biorąc, system sprawia, że [dane i modelowanie](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) uprawnienia kodu niezarządzanego. To żądanie występuje w czasie wykonywania dla każdego wywołania elementu członkowskiego i sprawdza, czy każdy obiekt wywołujący w stosie wywołań, aby uzyskać uprawnienia. Gdy atrybut nie jest obecny, system sprawia, że [zapotrzebowania na łącza](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) uprawnienia: Jeśli element wywołujący jest kompilowany dokładnie na czas, sprawdzane są uprawnienia bezpośredniego obiektu wywołującego.

 Atrybut ten jest używany głównie w celu zwiększenia wydajności; jednak wzrost wydajności powoduje znaczące zagrożenia dla bezpieczeństwa. Jeśli umieścisz ten atrybut na publiczne elementy członkowskie, które wywołują metody natywnej obiektów wywołujących w stosie wywołań (inne niż bezpośredniego obiektu wywołującego) nie ma potrzeby kodu niezarządzanego uprawnienia do wykonywania kodu niezarządzanego. W zależności od członka publicznego działania i obsługi danych wejściowych jego Zezwalaj na niezaufane wywołań do dostępu do funkcjonalności zazwyczaj ograniczone do zaufanego kodu.

 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Bazuje na kontroli zabezpieczeń uniemożliwia wywołującym uzyskania bezpośredniego dostępu do przestrzeni adresowej bieżącego procesu. Omija normalne zabezpieczeń, ten atrybut kodzie stwarza poważne zagrożenie, jeśli może służyć do odczytu lub zapisu w pamięci procesu. Należy pamiętać, że ryzyko nie jest ograniczona do metod, które celowo zapewniają dostęp do pamięci; procesu jest również obecny w każdym scenariuszu, w których złośliwy kod może osiągnąć dostępu w jakikolwiek sposób, na przykład przez podanie danych wejściowych Zaskakujące, źle sformułowany lub nieprawidłowy.

 Domyślne zasady zabezpieczeń nie powoduje przyznania uprawnień kodu niezarządzanego do zestawu, chyba że jest wykonywane z komputera lokalnego, lub jest ono członkiem jednej z następujących grup:

- Moja grupa kodu strefy

- Grupy kodu programu Microsoft silnej nazwy

- Grupy kodu programu ECMA silnej nazwy

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Należy dokładnie przejrzeć swój kod, aby upewnić się, że ten atrybut jest to absolutnie konieczne. Jeśli znasz zakresu zabezpieczeń dla kodu zarządzanego lub ich nie zrozumieć implikacje zabezpieczeń korzystające z tego atrybutu, należy go usunąć z kodu. Jeśli ten atrybut jest wymagany, upewnij się, że obiekty wywołujące nie mogą używać złośliwie swój kod. Jeśli Twój kod nie ma uprawnienia do wykonywania kodu niezarządzanego, ten atrybut nie ma wpływu i powinny zostać usunięte.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Aby bezpiecznie pominąć ostrzeżenie od tej reguły, upewnij się, że Twój kod nie zawiera obiektów wywołujących dostęp do natywnych operacji lub zasobów, które mogą być używane w szkodliwy sposób.

## <a name="example"></a>Przykład
 Poniższy przykład narusza regułę.

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesDoNotSuppress/cs/FxCop.Security.TypesDoNotSuppress.cs#1)]

## <a name="example"></a>Przykład
 W poniższym przykładzie `DoWork` metoda zapewnia ścieżkę publicznie kod do metody wywołania platformy `FormatHardDisk`.

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PInvokeAndSuppress/cs/FxCop.Security.PInvokeAndSuppress.cs#1)]

## <a name="example"></a>Przykład
 W poniższym przykładzie metoda publiczna `DoDangerousThing` powoduje naruszenie zasad. Aby rozwiązać naruszenie, `DoDangerousThing` powinno się prywatny i powinna być do niego dostęp za pośrednictwem publicznej metody zabezpieczonego przez żądanie zabezpieczeń, zgodnie z przedstawionymi `DoWork` — metoda.

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypeInvokeAndSuppress/cs/FxCop.Security.TypeInvokeAndSuppress.cs#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> [Wytyczne dotyczące bezpiecznego programowania](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [optymalizacje zabezpieczeń](http://msdn.microsoft.com/cf255069-d85d-4de3-914a-e4625215a7c0) [dane i modelowanie](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) [Link żądania](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
