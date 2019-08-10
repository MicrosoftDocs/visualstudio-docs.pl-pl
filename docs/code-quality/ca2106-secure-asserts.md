---
title: 'CA2106: Zabezpiecz asercje'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df19d31abe88c6d12bafc933ba740badb832eb16
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921072"
---
# <a name="ca2106-secure-asserts"></a>CA2106: Zabezpiecz asercje

|||
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
Metoda potwierdza uprawnienie i nie sprawdza zabezpieczeń obiektu wywołującego.

## <a name="rule-description"></a>Opis reguły
Potwierdzanie uprawnienia zabezpieczeń bez sprawdzania zabezpieczeń może pozostawić zdatną do wykorzystania słabość zabezpieczeń w kodzie. Przeszukiwanie stosu zabezpieczeń jest zatrzymywane, gdy zostanie potwierdzone uprawnienie zabezpieczeń. Jeśli zostanie potwierdzone uprawnienie bez wykonywania żadnych operacji sprawdzania wywołującego, obiekt wywołujący może pośrednio wykonać kod przy użyciu uprawnień. Potwierdzenia bez sprawdzania zabezpieczeń są dozwolone, jeśli masz pewność, że potwierdzenia nie można użyć w sposób szkodliwy. Potwierdzenie jest nieszkodliwe, jeśli wywoływany kod jest nieszkodliwy lub jeśli użytkownicy nie mogą przekazać dowolnych informacji do kodu, który jest wywoływany.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, należy dodać żądanie zabezpieczeń do metody lub jej typu deklarującego.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Pomiń ostrzeżenie z tej reguły tylko po dokładnym przeglądzie zabezpieczeń.

## <a name="see-also"></a>Zobacz także

- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
- [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)