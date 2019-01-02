---
title: 'CA2106: Zabezpiecz asercje'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 164d2bbe335f4b69892cf069bade5cf0df1e0787
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864676"
---
# <a name="ca2106-secure-asserts"></a>CA2106: Zabezpiecz asercje

|||
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda potwierdza uprawnienia i nie sprawdza zabezpieczeń na obiekcie wywołującym.

## <a name="rule-description"></a>Opis reguły
 Potwierdzanie uprawnienia zabezpieczeń bez sprawdzania zabezpieczeń może pozostawić zdatną do wykorzystania słabość zabezpieczeń w kodzie. Przeszukiwania stosu zabezpieczeń zatrzymuje, gdy jest potwierdzone uprawnienia zabezpieczeń. Jeśli uprawnienie jest assert bez wykonywania jakiejkolwiek kontroli obiekt wywołujący i obiekt wywołujący pośrednio wykonanie kodu przy użyciu uprawnień. Asercje bez kontroli zabezpieczeń są dopuszczalne, jeśli masz pewności, że asercja nie można używać w szkodliwy sposób. Asercja jest nieszkodliwe, jeśli kod, który można wywołać jest nieszkodliwe, lub jeśli użytkownicy nie mogła przekazywać dowolne informacje do kodu, który można wywoływać.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy dodać żądania zabezpieczeń do metody lub jej typ deklarujący.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżeń dla tej reguły tylko po weryfikacji zabezpieczeń zachowania ostrożność.

## <a name="see-also"></a>Zobacz także

- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
- [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)