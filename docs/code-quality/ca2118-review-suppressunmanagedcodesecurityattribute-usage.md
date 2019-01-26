---
title: 'CA2118: Przejrzyj przypadki użycia atrybutu SuppressUnmanagedCodeSecurityAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 092ac7599b0cfb715019a6a9894d845dc47747fc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54959060"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: Przejrzyj przypadki użycia atrybutu SuppressUnmanagedCodeSecurityAttribute

|||
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|CheckId|CA2118|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony lub elementu członkowskiego ma <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> atrybutu.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> Zmienia domyślne zachowanie systemu zabezpieczeń dla elementów członkowskich wykonujących kod niezarządzany, za pomocą wywołań międzyoperacyjnych COM lub platformy. Ogólnie rzecz biorąc, system sprawia, że [dane i modelowanie](/dotnet/framework/data/index) uprawnienia kodu niezarządzanego. To żądanie występuje w czasie wykonywania dla każdego wywołania elementu członkowskiego i sprawdza, czy każdy obiekt wywołujący w stosie wywołań, aby uzyskać uprawnienia. Gdy atrybut nie jest obecny, system sprawia, że [zapotrzebowania na łącza](/dotnet/framework/misc/link-demands) uprawnienia: Jeśli element wywołujący jest kompilowany dokładnie na czas, sprawdzane są uprawnienia bezpośredniego obiektu wywołującego.

 Atrybut ten jest używany głównie w celu zwiększenia wydajności; jednak wzrost wydajności powoduje znaczące zagrożenia dla bezpieczeństwa. Jeśli umieścisz ten atrybut na publiczne elementy członkowskie, które wywołują metody natywnej obiektów wywołujących w stosie wywołań (inne niż bezpośredniego obiektu wywołującego) nie ma potrzeby kodu niezarządzanego uprawnienia do wykonywania kodu niezarządzanego. W zależności od członka publicznego działania i obsługi danych wejściowych jego Zezwalaj na niezaufane wywołań do dostępu do funkcjonalności zazwyczaj ograniczone do zaufanego kodu.

 .NET Framework, zależy od sprawdza zabezpieczeń, co uniemożliwia wywołującym uzyskania bezpośredniego dostępu do przestrzeni adresowej bieżącego procesu. Omija normalne zabezpieczeń, ten atrybut kodzie stwarza poważne zagrożenie, jeśli może służyć do odczytu lub zapisu w pamięci procesu. Należy pamiętać, że ryzyko nie jest ograniczona do metod, które celowo zapewniają dostęp do pamięci; procesu jest również obecny w każdym scenariuszu, w których złośliwy kod może osiągnąć dostępu w jakikolwiek sposób, na przykład przez podanie danych wejściowych Zaskakujące, źle sformułowany lub nieprawidłowy.

 Domyślne zasady zabezpieczeń nie powoduje przyznania uprawnień kodu niezarządzanego do zestawu, chyba że jest wykonywane z komputera lokalnego, lub jest ono członkiem jednej z następujących grup:

- Moja grupa kodu strefy

- Grupy kodu programu Microsoft silnej nazwy

- Grupy kodu programu ECMA silnej nazwy

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Należy dokładnie przejrzeć swój kod, aby upewnić się, że ten atrybut jest to absolutnie konieczne. Jeśli znasz zakresu zabezpieczeń dla kodu zarządzanego lub ich nie zrozumieć implikacje zabezpieczeń korzystające z tego atrybutu, należy go usunąć z kodu. Jeśli ten atrybut jest wymagany, upewnij się, że obiekty wywołujące nie mogą używać złośliwie swój kod. Jeśli Twój kod nie ma uprawnienia do wykonywania kodu niezarządzanego, ten atrybut nie ma wpływu i powinny zostać usunięte.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Aby bezpiecznie pominąć ostrzeżenie od tej reguły, upewnij się, że Twój kod nie zawiera obiektów wywołujących dostęp do natywnych operacji lub zasobów, które mogą być używane w szkodliwy sposób.

## <a name="example-1"></a>Przykład 1
 Poniższy przykład narusza regułę.

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]

## <a name="example-2"></a>Przykład 2
 W poniższym przykładzie `DoWork` metoda zapewnia ścieżkę publicznie kod do metody wywołania platformy `FormatHardDisk`.

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]

## <a name="example-3"></a>Przykład 3
 W poniższym przykładzie metoda publiczna `DoDangerousThing` powoduje naruszenie zasad. Aby rozwiązać naruszenie, `DoDangerousThing` powinno się prywatny i powinna być do niego dostęp za pośrednictwem publicznej metody zabezpieczonego przez żądanie zabezpieczeń, zgodnie z przedstawionymi `DoWork` — metoda.

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_3.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>
- [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)
- [Dane i modelowanie](/dotnet/framework/data/index)
- [Zapotrzebowanie na łącza](/dotnet/framework/misc/link-demands)